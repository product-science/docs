
# Gradle Build Instructions - Android

Follow these steps to instrument your Java/Kotlin Android app with PS Plugin. Once you have successfully built, installed and run the app, you will be able to record and analyze traces.

If you get stuck, do refer to our [FAQ](https://docs.productscience.app/android/integration-faq-android/) for additional steps and guidance.

!!! info
    If your build environment does not allow network access to our servers `https://prod.productscience.app/api/v1/*`, please add to your allowlist.
    If your network settings prevent adding this endpoint, you will be provided with plugin and config archives detailed in sections below.

## 1. Identify the two levels of files
You will be working with and modifying files at two levels:

1. The __root__ directory. This is the root directory of your Android project. 
If your repository is entirely your Android project, it will usually be the top level folder. 
The `build.gradle` (or `build.gradle.kts`) file at this level is usuall fairly terse, 
defining a few global dependencies and repositories.

2. The __app__ directory. This is the folder that actually builds your Android app. 
It is often, though not always, named `app`. The `build.gradle` file at this level is usually more verbose, 
containing all the dependencies and settings needed to build your Android app.
   
## 2. Credentials

If you are an existing Product Science user, credentials have been shared with you via one of the following options:

- via BitWarden as the __productscience.properties__ file
- credentials were issued as a part of self-served onboarding at https://productscience.app/guide/instrument-and-build/android

Place the __productscience.properties__ file containing your credentials in the root director of your project.

!!! info
    If your build environment does not allow network access to our servers as specified above, 
    you will be provided with a 'productscience.config.N.zip' archive instead of a .properties file.  
    Copy the entire .zip archive to your workspace directory (do not unzip the archive).


## 3. Add Product Science maven repository for the build

In the __root__ level `build.gradle` (or `build.gradle.kts`) file, 
add the `productscience` maven url  to the `repositories` block inside of the `buildscript` block. 
If you do not have a `buildscript` block in the file, you can add one at the top level of the `build.gradle` file.

=== "Groovy" 
    ```groovy title="build.gradle"
        buildscript {
            repositories {
                ...
                maven {
                    url "https://artifactory.productscience.app/releases"
                }
            }
            dependencies { ... }
        }
    ```

=== "Kotlin DSL"
    ```kotlin title="build.gradle.kts"
        buildscript {
            repositories {
                ...
                maven {
                    url = uri("https://artifactory.productscience.app/releases")
                }
            }
            dependencies { ... }
        }
    ```

## 4. Add Product Science maven repository to all modules
In your __root__ directory the project either defines module dependencies in the `build.gradle` file or the `settings.gradle` file. Look in both files to see which.

### Case 1: Your project defines module dependencies in an allProjects block in the root build.gradle file

Add the repository url to the `allprojects` block in the root `build.gradle` file

=== "" 
    ```groovy title="settings.gradle"
        allprojects {
            repositories {
                ...
                maven {
                    url "https://artifactory.productscience.app/releases"
                }
            }
        }
    ```

=== "Kotlin DSL"
    ```kotlin title="settings.gradle.kts"
        allprojects {
            repositories {
                ...
                maven {
                    url = uri("https://artifactory.productscience.app/releases")
                }
            }
        }
    ```

If there is no `allprojects` block in the root `build.gradle` file, you can add it at the top level of the file.

### Case 2: Your project uses settings.gradle to specify module dependencies (requires gradle 6.8 or later)

The `productscience` plugin will attempt to instrument all modules of the app, 
so it is necessary to provide a repository url for all modules. 
To do this, add the `productscience` maven repository url to the `dependencyResolutionManagement` block of `settings.gradle`. 
If there is no such block, you can add it at the top level.

=== "Groovy"
    ```groovy title="build.gradle"
        dependencyResolutionManagement {
            repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
            repositories {
                ...
                maven {
                    url "https://artifactory.productscience.app/releases"
                }
            }
        }
    ```

=== "Kotlin DSL"
    ```kotlin title="build.gradle.kts"
        ...
        dependencyResolutionManagement {
            repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
            repositories {
                ...
                maven {
                    url = uri("https://artifactory.productscience.app/releases")
                }
            }
        }
    ```

__Note:__ If you use `RepositoriesMode.FAIL_ON_PROJECT_REPOS` mode you may experience a failure when one or more modules define their own repositories in their `build.gradle` files. Switching the mode to `RepositoriesMode.PREFER_SETTINGS` may solve this problem. Alternatively, you may add the `productscience` maven repository url to these modules `build.gradle` files. You can also use the method defined in Case 1 above instead of defining them in `settings.gradle`.

## 5. Add Product Science plugin to classpath

In the `buildscript` block of the __root__ `build.gradle` file, add the classpaths for the `productscience` `transformer-plugin` and `transformer-instrumentation` artifacts:

=== "Groovy"
    ```groovy title="build.gradle
        buildscript {
            repositories { ... }
            dependencies {
                ...
                classpath "com.productscience.transformer:transformer-plugin:{{ android_release() }}"
                classpath "com.productscience.transformer:transformer-instrumentation:{{ android_release() }}"
            }
        }
        ...
    ```

=== "Kotlin DSL"
    ```kotlin title="build.gradle.kts"
        buildscript {
            repositories { ... }
            dependencies {
                ...
                classpath("com.productscience.transformer:transformer-plugin:{{ android_release() }}")
                classpath("com.productscience.transformer:transformer-instrumentation:{{ android_release() }}")
            }
        }
        ...
    ```


## 6. Apply the Product Science Plugin

Now you need to enable the plugin in your __app__ `build.gradle` file. This is often in a directory named `app`, and will be more verbose than the top level gradle file.

=== "Groovy"
    ```groovy title="app/build.gradle"
        plugins {
            ...
            id "com.android.application"
        }
        apply plugin: "com.productscience.transformer.plugin"
        ...
    ```

=== "Kotlin DSL"
    ```kotlin title="app/build.gradle.kts"
        plugins {
            ...
            id("com.android.application")
            id("com.productscience.transformer.plugin")
        }
        ...
    ```

## 7. Add Proguard rules

If the application uses obfuscation/shrinking using Proguard, add a new Proguard rule to your project. Add the next line to the R8/ProGuard configuration file:

```
-keep class com.productscience.transformer.module.** { *; }
-keep class com.productscience.** { *; }
```

The file can have a variety of names but will include the word proguard and have similar lines to this one, and it will be in your __app__ folder.

More information about R8/ProGuard configuration can be found here: https://developer.android.com/studio/build/shrink-code

## 8. Build your app

Now you can build your app with Gradle, i.e.:
```bash
./gradlew assemble
```


----


## Enabling the plugin by build type

If you are using a productscience plugin version greater that __0.12.1__, you can selectively integrate the productscience plugin into your Gradle build.
You will do this by applying the plugin only to specific build types.

To do this, insert a `productScience` block at the top of your __app/build.gradle__ file. 
Inside the proguard block, add a block corresponding to the build type (must have the same name) and set `enabled` to `true`.

=== "Groovy"
    ```groovy title="app/build.gradle"
    plugins {
        id "com.android.application"
        id "kotlin-android"
    }
    apply plugin: "com.productscience.transformer.plugin" 
    productScience {
        psiRelease {
            enabled true
        }
    }
    
    android {
        ...
        buildTypes {
            psiRelease {
                minifyEnabled true
            }
            release {
                minifyEnabled true
            }
        }
    }
    ```
=== "Kotlin DSL"
    ```kotlin title="app/build.gradle.kts"
    plugins {
        id("com.android.application")
        id("kotlin-android")
        id("com.productscience.transformer.plugin")
    }
    
    productScience {
        create("psiRelease") {
            isEnabled = true
        }
    }
    
    android {
        ...
        buildTypes {
            create("psiRelease") {
                isMinifyEnabled = true
            }
    
            getByName("release") {
                isMinifyEnabled = true
            }
        }
    }
    ```


If the `productScience` block is missing or empty, the plugin will be applied to all build types.
If one or more build types appear in the `productScience` block,
the plugin will be applied only to those build types that have `enabled` set to true. 

