# Integration FAQ - Android

## Use CLI Tool to build
[CLI Tool](cli-tool.md) will automatically retry and fix most issues experienced
```
java -jar integration-cli.jar "./gradlew assembleRelease --stacktrace"
```
On failure share the created `ps-output` directory to help us debug


## Build Duration
Instrumenting takes significant time (oftentimes > 1 hour), let the build run until completion even if it looks like it has stalled

**Common steps it may appear to hang on:** ```:app:dexAppRelease```


### Proguard Rules
Setting proper Proguard rules will also help reduce build time, especially important during the R8 minify step. Check these are set in the R8/Proguard config file *(proguard-rules.pro)*:
```
-keep class com.productscience.transformer.module.** { *; } 
-keep class com.productscience.** { *; }
```


## Memory Usage
Instrumenting requires quite a lot of memory, for the best success rate, increase the heap size available. See example for 12GB, adjust as necessary:
```
org.gradle.jvmargs=-Xmx12288m         // gradle.properties

dexOptions { javaMaxHeapSize "12g" }  // build.gradle
```


## Gradle Settings

#### Check Cache Configuration Disabled
Sometimes cache configuration can cause issues with instrumentation. Support currently in development

#### Check Plugin Applied to Correct Build Variant
Ensure that plugin is applied to the built variant chosen in the CLI command



## Screen Recording

Some apps disable screen recording for security reasons.
For Product Science plugin builds, you may want to keep screen recording enabled so that the screen recording can be synchronized to recorded traces. 
To do this for a specific build type, it is recommended to create a boolean variable in the `gradle.build` file and use that in code to guard the toggling of the `Window` flags.

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
