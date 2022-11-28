# Manual Annotation for User Flows

In addition to automatically instrumenting your app, the Product Science SDK provides a `userflow` library that enables manual annotation of user flows in your code. This can be useful for tracking and comparing timing changes between specific events across traces.

The steps to add and use the library are below. Note that steps 1-3 are the same as required for adding the Product Science plugin and may have already been completed.

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

### 4. Add the userflow library in app/build.gradle
![userflow-library](images/add-library.png)

### 5. Start manually annotating user flows in your app. Ensure that each user flow has a distinct integer identifier.
![uf-annotation](images/uf-annotation.png)

There is a sample app demonstrating the use of the userflow library at URL.
