## Gradle Instructions - Android

### Preparation
1. Set up Gradle build with the Product Science plugin from the Product Science Github repo (see instructions below.)
2. Determine a named developer resource for Product Science to partner with for generating new builds
3. Ideally create a trigger for Product Science to generate new builds to increase speed of the Optimization process

### Optimization Loop
The Loop is repeated by your developers 20+ times initially and 5+ times with every major update.

1. [Your devs]  Build the app with PSi Gradle plugin
2. Ideally Product Science is provided with a trigger to create automation- otherwise a named developer can be supplied to rebuild
3. [Your devs]  Provide a cloud link to your .apk
4. [Product Science] Runs the app and collects app performance data
5. Optimization may finish and we proceed to Insight Generation
6. [Product Science] Feeds the app performance data to Product Science optimization algorithms
7. [Product Science] Algorithms update model in the Product Science Github repo
8. [Your devs] Next build will use the new model from the Product Science Github repo automatically

### Gradle Instructions

1. Key Generation Methodology- PSi:  
* Generates a token (key) via GitHub
* Saves key in Bitwarden credential storage
* Shares token with Bitwarden Send 
* Keys have an expiration date

2. Configure `gradle.properties` in Gradle home directory
`github_user=<supplied-by-PSi>`  
`github_key=<supplied-by-PSi>`

For example:  
<img src="./images/creds.png" alt="image" width="640"/>

3. In build.gradle add the maven build info to the repositories for project and subprojects:
```
maven {
    url "https://maven.pkg.github.com/product-science/PSAndroid"
    credentials {
        username = github_user
        password = github_key
    }
}
```
For example:  
<img src="./images/maven1.png" alt="image" width="640"/>  
and  
For example:  
<img src="./images/maven2.png" alt="image" width="640"/>

4. Add the PSi Classpath to Dependencies

Note that we are using a demo app for this example called “Signal” to visualize the process

```
classpath "com.productscience.transformer:transformer-plugin:0.8.25_S"
classpath "com.productscience.transformer:transformer-instrumentation:0.8.25_S"
```

For example:  
<img src="./images/classpath.png" alt="image" width="640"/

5. Add `<profileable android:shell="true" />` into `AndroidManifest.xml` to enable profiling

For example:  
<img src="./images/manifest.png" alt="image" width="640"/>

6. Apply the PSi transformer.plugin 
apply plugin: `"com.productscience.transformer.plugin" to app/build.gradle`

For example:  
<img src="./images/transformer.png" alt="image" width="640"/>

7. Create a file called `productscience.properties` and add the PSi config/token to it

```
productscience.github.config=product-science:airbnb-configs:ps-airbnb.yaml:master
productscience.github.token=<supplied-by-PSI>
```

### That’s it!
Now you can build your app with Gradle

For example:  
<img src="./images/build.png" alt="image" width="640"/>

### Separate build configuration

For the future work convenience it’s best to create a separate build configuration with PSi.
A special flag enableProductScience can be used for these purposes:
<img src="./images/separate1.png" alt="image" width="640"/>  
<img src="./images/separate2.png" alt="image" width="640"/>  
<img src="./images/separate3.png" alt="image" width="640"/>  

Then you can build your app with PSi using the flag:

<img src="./images/build2.png" alt="image" width="640"/>