# CLI Tool Instructions - Android

## 1. Gradle Setup
Follow [Gradle Instructions](gradle.md) to setup build environment


## 2. Clean Build Directory and Run .jar
```
rm -rf ./**/build
./gradlew clean
java -jar integration-cli-{{ android_release() }}.jar "./gradlew :app:tfa:assembleDefaultRelease --stacktrace"
```

## 3. Share .apk and ps-output Directory with Us to Debug
Upload to Google Drive (or sharing service of your choice) and send to us
