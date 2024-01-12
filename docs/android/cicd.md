# CICD Integration with Gradle

Product Science suggests two main approach for integration Gradle plugin in CICD. 

## Build Variant 

* [Example App](https://github.com/product-science/demoapps/tree/main/cicd-examples/android-buildvariant)
* [Example GitHub workflow](https://github.com/product-science/demoapps/blob/main/.github/workflows/cicd-buildvariant.yml)
* [Build Variant docs](gradle.md#enabling-the-plugin-by-build-type)


This approach is based on [Gradle build variant](https://developer.android.com/studio/build/build-variants).
A build variant `psiRelease` is created for instrumented version of the app. 
PS Plugin is applied only for this build variant.

=== "Groovy"
    ```groovy title="app/build.gradle"
    plugins {
        id 'com.android.application'
        id 'kotlin-android'
    }

    apply plugin: "com.productscience.transformer.plugin" 

    productScience {
        psiRelease {
            enabled true
        }
    }

    android {
        defaultConfig { ... }

        buildTypes {
            release {
                ...
            }

            psiRelease {
                ...
            }
        }
    }
    ```

=== "Kotlin DSL"
    ```kotlin title="app/build.gradle"
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
                ...
            }

            getByName("debug") {
                ...
            }
        }
    }
    ```


Build can be triggered with gradle command:
```
./gradlew assemblePsiRelease
```


## Conditional plugin apply

* [Example App](https://github.com/product-science/demoapps/tree/main/cicd-examples/android-condition)
* [Example GitHub workflow](https://github.com/product-science/demoapps/blob/main/.github/workflows/cicd-condition.yml)


This approach is based on conditional applying of gradle plugin.
PS Plugin is applied only when the value of `USE_PSTOOL` environment variable is true.

=== "Groovy"
    ```groovy title="app/build.gradle"
    plugins {
        id 'com.android.application'
        id 'kotlin-android'
    }

    if (System.getenv("USE_PSTOOL")) {
        apply plugin: "com.productscience.transformer.plugin" 
    }
    ```

    Build can be triggered with gradle command:
    ```
    USE_PSTOOL=true ./gradlew assembleRelease
    ```

=== "Kotlin DSL"
    ```kotlin title="app/build.gradle"
    plugins {
        id("com.android.application")
        id("kotlin-android")

        val usePSPlugin: Boolean = System.getenv("USE_PSTOOL").toBoolean()
        if (usePSPlugin) {
            id("com.productscience.transformer.plugin")
        }
    }
    ```

    Build can be triggered with gradle command:
    ```
    USE_PSTOOL=true ./gradlew assembleRelease
    ```
