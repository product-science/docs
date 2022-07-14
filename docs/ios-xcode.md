# IOS Instructions:

## Preparation
1. Set up Xcode build with the Product Science Instrumentation Injector from the Product Science Github repo (see instructions below)
2. Determine a named developer resource for Product Science to partner with for generating new builds
3. Ideally create a trigger for Product Science to generate new builds to increase speed of the Optimization process

## Optimization Loop
The Loop is repeated by your developers 20+ times initially and 5+ times with every major update.

1. [Your devs]  Build the app with PSi Xcode instrumentation
2. Ideally Product Science is provided with a trigger to create automation- otherwise a named developer can be supplied to rebuild
3. [Your devs]  Provide a cloud link to your .ipa
4. [Product Science] Runs the app and collects app performance data
5. Optimization may finish and we proceed to Insight Generation
6. [Product Science] Feeds the app performance data to Product Science optimization algorithms
7. [Product Science] Algorithms update model in the Product Science Github repo
8. [Your devs] Next build will use the new model from the Product Science Github repo automatically

## Xcode Instructions

### 1. Key Generation Methodology- PSi:  
* Generates a token (key) via GitHub
* Saves key in Bitwarden credential storage
* Shares token with Bitwarden Send 
* Keys have an expiration date

### 2. Configure `productscience.yaml`  

 Set up `productscience.yaml` in the Xcode app project directory:  
```bash
productscience.github.config:=<supplied-by-PSi>
productscience.github.token:=<supplied-by-PSi>
```

example `productscience.yaml`:  

```bash
productscience.github.config: product-science-configs:ios-template-configs:config.yaml:main
productscience.github.token: ghp_XXXXXXXXXXXXXXX
```

### 3. Configure and Test `xcodebuild`

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

### 4. Install `PSTools` Instrumentation Injection Kit

You will need to use the github credentials supplied by PSi to above to follow these steps:

1. Download PSTools.zip from [this link](https://github.com/product-science/PSios/releases/tag/1.1.0) and unzip it  
2. Install PSTools/PSCliCodeInjector.pkg on your Mac with double-click  
3. Copy PSTools/PSKit.xcframework to ps-workdir i.e.  
`cp -rf PSTools/PSKit.xcframework .`

See the Firefox example below for sample final directory structure.

### 5. Build 

- Run PSTool code transformation and configuration fine-tuning:
```bash
PSCliCodeInjector MyApp MyApp-ps \
    --sub-folders=. \
    --console-build-command="<BUILD-COMMAND-FROM_STEP-3>"
```

This step transforms the code of the MyApp and stores the transformed version in `MyApp-ps` folder.  

The **BUILD-COMMAND-FROM_STEP-2** is the choice between the xcworkspace or xcodeproj methods and their associated flags. These are examples of xcodebuild templates- yours may differ. See the Firefox app example below for examples.

⚠️ Warning: *PSCliCodeInjector parses the command’s output to identify issues with the injected code. Be sure not to pipe the build’s results through tools like xcbeautify, xcpretty, etc. or this logic might not work correctly.*

When complete, a new directory called `myapp-ps` will have been created. This is the instrumented version of `myapp`. Use this one (`myapp-ps`) for your build.

- Change to the `MyApp-ps` directory
- Build and export the app in your default pipeline.
- Send us MyApp/psfilter.txt if it exists

## Example: Firefox for iOS

### 1. Clone Firefox iOS repo

```bash
git clone https://github.com/mozilla-mobile/firefox-ios
```

### 2. Configure and text `xcodebuild`

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

Make sure that the `PSKit.xcframework` is in the same top level directory level as `firefox-ios` i.e.

```bash
drwxr-xr-x@  5 user  staff       160 Jul 12 16:24 PSKit.xcframework
drwxr-xr-x@  6 user  staff       192 Jul  5 10:22 PSTools
drwxr-xr-x  76 user  staff      2432 Jul 12 16:26 firefox-ios
```

### 4. Build with `PSCliCodeInjector`

This is done in the same directory level as the `firefox-ios` directory i.e. the same one as shown above- NOT IN the `firefox-ios` directory:

```bash
drwxr-xr-x@  5 user  staff       160 Jul 12 16:24 PSKit.xcframework
drwxr-xr-x@  6 user  staff       192 Jul  5 10:22 PSTools
drwxr-xr-x  76 user  staff      2432 Jul 12 16:26 firefox-ios
```

```bash
PSCliCodeInjector firefox-ios firefox-ios-ps \
    --sub-folders=. \
    --console-build-command=\
      "xcodebuild \
          -project Client.xcodeproj \
          -scheme Fennec \
          -destination 'name=iPhone 13 mini' \
          -sdk iphoneos"
```

When complete, a new directory called `firefox-ios-ps` will have been created. This is the instrumented version of `firefox-ios`

```bash
drwxr-xr-x@  5 user  staff       160 Jul 12 16:24 PSKit.xcframework
drwxr-xr-x@  6 user  staff       192 Jul  5 10:22 PSTools
drwxr-xr-x  76 user  staff      2432 Jul 12 16:26 firefox-ios
drwxr-xr-x  77 user  staff      2464 Jul 12 16:46 firefox-ios-ps
```

This new `ps` directory is the one to use for the instrumented build. Use this one (`firefox-ios-ps`) for your pipeline or Xcode.
