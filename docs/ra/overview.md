# Regression Analysis 
PS Performance Regression Analysis is our solution to provide a crystal-clear view of potential performance regressions in mobile apps. By eliminating confusing results due inconsistent network conditions or unpredictable system behavior, we cut through the noise and excel where other tools fall short.

## Build Uploading

To make the most of the Regression Analysis feature, it makes sense to incorporate build uploading into a CI/CD pipeline.

### Overview

To upload builds to the PS Tool, follow these steps:

1. Obtain the upload context ID
2. Build a non-instrumented APK with the [UserFlow](/integration/android/user-flow/) library enabled
3. Upload the non-instrumented APK to PS Tool
4. Build an instrumented APK with the [UserFlow](/integration/android/user-flow/) library enabled
5. Upload the instrumented APK to PS Tool

After receiving a context ID, tasks could be parallelized: building and uploading the non-instrumented version (steps 2 and 3), and building and uploading the instrumented version (steps 4 and 5). The context ID has to be passed to both uploads.

The instrumented build is optional for uploading, however, it's recommended to upload as it will help to provide traces and insights in case of regression.  

### HTTP API

Host:         `productscience.app`  
Protocol:     `HTTPS`  
Content type: `application/json`  
Charset:      `utf-8`

To access the API endpoints, you must supply your `productscience.token` from the `productscience.properties` file as an Authorization header. For instance: 

```
Authorization: Bearer {YOUR_TOKEN}
```

See all the API endpoints [here](/regression-analysis/api).
