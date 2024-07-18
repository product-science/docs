## 1. Obtain upload context ID

### Request

```
POST /api/v1/projects/{projectName}/build-uploads
```

### Response

JSON body with parameters:

- **`id`** (required) – integer upload contextId to use in next steps
- **`dateCreated`** (required) – creation date in ISO 8601 format

Example:

```json
{
  "id": 28,
  "dateCreated": "2024-03-07T16:55:49.168Z"
}
```

## 2. Submit build metadata and obtain upload URL

Call this endpoint when your build file is ready.

### Request


```
POST /api/v1/projects/{projectName}/builds
```

JSON body with parameters:

- **`contextId`** (required) – upload context ID obtained in step 1
- **`buildType`** (required) – possible values are: `APK` or `INSTRUMENTED_APK`  
- **`buildFileName`** (required) – file name, e.g. `app-play-release.apk` 
- **`name`** – arbitrary name to distinguish the build, e.g. `release-5.2.8`
- **`description`** – arbitrary build description
- **`sourceControlId`** – VCS commit, e.g. git commit hash
- **`sourceControlIsoTimestamp`** – VCS commit timestamp in ISO 8601 format. To retrieve the timestamp in Git, you can use the following shell command: `git show -s --format='%cI' <commit-hash>`

Example:

```json
{
  "contextId": "28",
  "buildType": "APK",
  "buildFileName": "app-play-release.apk",
  "name": "v5.2.8",
  "description": "Arbitrary description",
  "sourceControlId": "e3c0fedc625094db1cbb2823fd425b51ddc0932e",
  "sourceControlIsoTimestamp": "2024-03-07T14:55:43.540Z"
}
```

### Response

JSON body with parameters:

- **`uploadSpec`** (required) – metadata to upload build to a storage
    * **`method`** (required) – HTTP method
    * **`url`** (required) – URL
    * **`headers`** (required) – map of HTTP headers
- **`build`** (required) – build metadata
    * **`id`** (required) – build ID number
    * **`contextId`** (required) – upload context ID obtained in step 1
    * **`buildType`** (required) – possible values are: `APK` or `INSTRUMENTED_APK`
    * **`buildFileName`** (required) – file name, e.g. `app-play-release.apk`
    * **`name`** – arbitrary name to distinguish the build, e.g. `release-5.2.8`
    * **`description`** – arbitrary build description
    * **`sourceControlId`** – VCS commit, e.g. git commit hash
    * **`sourceControlIsoTimestamp`** – VCS commit timestamp in ISO 8601 format
    * **`uploadState`** – `UPLOADING` or `FINISHED` or `FAILED`
    * **`dateCreated`** – build creation timestamp 

Example:

```json
{
  "uploadSpec": {
    "method": "PUT",
    "url": "https://storage.googleapis.com/some/path?someParams=someValue",
    "headers": {
      "Content-Type": "application/octet-stream",
      "X-Goog-Content-Length-Range": "0,1073741824"
    }
  },
  "build": {
    "id": 70,
    "contextId": 28,
    "buildType": "APK",
    "buildFileName": "app-play-release.apk",
    "name": "v5.2.8",
    "description": "Arbitrary description",
    "sourceControlId": "e3c0fedc625094db1cbb2823fd425b51ddc0932e",
    "sourceControlIsoTimestamp": "2024-03-07T14:55:43.540Z",
    "dateCreated": "2024-03-08T14:13:33.143Z",
    "uploadState": "UPLOADING"
  }
}
```

## 3. Upload file to the obtained URL

Use `uploadSpec` object from the previous response to upload a file as `application/octet-stream`.

```
{uploadSpec.method} {uploadSpec.url}
{uploadSpec.hearder1}: {uploadSpec.header1Value}
{uploadSpec.hearder2}: {uploadSpec.header2Value}
Content-Length: {YOUR_FILE_LENGTH}

{YOUR_FILE_BINARY_DATA}
```
