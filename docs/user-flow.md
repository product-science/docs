# Manual Annotation for User Flows

In addition to automatically instrumenting your app, the Product Science SDK provides a `userflow` library that enables manual annotation of user flows in your code. This can be useful for tracking and comparing timing changes between specific events across traces.

The steps to add and use the library are below. Note that steps 1-3 are the same as required for adding the Product Science plugin and may have already been completed.

### 1. UserFlow dependency
 Add the userflow library as a dependency in app/build.gradle

    dependencies {
        implementation "com.productscience.userflow:userflow:555"
    }


### 2. Annotation methods
There are three static methods used to define user flows. They are `UserFlow#start`, `UserFlow#custom`, and `UserFlow#end`. Each of these methods take an integer argument and a nullable String argument. The String will appear in the trace as a message.

### 3. Starting a UserFlow
To start a UserFlow, call `UserFlow#start` and pass it an id and a String message.

    UserFlow.start(1, "App start begins")
    
### 4. During a UserFlow
While a UserFlow is in progress, you can make calls to `UserFlow#custom` passing the UserFlow id and a String message. This can be useful to annotate events along the UserFlow (e.g., reaching a milestone or annotating different conditional paths among others).

    UserFlow.custom(1, "UserFlow hit milestone")
    
### 5. Ending a UserFlow
To end a UserFlow, call `UserFlow#end` passing the id of the UserFlow to end and a String message.

    UserFlow.end(1, "App start complete")
    
### 6. Use the Product Science tool to examine the trace file:
![trace][images/userflow-trace.png]

### UserFlow without plugin.
To annotate user flows without applying the Product Science Android plugin, call `UserFlow#setAlwaysAnnotate(true)`. CAUTION: using this method can enable unwanted annotations in production builds. You will have to take steps to insure that UserFlow annotations are only called where appropriate. 

### Sample app
There is a sample app demonstrating the use of the userflow library at [https://github.com/product-science/demoapps-private/tree/main/Android/userflow-android-example](https://github.com/product-science/demoapps-private/tree/main/Android/userflow-android-example)
