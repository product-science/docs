# Gradle Build Instructions - Android

## 1. Credentials
Product Science shared access credentials (`productscience.properties` file) via Bitwarden sent. 
Please place it in the root directory of your project.

Product Science Android plugin is distributed as public GitHub maven package. 
It's publicly available but requires authentication with github account.

Please [generate new token](https://github.com/settings/tokens/new) with **read:packages** access and setup `gradle.properties` in your home directory `~/.gradle/gradle.properties`.

```properties title="~/.gradle/gradle.properties"
github_user=<Github Account>
github_key=<Github Token>
```

## 2. Add Product Science maven repository

In `build.gradle` add the maven build info to the repositories for project and subprojects:  


=== "Groovy"
    ```groovy title="build.gradle"
    buildscript {
        repositories {
            maven {
                url "https://maven.pkg.github.com/product-science/PSAndroid"
                credentials {
                    username = github_user
                    password = github_key
                }
            }
        }
        dependencies { ... }
    }
    
    allprojects {
        repositories {
            maven {
                url "https://maven.pkg.github.com/product-science/PSAndroid"
                credentials {
                    username = github_user
                    password = github_key
                }
            }
        }
    }
    ```  

=== "Kotlin DSL"
    ```kotlin title="build.gradle.kts"
    buildscript {
        repositories {
            maven {
                url = uri("https://maven.pkg.github.com/product-science/PSAndroid")
                credentials {
                    username = System.getProperty("github_user")
                    password = System.getProperty("github_key")
                }
            }
        }
        dependencies { ... }
    }

    allprojects {
        repositories {
            maven {
                url = uri("https://maven.pkg.github.com/product-science/PSAndroid")
                credentials {
                    username = System.getProperty("github_user")
                    password = System.getProperty("github_key")
                }
            }
        }
    }

    ```

If the project is configured to prefer settings repositories the
=== "Groovy"
    ```groovy title="build.gradle"
    ...
    dependencyResolutionManagement {
        repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
        repositories {
            maven {
                url "https://maven.pkg.github.com/product-science/PSAndroid"
                credentials {
                    username = github_user
                    password = github_key
                }
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
            maven {
                url = uri("https://maven.pkg.github.com/product-science/PSAndroid")
                credentials {
                    username = System.getProperty("github_user")
                    password = System.getProperty("github_key")
                }
            }
        }
    }
    ```


In another case, if `allprojects` is not present in top level `build.gradle` then add it in the top of the file.  


## 3. Add Product Science plugin to `classpath`

Contact your Sales Engineer to get the `Version` of the Plugin to replace the `VERSIONSUPPLIEDBYPSI` with the `Version` we supply.  

=== "Groovy"
    ```groovy title="build.gradle"
    buildscript {
        repositories { ... }
        dependencies {
            classpath "com.productscience.transformer:transformer-plugin:0.13.1"
            classpath "com.productscience.transformer:transformer-instrumentation:0.13.1"
        }
    }
    ...
    ```

=== "Kotlin DSL"
    ```kotlin title="build.gradle.kts"
    buildscript {
        repositories { ... }
        dependencies {
            classpath("com.productscience.transformer:transformer-plugin:0.13.1")
            classpath("com.productscience.transformer:transformer-instrumentation:0.13.1")
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
