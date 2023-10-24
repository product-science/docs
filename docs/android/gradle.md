
# Gradle Build Instructions - Android

The following instructions describe how to add Product Science instrumentation to an Android application build with Gradle.

!!! info
    If your build environment does not allow network access to our servers `https://prod.productscience.app/api/v1/*`, please add to your allowlist.
    If your network settings prevent adding this endpoint, you will be provided with plugin and config archives detailed in sections below.

## 1. Credentials
Product Science shared access credentials (`productscience.properties` file) via Bitwarden sent. 
Please place it in the root directory of your project.

!!! info
    If your build environment does not allow network access to our servers as specified above, 
    you will be provided with a 'productscience.config.N.zip' archive instead of a .properties file.  
    Copy the entire .zip archive to your workspace directory (do not unzip the archive).


## 2. Add Product Science maven repository

In `build.gradle` add the PS maven artifactory to the repositories for project and subprojects:  


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
    buildscript {
        repositories {
            maven {
                url "https://artifactory.productscience.app/releases"
            }
        }
        dependencies { ... }
    }

    allprojects {
        repositories {
            maven {
                url "https://artifactory.productscience.app/releases"
            }
        }
    }

    ```

If the project is configured to prefer settings repositories maven source should be added to settings file:
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


In another case, if `allprojects` is not present in top level `build.gradle` then add it in the top of the file.  

!!! info
    If your build environment does not allow network access to our servers, 
    you will be provided with an archive with a local version of PS Plugin. 
    Unarchive it and put maven packages in an internal artifactory or local maven storage (`~/.m2/repository/`).  
    
    Then add internal artifactory or local maven to the project's repositories instead of public PS artifactory:
    ```
    repositories {
        maven {
            url "https://company.com/artifactory"
        }
        mavenLocal() // If local maven is used
    }
    ```


## 3. Add Product Science plugin to `classpath`

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

**Please label your build with the PSi Plugin Version from above i.e.**  
`MyAppPSi0.9.1.apk` 
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
-keep class com.productscience.** { *; }
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
`MyApp_PSi-0.14.2.apk` 
**so our AI can learn how its dynamic instrumentation is performing on the build.**


----


## Enabling the plugin by build type

For plugin versions greater than **0.12.1**, 
you can integrate Product Science pipeline into your gradle build 
selectively apply the plugin to a given build type by adding a `productScience` block 
at the top level of your `app/build.gradle` file. 

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

## Disabling Window#setFlags(LayoutParams.FLAG_SECURE, LayoutParams.FLAG_SECURE) by build type

Some apps disable screen recording for security reasons. For Product Science plugin builds, you may want to keep screen recording enabled so that the screen recording can be synchronized to recorded traces. To do this for a specific build type, it is recommended to create a boolean variable in the `gradle.build` file and use that in code to guard the toggling of the `Window` flags.

For example, if you have the following code in your Activity to disable screen recording:

```
getWindow.setFlags(LayoutParams.FLAG_SECURE, LayoutParams.FLAG_SECURE);
```

Set up the following variable in the `build.gradle` file for the app:

=== "Groovy"
    ```groovy title="app/build.gradle"
    ...
    android {
        ...
        buildFeatures {
            buildConfig true
        }
        defaultConfig {
            buildConfigField "boolean", "disableScreenRecording", "true"
        }
        buildTypes {
            psiRelease {
                buildConfigField "boolean", "disableScreenRecording", "false"            
            }
            release {
                buildConfigField "boolean", "disableScreenRecording", "true"
            }
        }
    }
    ```
=== "Kotlin DSL"
    ```kotlin title="app/build.gradle"
    ...
    android {
        ...
        buildFeatures {
            buildConfig = true
        }
        defaultConfig {
            buildConfigField("boolean", "disableScreenRecording", "true")
        }
        buildTypes {
            psiRelease {
                buildConfigField("boolean", "disableScreenRecording", "false")            
            }
            release {
                buildConfigField("boolean", "disableScreenRecording", "true")
            }
        }
    }
    ```
Then you can wrap the call for `setFlags` to conditionally enable screen recording for the Product Science build.

```
if (Build.Config.disableScreenRecording) {
    getWindow.setFlags(LayoutParams.FLAG_SECURE, LayoutParams.FLAG_SECURE);
}
```
