# Regression Analysis 

## Build Uploading

To make the most of the Regression Analysis feature, it makes sense to incorporate build uploading into a CI/CD pipeline.

### Overview

To upload builds to the PS Tool, follow these steps:

1. Obtain the upload context ID
2. Build a non-instrumented APK with the [UserFlow](/integration/android/user-flow/) library enabled
3. Upload the non-instrumented APK to PS Tool
4. Build an instrumented APK with the [UserFlow](/integration/android/user-flow/) library enabled
5. Upload the instrumented APK to PS Tool

Steps 2-3 and 4-5 could be executed in parallel. 

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
