
# Gradle Build Instructions - Android

## 1. Credentials
Product Science shared access credentials (`productscience.properties` file) via Bitwarden sent. 
Please place it in the root directory of your project.


## 2. Add maven repository to buildscript in root `build.gradle`

In the root level `build.gradle` file, add the productscience maven url to the `repositories` block inside of the `buildscript` block. If there is no `buildscript` block, you can add one at the toplevel:  

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
                url "https://artifactory.productscience.app/releases"
            }
        }
        dependencies { ... }
    }
    ```
    
## 3. Add dependencies to buildscript in root `build.gradle`

In the `buildscript` block of the root `build.gradle` file, add the classpaths for the productscience transformer-plugin and transformer-instrumentation artifacts:

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

## 4. Add Product Science maven repository url to all modules

**Case 1:** The project uses `settings.gradle` to specify module dependencies (requires gradle 6.8 or later)

The productscience plugin will attempt to instrument all modules of the app,
so it is necessary to provide a repository url for all modules.
To do this, add the productscience maven repository url to the `dependencyResolutionManagement` block of `settings.gradle`.
If there is no such block, you can add it at the toplevel.

=== "Groovy"
    ```groovy title="settings.gradle"
    ...
    dependencyResolutionManagement {
        repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
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
        repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
        repositories {
            maven {
                url "https://artifactory.productscience.app/releases"
            }
        }
    }
    ```
> **Note**: If you use `RepositoriesMode.FAIL_ON_PROJECT_REPOS` mode you may experience a failure when one or more of the project's modules define their own repositories in their `build.gradle` files.
> Switching the mode to `RepositoriesMode.PREFER_SETTINGS` may solve this problem.
> Alternatively, you may add the productscience maven url to these module `build.gradle` files.
> You can also use the method defined in Case 2 below instead of defining them in `settings.gradle`.
    
----
**Case 2:** The project defines module dependencies in an `allprojects` block in the root `build.gradle` file

Add the repository url to the `allprojects` block in the root `build.gradle` file
=== "Groovy"
    ```groovy title="settings.gradle"
    ...
    allprojects {
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
    allprojects {
        repositories {
            maven {
                url "https://artifactory.productscience.app/releases"
            }
        }
    }
    ```

If there is no `allprojects` block in the root `build.gradle` file, you can add it at the toplevel of the file.
----


**Please label your build with the PSi Plugin Version from above i.e.**  
`MyAppPSi{{ android_release() }}.apk` 
**so our AI can learn how its dynamic instrumentation is performing on the build.**

## 4. Apply the Product Science Plugin  

Apply plugin to `app/build.gradle`  

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


## 5. Add Proguard rules

If the application uses obfuscation/shrinking add a new ProGuard rule to your project.
To achieve it add the next line to the R8/ProGuard configuration file: 
  
```proguard title="proguard-rules.pro."
-keep class com.productscience.transformer.module.** { *; }
```

Your project may use the other proguard file name.

More information about R8/ProGuard configuration can be found here:
[https://developer.android.com/studio/build/shrink-code](https://developer.android.com/studio/build/shrink-code)

## 6. Build your app
Now you can build your app with Gradle, i.e.:
```bash
./gradlew assemble
```

**Please label your build with the Plugin Version from above i.e.**  
`MyApp_PSi-{{ android_release() }}.apk` 
**so our AI can learn how its dynamic instrumentation is performing on the build.**


----


## Enabling the plugin by build type

For plugin versions greater than **0.12.1**, 
you can integrate Product Science pipeline into your gradle build 
selectively apply the plugin to a given build type by adding a `productScience` block 
at the top level of your `app/build.gradle` file. 

Inside the `productScience` block, add a block corresponding to the build type (must have the same name) and set `enabled` to `true`.
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
