# iOS Build Instructions - Xcode

### 1. Configure `productscience.yaml`  
Put this file into root of build directory
 
*This step is not needed if you use standalone build.*

### 2. Configure and Test `xcodebuild`

Prepare an `xcodebuild` command to build the app in terminal.  

For projects that are organized with `xcworkspace`: 

```bash 
xcodebuild \
    -workspace MyApp.xcworkspace \
    -scheme MyAppScheme \
    -sdk iphoneos
```

For `xcodeproj` based projects:  

```bash
xcodebuild \
    -project MyApp.xcodeproj \
    -scheme MyAppScheme \
    -sdk iphoneos
```
Ensure that your app can build successfully before using the `PSCliCodeInjector`.
A reference example using the Firefox Fennec iOS app is shown below.

### 3. Install `PSTools` Instrumentation Injection Kit

You will need to use the github credentials supplied by PSi to above to follow these steps:

1. Download the latest PSTools-PLATFORM.zip from our [public plugin repo](https://github.com/product-science/PSios/releases) and unzip it  
2. Install PSTools/PSCliCodeInjector.pkg on your Mac with double-click  
3. Copy PSTools/PSKit to ps-workdir i.e.  
`cp -r PSTools/PSKit .`

See the Firefox example below for sample final directory structure.

**Please label your build with the PSi Plugin Version from above i.e.**  
`MyAppPSi0.9.1.ipa` 
**so our AI can learn how its dynamic instrumentation is performing on the build.**

### 4. Build 

- Ensure that the `PSKit` tool folder is at the same folder level as your project i.e.:  
```
drwxr-xr-x@  5 user  staff       160 Jul 12 16:24 PSKit
drwxr-xr-x@  6 user  staff       192 Jul  5 10:22 PSTools
drwxr-xr-x  76 user  staff      2432 Jul 12 16:26 MyApp
```

- Run PSTool code transformation and configuration fine-tuning. The `PSCliCodeInjector` command must be run at the folder level above where the `.xcodeproj` sits and run against that folder. For example, if the project is `./MyApp/MyApp.xcodeproj` then from the `.` level folder run:  
```bash
PSCliCodeInjector MyApp \
    --backup-dir MyApp-BACKUP \
    --sub-folders=. \
    --console-build-command="<BUILD-COMMAND-FROM_STEP-3>"
```

This step transforms the code of within the `MyApp` project folder.  
A backup of the original `./MyApp` will be created at the same folder level where injection is run i.e. `./MyApp-BACKUP`.

The **BUILD-COMMAND-FROM_STEP-2** is the choice between the xcworkspace or xcodeproj methods and their associated flags. These are examples of xcodebuild templates- yours may differ. See the Firefox app example below.

⚠️ Warning: *PSCliCodeInjector parses the command’s output to identify issues with the injected code. Be sure not to pipe the build’s results through tools like xcbeautify, xcpretty, etc. or this logic might not work correctly.*

When complete, the `MyApp` directory will have been transformed. Use this directory for your build.

- Open project from `MyApp` directory
- Build and export the app in your default pipeline.
- Send us MyApp/psfilter.txt if it exists

**Please label your build with the PSi Plugin Version from above i.e.**  
`MyAppPSi0.9.1.ipa` 
**so our AI can learn how its dynamic instrumentation is performing on the build.**

### 5. Distribute Build
Please follow instructions at [iOS Distribution Instructions](distribution.md) to share your build with us


## Example: Firefox for iOS

### 1. Clone Firefox iOS repo

```bash
git clone https://github.com/mozilla-mobile/firefox-ios
```

### 2. Configure and test `xcodebuild`

In the `firefox-ios` directory

```bash
xcodebuild \
    -project Client.xcodeproj \
    -scheme Fennec \
    -destination 'name=iPhone 13 mini' \
    -sdk iphoneos
```

Note this example uses `iPhone 13 mini` as the example destination- this can be changed.

### 3. Create Creds and install PStools

Create the `productscience.yaml` file in the `firefox-ios` directory as shown in Step 2 above.

Download, unzip, and install `PStools` as shown in Step 4 above.

Make sure that the `PSKit` is in the same top level directory level as `firefox-ios`:  
```bash
cp -r PSTools/PSKit .
```
 i.e.

```bash
drwxr-xr-x@  5 user  staff       160 Jul 12 16:24 PSKit
drwxr-xr-x@  6 user  staff       192 Jul  5 10:22 PSTools
drwxr-xr-x  76 user  staff      2432 Jul 12 16:26 firefox-ios
```

*If you use standalone put `productscience.zip` archive in project directory.*

### 4. Build with `PSCliCodeInjector`

This is done in the same directory level as the `firefox-ios` directory i.e. the same one as shown above- NOT IN the `firefox-ios` directory:

```bash
drwxr-xr-x@  5 user  staff       160 Jul 12 16:24 PSKit
drwxr-xr-x@  6 user  staff       192 Jul  5 10:22 PSTools
drwxr-xr-x  76 user  staff      2432 Jul 12 16:26 firefox-ios
```

```bash
PSCliCodeInjector firefox-ios --backup-dir firefox-ios-BACKUP \
    --sub-folders=. \
    --console-build-command=\
      "xcodebuild \
          -project Client.xcodeproj \
          -scheme Fennec \
          -destination 'name=iPhone 13 mini' \
          -sdk iphoneos"
```

When complete, the `firefox-ios` directory will have been transformed. `firefox-ios-BACKUP` is a directory with original project.
```bash
drwxr-xr-x@  5 user  staff       160 Jul 12 16:24 PSKit
drwxr-xr-x@  6 user  staff       192 Jul  5 10:22 PSTools
drwxr-xr-x  76 user  staff      2432 Jul 12 16:26 firefox-ios
drwxr-xr-x  77 user  staff      2464 Jul 12 16:46 firefox-ios-BACKUP
```

Use `firefox-ios` for your pipeline or Xcode.
