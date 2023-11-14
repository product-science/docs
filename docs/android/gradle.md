
# Gradle Build Instructions - Android

These instructions guide you through the process of integrating Product Science instrumentation into an Android application's Gradle build process.

!!! info
    If your build environment does not allow network access to our servers `https://prod.productscience.app/api/v1/*`, please add to your allowlist.
    If your network settings prevent adding this endpoint, you will be provided with plugin and config archives detailed in sections below.

## 1. Credentials
Product Science shared access credentials (`productscience.properties` file) via Bitwarden sent. 
Please place this file in the root directory of your project.

!!! info
    If your build environment does not allow network access to our servers as specified above, 
    you will be provided with a 'productscience.config.N.zip' archive instead of a .properties file.  
    Copy the entire .zip archive to your workspace directory (do not unzip the archive).


## 2. Add Product Science maven repository to root project's `buildscript`

In the root level **build.gradle** file, add the productscience maven url to the `repositories` inside of the `buildscript` block.
If you do not have a `buildscript` block in the file, you can add one at the toplevel.

=== "Groovy"
    ```groovy title="build.gradle"
    buildscript {
        repositories {
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
            maven {
                url = uri("https://artifactory.productscience.app/releases")
            }
        }
        dependencies { ... }
    }

    ```

## 3. Add Product Science dependencies to buildscript in root **build.gradle**

In the `buildscript` block of the root **build.gradle** file, add the classpaths for the productscience
`transformer-plugin` and `transformer-instrumentation` artifacts:

=== "Groovy"
    ```groovy title="build.gradle"
    buildscript {
        repositories { ... }
        dependencies {
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
            classpath("com.productscience.transformer:transformer-plugin:{{ android_release() }}")
            classpath("com.productscience.transformer:transformer-instrumentation:{{ android_release() }}")
        }
    }
    ...
    ```


## 4. Add Product Science maven repository url to all submodules

The productscience plugin will attempt to instrument all modules of the app, 
so it is necessary to provide access to dependencies for all submodules. 

To achieve that, product science maven repository has to be visible for all submodules.
This can be achieved in Gradle in two ways: either using the `allprojects` block in the root **build.gradle**, 
or the `dependencyResolutionManagement` block in the **settings.gradle**.


### Case 1: Project uses **settings.gradle** to specify module dependencies (requires gradle 6.8 or later)

Add the repository url to the `dependencyResolutionManagement` block of the **settings.gradle** file:

=== "Groovy"
    ```groovy title="settings.gradle"
    ...
    dependencyResolutionManagement {
        ...
        repositories {
            maven {
                url "https://artifactory.productscience.app/releases"
            }
        }
    }
    ```

=== "Kotlin DSL"
    ```kotlin title="settings.gradle.kts"
    ...
    dependencyResolutionManagement {
        ...
        repositories {
            maven {
                url = uri("https://artifactory.productscience.app/releases")
            }
        }
    }
    ```

If this block does not exist, you can create it at the top level of your **settings.gradle** file.


### Case 2: Project defines module dependencies in an `allprojects` block in the root **build.gradle** file
Add the repository url to the `allprojects` block in the root **build.gradle** file:

=== "Groovy"
    ```groovy title="build.gradle"
    
    allprojects {
        repositories {
            maven {
                url "https://artifactory.productscience.app/releases"
            }
        }
    }
    ```  

=== "Kotlin DSL"
    ```kotlin title="build.gradle.kts"

    allprojects {
        repositories {
            maven {
                url = uri("https://artifactory.productscience.app/releases")
            }
        }
    }
    ```

If this block does not exist, you can create it at the top level of your **build.gradle** file.


**Note:** If you use `RepositoriesMode.FAIL_ON_PROJECT_REPOS` of `dependencyResolutionManagement` you 
may experience a failure when one or more modules define their own repositories in their **build.gradle** files.  
Switching the mode to `RepositoriesMode.PREFER_SETTINGS` may solve this problem.
Alternatively, you may add the productscience maven repository url to these module **build.gradle** files.


## 5. Apply the Product Science Plugin  

Apply the plugin in the **app/build.gradle** file as follows:

=== "Groovy"
    ```groovy title="app/build.gradle"
    plugins {
        id "com.android.application"
        id "kotlin-android"
    }
    apply plugin: "com.productscience.transformer.plugin"
    ...
    ```

=== "Kotlin DSL"
    ```kotlin title="app/build.gradle.kts"
    plugins {
        id("com.android.application")
        id("kotlin-android")
        id("com.productscience.transformer.plugin")
    }
    ...
    ```

## 6. Add Proguard rules

If the application uses obfuscation/shrinking add a new ProGuard rule to your project.
To achieve it add the next line to the R8/ProGuard configuration file: 
  
```proguard title="proguard-rules.pro"
-keep class com.productscience.transformer.module.** { *; }
-keep class com.productscience.** { *; }
```

Your project may use the other proguard file name.

More information about R8/ProGuard configuration can be found here:
[https://developer.android.com/studio/build/shrink-code](https://developer.android.com/studio/build/shrink-code)

## 7. Build your app
Now you can build your app with Gradle, i.e.:
```bash
./gradlew assemble
```

Please label your build with the Plugin Version from above i.e. `MyApp_PSi-{{ android_release() }}.apk` 
so our AI can learn how its dynamic instrumentation is performing on the build.


----


## Enabling the plugin by build type

For versions of the plugin exceeding **0.12.1**, you have the option to selectively integrate the productscience plugin into your Gradle build. 
This can be achieved by applying the plugin only to specific build types. 

To do this, insert a `productScience` block at the top of your **app/build.gradle** file. 
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

