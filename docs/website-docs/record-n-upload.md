Android
---------

## Record

### How to start a trace recording
The 'Record trace' button should be available in your quick settings tile. If it is not, go back to the section on [enabling trace recording](device-set-up.md#3-make-sure-tracing-is-enabled) and ensure you enabled __Show Quick Settings tile__.

### 1. Install instrumented app

Install the app that you want to analyze instrumented with PS plugin. Don't have the app? Learn [here](../android/gradle.md) how to build instrumented app.

### 2. Select a user flow you want to analyze

At Product Science, performance optimization starts with defining key user flows that bring the most value to users.

##### What is a user flow?

There are several ways to select a user flow:

- (**preferred**) __An "Action-Reaction" one step flow__. Here the user starts with an Action (pressing a button, swiping, selecting a menu item, etc) and you measure until a "Reaction", such as a new page being fully displayed. These flows are clean and simple to analyze.
- __More complex flows__. Sometimes, there are multiple steps that need to be strung together to get an idea of the performance of a feature. It can make sense to have flows like these, but consider carefully if they cannot be broken into smaller parts.

Either way, a sequence of functions execute before the user finally arrives at a final state. This is where our AI technology comes into play—highlighting these sequences that formed into what we call __execution paths__.

**Flows should be short, in the order of 30 seconds, to enable the analysis to be a manageable size.**


### 3. Get to the beginning of your user flow
Before you start recording:
1. Optional Step: [quit all open apps](https://support.google.com/android/answer/9079646?hl=en-IN#zippy=%2Cclose-apps) so nothing slows down the app you are measuring.
2. Navigate to the beginning of your user flow. If recording a trace for app start, just navigate to the icon for your app on the Home screen.

### 4. Start screen and trace recording
Start both the screen and trace recording as described above.

### 5. Execute your user flow.
Perform the user action to execute the identified user flow.

### 6. Stop recordings at the end of your flow
When you have reached the end of the user flow, swipe down from the top again to access the Quick Settings and tap both the "Record trace" and "Screen recorder" buttons to turn the recordings off.

## Upload

### 7. Upload your trace and video to PS Tool

- Open your notification panel &gt; “Tap to share you trace”
- Tap the notification. You will have the option to save it or export it to different apps.

![upload-trace](../images/upload-trace.png)

- Select the Product Science app (PS)

-   Name the trace, assign it to the relevant flow
  
#### Attach screen recording
- On the same screen, while the trace details screen is still opened, tap "Select"

- Phone library opens &gt; select the screen recording

![name-trace](../images/name-trace-android.png)


- Once trace and video finish uploading and processing, you can view your trace in PS Tool. Uploaded trace will appear in your productscience.app Flow Library.

iOS
---------

## Record

### 1. Install instrumented app

-   Install the app you [instrumented in the previous steps](../ios/distribution.md#ios-application-distribution-instructions). *Make sure it is instrumented. *

### 2. Select a user flow you want to analyze

At Product Science, performance optimization starts with defining key user flows that bring the most value to users.

##### What is a user flow?

There are several ways to select a user flow:

- (**preferred**) __An "Action-Reaction" one step flow__. Here the user starts with an Action (pressing a button, swiping, selecting a menu item, etc) and you measure until a "Reaction", such as a new page being fully displayed. These flows are clean and simple to analyze
- __More complex flows__. Sometimes, there are multiple that need to be strung together to get an idea of the performance of a feature. It can make sense to have flows like these, but consider carefully if they cannot be broken into smaller parts.

Either way, a sequence of functions execute before the user finally arrives at a final state. This is where our AI technology comes into play—highlighting these sequences that formed into what we call __execution paths__.

**Flows should be short, in the order of 30 seconds, to enable the analysis to be a manageable size.**

### 3. Trace and screen recording
‍
You can start traace recording from the instrumented app itself. If you want to capture app start on your trace recording, you can kick off trace recording from PS Companion app. 


| Step | To record App Start Flow    | To record any Flow other than App Start|
|:-----|:----------------------------|:---------------------------------------|
| 1    | Optionally, quit all open apps so nothing slows down the app you are measuring. | Optionally, quit all open apps so nothing slows down the app you are measuring. |
| 2    | Open PS Companion app. If you don't have a designated user flow for app start, create a new one. Go to the corresponding flow | Open your instrumented app and perform all the actions before beginning of your user flow. |
| 3    | Start screen recording      | Start screen recording                 | 
| 4    | At the bottom right corner, tap the ![rec-icon](../images/rec-icon.png) button to start trace recording | At the ![ios-start-recording](../images/ios-start-recording.png) panel, tap ![rec-icon](../images/rec-icon.png) button to start trace recording |
| 5    | Perform the user actions from the [(user) flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) and that you want to optimize. | Perform the user actions from the [(user) flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) and that you want to optimize. |
| 6    | Once the final step is fully loaded, at the ![ios-stop-recording](../images/ios-stop-recording.png) panel, tap ![stop-icon](../images/stop-icon.png)  button to stop recording. | Once the final step is fully loaded, at the ![](../images/ios-stop-recording.png) panel, tap ![stop-icon](../images/stop-icon.png)  button to stop recording. |

## Upload

### 4. Upload trace to PS Tool

-   Tap "Export" button to export your trace file.

![export-icon](../images/export-icon.png)

-   Choose PS Companion app among sharing options:

![share-companion-app](../images/share-companion-app.png)

[Don't see PS Companion app? Customize the share sheet](device-set-up.md#3-customize-share-sheet)

-   Name the trace, assign it to the relevant flow
#### Attach screen recording
- On the same screen, while the trace details screen is still opened, tap "Select"

- Phone library opens &gt; select the screen recording

![name-trace](../images/name-trace.png)

- Once trace and video finish uploading and processing, you can view your trace in PS Tool. Uploaded trace will appear in your productscience.app Flow Library.

