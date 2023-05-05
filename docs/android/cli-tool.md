# CLI Tool Instructions - Android

## 1. Gradle Setup
Follow [Gradle Instructions](gradle.md) to setup build environment


## 2. Clean Build Directory and Run .jar
```
rm -rf ./**/build
./gradlew clean
java -jar integration-cli-{{ android_release() }}.jar "./gradlew assemble --stacktrace"
```

## 3. Share .apk and ps-output Directory
Upload to Google Drive (or sharing service of your choice) and send to us
