# Regression Analysis Build Uploading

To make the most of the Regression Analysis feature, it makes sense to incorporate build uploading into a CI/CD pipeline.

## Overview

1. Fetch upload context ID
2. Build a non-instrumented APK with enabled [UserFlow](/integration/android/user-flow/) library
3. Upload a non-instrumented APK to PS Tool
4. Build an instrumented APK with enabled [UserFlow](/integration/android/user-flow/) library
5. Upload instrumented APK to PS Tool

Steps 2-3 and 4-5 could be parallelized. 

## Build Uploading API

### 1. Request upload context ID

#### Request

```
POST /api/v1/projects/{projectName}/build-uploads
```

#### Response

##### Parameters

- `id` – integer upload contextId to use in next steps
- `dateCreated` – creation date in ISO 8601 format

##### Example

```json
{
  "id": 123,
  "dateCreated": "2024-03-07T16:55:49.168Z"
}
```



