# cURL example

## 1. Obtain upload context ID

Request: 

```shell
curl -X "POST" "https://test.productscience.app/api/v1/projects/{projectName}/build-uploads" \
     -H 'Authorization: Bearer {YOUR_TOKEN}'
```

Response: 

```
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 50
```
```json
{
  "id": 28,
  "dateCreated": "2024-03-07T16:55:49.168Z"
}
```

## 2. Submit build metadata and obtain upload URL 

Request: 

```shell
curl -X "POST" "https://test.productscience.app/api/v1/projects/{projectName}/builds" \
     -H 'Authorization: Bearer {YOUR_TOKEN}' \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
  "contextId": 28,
  "buildType": "APK",
  "buildFileName": "app-play-release.apk",
  "name": "v5.2.8"
  "description": "Arbitrary description",
  "sourceControlId": "e3c0fedc625094db1cbb2823fd425b51ddc0932e",
  "sourceControlIsoTimestamp": "2024-03-07T14:55:43.540Z",
}'
```

Response:

```
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1430
```
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

Request: 

```shell
curl -X "PUT" "https://storage.googleapis.com/some/path?someParams=someValue" \
     -H 'Content-Type: application/octet-stream' \
     -H 'X-Goog-Content-Length-Range: 0,1073741824' \
     --data-binary "@{FILE_PATH}"
```

Response:

```
HTTP/1.1 200 OK
Content-Length: 0
```
