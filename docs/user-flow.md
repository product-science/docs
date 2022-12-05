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

### 4. Add the userflow library as a dependency in app/build.gradle
    dependencies {
        implementation "com.productscience.userflow:userflow:555"
    }


### 5. Start manually annotating user flows in your app. Ensure that each user flow has a distinct integer identifier.

### 6. There are three static methods used to define user flows. They are `UserFlow#start`, `UserFlow#custom`, and `UserFlow#end`. Each of these methods take an integer argument and a nullable String argument. The String will appear in the trace as a message.

### 7. To start a UserFlow, call `UserFlow#start` and pass it an id and a String message.

    UserFlow.start(1, "App start begins")
    
### 8. While a UserFlow is in progress, you can make calls to `UserFlow#custom` passing the UserFlow id and a String message. This can be useful to annotate events along the UserFlow (e.g., reaching a milestone or annotating different conditional paths among others).

    UserFlow.custom(1, "UserFlow hit milestone")
    
### 9. To end a UserFlow, call `UserFlow#end` passing the id of the UserFlow to end and a String message.

    UserFlow.end(1, "App start complete")
    
### 10. Use the Product Science tool to examine the trace file:
![trace][images/userflow-trace.png]

There is a sample app demonstrating the use of the userflow library at [https://github.com/product-science/demoapps-private/tree/main/Android/userflow-android-example](https://github.com/product-science/demoapps-private/tree/main/Android/userflow-android-example)
