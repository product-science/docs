# Manual Annotation for User Flows

In addition to automatically instrumenting your app, the Product Science SDK provides a `userflow` library that enables manual annotation of user flows in your code. 
This can be useful for tracking and comparing timing changes between specific events across traces.

The steps to add and use the library are below.

## Dependencies

 Add the userflow library as a dependency in `app/build.gradle`

```groovy
    dependencies {
        implementation "com.productscience.userflow:userflow:{{ android_release() }}"
    }
```

## Annotation Process

There are three static methods used to annotate user flows:

* `UserFlow#start`
* `UserFlow#custom`
* `UserFlow#end`

Each of these methods takes a string argument (UserFlow ID) and a nullable String argument (comment message).

Import UserFlow class.

```kotlin
import com.productscience.userflow.v2.UserFlow;
```

### 1. Starting a UserFlow

To start a UserFlow, call `UserFlow#start` and pass it an ID and a String message.

```kotlin
    // ...
    UserFlow.start("appStart")
    // or
    UserFlow.start("appStart", "Comment message")
```

### 2. Annotations UserFlow's milestones

While a UserFlow is in progress, you can make calls to `UserFlow#custom` passing the UserFlow ID and a String message. 

This can be useful to annotate events along the UserFlow (e.g., reaching a milestone or annotating different conditional paths among others).

```kotlin
    UserFlow.custom("appStart", "UserFlow hit a milestone")
```    

### 3. Ending a UserFlow
To end a UserFlow, call `UserFlow#end` passing the ID of the UserFlow to end and an optional String message.

```kotlin
    UserFlow.end("appStart")
    // or
    UserFlow.end("appStart", "One more comment message")
```
    
## Examples

### UserFlow Annotations on PSTool

An example of a slice added via the UserFlow Annotations library. The gray flag on the trace is automatically created for events marked by these slices.
![trace](../../../images/userflow-trace.png)

### Sample app

There is a sample app demonstrating the use of the userflow library at:
[https://github.com/product-science/demoapps/tree/main/Android/userflow-android-example](https://github.com/product-science/demoapps/tree/main/Android/userflow-android-example)


## Project Integration

If you want to enable UserFlow Annotations to be used with Regression Analysis feature, you should enable `UserFlow#setRegressionAnalysisEnabled(true)`.   

_CAUTION_: this method can enable some extra work. You will have to take steps to ensure that regression analysis is disabled in production builds.
