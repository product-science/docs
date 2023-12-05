# CLI Tool Integration Instructions - Android
The CLI tool is a small wrapper around gradlew build command that reads build output and filters unsupported classes in Product Science instrumentation. It will build the specified release in a loop until successful.

## 1. Gradle Setup
First follow [Gradle Instructions](gradle.md) up to step 6: Build your app (this will be used after integration) to setup build environment

## 2. Download CLI Tool
Download the CLI tool .jar from our Artifactory: [Download here](https://artifactory.productscience.app/#/releases/com/productscience/integration/integration-cli/{{ android_release() }}/integration-cli-{{ android_release() }})

## 3. Clean Build Directory and Run .jar
integration-cli is a CLI on top of Gradle which automates integration with the PS Plugin by receiving your regular gradle build command as input. Please use flag *--stacktrace* together with gradle command.

#### 1. We recommend cleaning your project before starting:
```
rm -rf ./**/build
./gradlew clean
```

#### 2. Run the jar with your normal Gradle command. 

*Example:*
If you build the project with `./gradlew assembleRelease` your integration-cli command will look like:
```
java -jar integration-cli.jar "./gradlew assembleRelease --stacktrace"
```

## 4. Share .apk and ps-output Directory
Upload to Google Drive (or sharing service of your choice) and share with us
