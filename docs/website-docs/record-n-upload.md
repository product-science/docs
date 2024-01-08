Android
---------

## Record

### How to start a trace recording
The 'Record trace' button should be available in your quick settings. If it is not, go back to the section on enabling trace recording **INSERT LINK** and ensure you enabled __Show Quick Settings tile__.

### 1. Install instrumented app

Install the app that you want to analyze instrumented with PS plugin. Don't have the app? Learn [here](https://docs.productscience.app/android/gradle/) how to build instrumented app.

### 2. Select a user flow you want to analyze

At Product Science, performance optimization starts with defining key user flows that bring the most value to users.

##### What is a user flow?

There are several ways to select a user flow:

- (**preferred**) __An "Action-Reaction" one step flow__. Here the user starts with an Action (pressing a button, swiping, selecting a menu item, etc) and you measure until a "Reaction", such as a new page being fully displayed. These flows are clean and simple to analyze
- __More complex flows__. Sometimes, there are multiple that need to be strung together to get an idea of the performance of a feature. It can make sense to have flows like these, but consider carefully if they cannot be broken into smaller parts.

Either way, a sequence of functions execute before the user finally arrives at a final state. This is where our AI technology comes into play—highlighting these sequences that formed into what we call __execution paths__.

**Flows should be short, in the order of 30 seconds, to enable the analysis to be a manageable size.**


### 3. Get to the beginning of your user flow
Before you start recording:
1. Optionally, [quit all open apps](https://support.google.com/android/answer/9079646?hl=en-IN#zippy=%2Cclose-apps) so nothing slows down the app you are measuring.
2. Navigate to the beginning of your user flow. If this is launching the app, just navigate to the icon for your app on the Home screen.

### 4. Start screen and trace recording
Start both the screen and trace recording as described above.

### 5. Stop recordings at the end of your flow
- Execute your user flow.
- When you have reached the end of the user flow, swipe down from the top again to access the Quick Settings and tap both the "Record trace" and "Screen recorder" buttons to turn the recordings off.

## Upload

### 6. Upload your trace and video to PS Tool

- Open your notification panel &gt; “Tap to share you trace”
- Tap the notification. You will have the option to save it or export it to different apps.

![upload-trace](https://images.ctfassets.net/tab8wfn9nvlu/6Ax8quUV01SWijAhbaE7mp/611cb00ff510667efb9050f26832bb82/upload-trace.png)

- Select the Product Science app (PS)

- Name the trace, then assign it to the relevant user flow.

### Attach screen recording

- On the same screen, while the trace details screen is still opened, tap "Upload"
![upload-video](https://images.ctfassets.net/tab8wfn9nvlu/7Ct8YPq7xdoqN7I4WAfo93/c9a4fe817c49c36c041d41a184aaa5a6/upload-video.png)
- Phone library opens &gt; select the screen recording &gt; "Upload"
- Tap "Upload"
- Once trace and video finish uploading and processing, you can view your trace in PS Tool. Uploaded trace will appear in your productscience.app Flow Library.


iOS
---------

## Record

### 1. Install instrumented app

-   Install the app you [instrumented in the previous steps](https://www.productscience.ai/documentation?doc=essentials-steps&sub=instrumentation). *Make sure it is instrumented. *

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
Optimizing any user flow with [cold start](https://www.productscience.ai/documentation?doc=dictionary&sub=cold-app-start) enables you to improve all app processes that are being created from scratch which can enhance the same user flow's performance with warm and [hot starts](https://www.productscience.ai/documentation?doc=dictionary&sub=hot-app-start) as well.


| Step | To record App Start Flow    | To record any Flow other than App Start|
|:-----|:----------------------------|:---------------------------------------|
| 1    | Optionally, quit all open apps so nothing slows down the app you are measuring. | Optionally, quit all open apps so nothing slows down the app you are measuring. |
| 2    | Open PS Companion app. If you don't have a designated user flow for app start, create a new one. Go to the corresponding flow | Open your instrumented app and perform all the actions before beginning of your user flow. |
| 3    | Start screen recording      | Start screen recording                 | 
| 4    | At the bottom right corner, tap the ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ef05ff46b61311e879f55_rec_icon.png) button to start trace recording | At the ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ffc437b9fbf009f15bc23_ios_start_rec.png) panel, tap ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ef05ff46b61311e879f55_rec_icon.png) button to start trace recording |
| 5    | Perform the user actions from the [(user) flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) and that you want to optimize. | Perform the user actions from the [(user) flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) and that you want to optimize. |
| 6    | Once the final step is fully loaded, at the ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ffc54367bb5c36b6cf4c6_ios_stop_rec.png) panel, tap ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ef0a4eb698e0328f8c7c7_share_square_icon.png)  button to stop recording. | Once the final step is fully loaded, at the ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ffc54367bb5c36b6cf4c6_ios_stop_rec.png) panel, tap ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ef0a4eb698e0328f8c7c7_share_square_icon.png)  button to stop recording. |

## Upload

### 4. Upload trace to PS Tool

-   Tap "Export" button to export your trace file.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f0_tap_the_icon.png)

-   Choose PS Companion app among sharing options:

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43842_open_with_companion_app.png)

[Don't see PS Companion app? Customize the share sheet](https://www.productscience.ai/documentation?doc=essentials-steps&sub=customize-share-sheet)

-   Name the trace, assign it to the relevant [flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) and then upload it to PS cloud.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43843_name_trace_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43843_name_trace_modal.png)

### Attach screen recording

- On the same screen, while the trace details screen is still opened, tap "Upload"
![upload-video](https://images.ctfassets.net/tab8wfn9nvlu/7Ct8YPq7xdoqN7I4WAfo93/c9a4fe817c49c36c041d41a184aaa5a6/upload-video.png)
- Phone library opens &gt; select the screen recording &gt; "Upload"
- Tap "Upload"
- Once trace and video finish uploading and processing, you can view your trace in PS Tool. Uploaded trace will appear in your productscience.app Flow Library.
