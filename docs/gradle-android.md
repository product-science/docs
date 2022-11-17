# Gradle Build Instructions - Android

### 1. Key Generation Methodology- PSi:  
* Generates a token (key) via GitHub
* Saves key in Bitwarden credential storage
* Shares token with Bitwarden Send 
* Keys have an expiration date

### 2. Configure `gradle.properties`  

 Set up `gradle.properties` in your home directory i.e. `~/.gradle/gradle.properties`  
```bash
github_user=<supplied-by-PSi>
github_key=<supplied-by-PSi>
```

For example:  
![creds](images/creds.png)  

### 3. Project top level `build.gradle`: add maven build Info

In `build.gradle` add the maven build info to the repositories for project and subprojects:  

```bash
maven {
    url "https://maven.pkg.github.com/product-science/PSAndroid"
    credentials {
        username = github_user
        password = github_key
    }
}
```  

If `allprojects` is not present in top level `build.gradle` then add it:  

```bash
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

For example:  
![maven](images/maven1.png)  
and   
![maven](images/maven2.png)  

### 4. Project top level `build.gradle`: Add PSi `classpath` to `dependencies`

Note that we are using a demo app for this example called “Signal” to visualize the process.
Contact your Sales Engineer to get the `Version` of the Plugin- replace the `VERSIONSUPPLIEDBYPSI` with the `Version` we supply.  

```bash
classpath "com.productscience.transformer:transformer-plugin:<VERSIONSUPPLIEDBYPSI>"
classpath "com.productscience.transformer:transformer-instrumentation:<VERSIONSUPPLIEDBYPSI>"
```

For example:  
![classpath](images/classpath.png)  

**Please label your build with the PSi Plugin Version from above i.e.**  
`MyAppPSi0.9.1.apk` 
**so our AI can learn how its dynamic instrumentation is performing on the build.**

### 5. `app/build.gradle`: Apply the PSi `transformer.plugin`  

Apply plugin to `app/build.gradle`  

```bash
"com.productscience.transformer.plugin" 
```

For example:  
![transformer](images/transformer.png)

### 6. `AndroidManifest.xml`: Enable PSi profiling  

Add  
```bash
<profileable android:shell="true" />
```  
into `AndroidManifest.xml` to enable profiling

For example:  
![manifest](images/manifest.png)  

### 7. Setup PSi properties  

Create a file called  
`productscience.properties`  in the projects top level directory and add the PSi config/token to it:

```bash
productscience.github.config=<VERSIONSUPPLIEDBYPSI>
productscience.github.token=<supplied-by-PSI>
```

### Proguard

If the application uses obfuscation/shrinking add a new ProGuard rule to your project.
To achieve it add the next line to the R8/ProGuard configuration file- typically 
  
```bash
app->proguard->proguard-appcompatv7.pro
```
  
```bash
-keep class com.productscience.transformer.module.** { *; }
```

The default name of this file is proguard-rules.pro. But your project may use the other name.

More information about R8/ProGuard configuration can be found here:
https://developer.android.com/studio/build/shrink-code

### Build your app
Now you can build your app with Gradle

For example:  
![build](images/build.png)  

**Please label your build with the PSi Plugin Version from above i.e.**  
`MyAppPSi0.9.1.apk` 
**so our AI can learn how its dynamic instrumentation is performing on the build.**

### Enabling the plugin by build type

For plugin versions greater than 0.12.1, you can selectively apply the plugin to a given build type by adding a `productScience` block at the top level of your `app/build.gradle` file. Inside the proguard block, add a block corresponding to the build type (must have the same name) and set `enabled` to `true`.
![buildType](images/buildType.png)

If the `productScience` block is missing or empty, the plugin will be applied to all build types. If one or more build types appear in the `productScience` block, the plugin will be applied only to those build types that have `enabled` set to true. 
