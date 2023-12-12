Essentials Steps
----------------

‍

To get unique insights to your code with our PS Tool, follow the step by step below:

[Instrumentation](https://docs.productscience.app/android/gradle/)
------------------------------------------------------------------

Instrument and build the app with our plugin, so it can analyze your code.

Read instrumentation documentation [here](https://docs.productscience.app/android/gradle/).

Recording
---------

Record the trace and video by running your instrumented app on the target device and walk through use flow you want to optimize.

-   ‍[What is a flow? Learn more about it](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow).
-   [How can screen recording helps to find insights faster? Learn more about it.](https://www.productscience.ai/documentation?doc=essentials-steps&sub=record-trace-with-video)

### Android

#### Preparation (Only Needs to be Done Once)

#### Install PS Companion app

-   Install [PS Companion app](https://play.google.com/store/apps/details?id=com.ps.companion&hl=en_US&gl=US)

-   Make sure to log in before moving on to the next step.

#### Enable tracing

1\. First, you'll need to enable developer options and USB debugging:

-   Settings > About Phone > Software information > Build Number
-   Tap the Build Number option 7 times

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb439c2_enable_tracing_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb439c2_enable_tracing_1_modal.png)

2\. Then, you can enable tracing:

-   Settings > System > Developer Options > Debugging section> System Tracing
-   Make sure to turn off all categories except view: View System and sched: CPU Scheduling

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb439c7_enable_tracing_2.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb439c7_enable_tracing_2.png)

-   Enable Show Quick Settings tile. This will add System Tracing tile to the Quick Settings panel, which appears as an upper panel: 

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb439c4_enable_tracing_3.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb439c4_enable_tracing_3.png)

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb439c5_enable_tracing_4.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb439c5_enable_tracing_4.png)

-   Hold down the "bug" button to yield the full trace menu
-   Enable "Long traces"
-   Set per CPU buffer size to maximum

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb439c6_enable_tracing_5.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb439c6_enable_tracing_5.png)

#### Trace and Screen Recording

##### Install instrumented app

-   Install the build of the app [instrumented in the previous steps](https://www.productscience.ai/documentation?doc=essentials-steps&sub=how-to-instrument). *Make sure your app is instrumented!*

##### Screen recording (optional but highly recommend)

-   Capturing how your application functions in real life provides valuable context that helps to understand what's happening - even when the code is hard to follow. With screen recording, you can see when the user interacts with the application (action: start of the user flow) and when the application screen is updated (reaction: end of the user flow). We highly recommend you to record your screen to complement your trace analysis.[\
    Learn more about how to make the most out of videos.](https://www.productscience.ai/documentation?doc=essentials-steps&sub=record-trace-with-video)

Record your phone screen (Source: [Google](https://support.google.com/android/answer/9075928?hl=en))

1.  Swipe down twice from the top of your screen.
2.  Tap Screen record ![screen recording button](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a57fbc8cfe911505c2d737_BYtciKd3s_XXk-9n7meutIUxIEjumxocLy28LoHIR_KnYVxHc_7TjXbMiBKbJDWG8DeMPMn2tWeiKFirlDAE_UOt9ApT3UANWYI7OW0RUMZw5exonaCGc3r8jIdklUmGYc6WYi7_RQ6xBk5_Nskq7Cdww_XnsTWVq7_SPXseXXmxagnn6FuVLl7UflUrZA.png)

-   You might need to swipe right to find it
-   If it's not there, tap Edit ![edit button](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a57fbc6c31f2df18205977_aXS6sj1Bc-lal1jNsGT_usEOVuSiw7dT5cyyTcyyXWCodEfQFWC34JnPAGoAHwF5w7mQXjL79ZtxrkfgaTFxdNm5i_MU9r7QRP9BpZpiWQ7u67juLdgc7nOfPIJYlYIb3QdIOXOkJgo5yvEmtG63BihKrgMLpuCSHjr7heHV8zbkUvIi9gnDUI03_K1Yzw.png) and drag Screen record ![screen recording button](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a57fbc8cfe911505c2d737_BYtciKd3s_XXk-9n7meutIUxIEjumxocLy28LoHIR_KnYVxHc_7TjXbMiBKbJDWG8DeMPMn2tWeiKFirlDAE_UOt9ApT3UANWYI7OW0RUMZw5exonaCGc3r8jIdklUmGYc6WYi7_RQ6xBk5_Nskq7Cdww_XnsTWVq7_SPXseXXmxagnn6FuVLl7UflUrZA.png) to your Quick Settings

4.  Choose what you want to record and tap Start. The recording begins after the countdown.
5.  To stop recording, swipe down from the top of the screen and tap the Screen recorder notification ![screen recording button](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a57fbc8cfe911505c2d737_BYtciKd3s_XXk-9n7meutIUxIEjumxocLy28LoHIR_KnYVxHc_7TjXbMiBKbJDWG8DeMPMn2tWeiKFirlDAE_UOt9ApT3UANWYI7OW0RUMZw5exonaCGc3r8jIdklUmGYc6WYi7_RQ6xBk5_Nskq7Cdww_XnsTWVq7_SPXseXXmxagnn6FuVLl7UflUrZA.png)

How to record when there is no screen recorder feature

‍‍

We recommend you to download 3rd party apps such as [Screen Recorder - XRecorder](https://play.google.com/store/apps/details?id=videoeditor.videorecorder.screenrecorder&hl=en_US&gl=US).

‍

Find screen recordings (Source: [Google](https://support.google.com/android/answer/9075928?hl=en))

1.  Open your phone's Photos app ![photos app button](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a57fbc05752a8305776984_9WdCoHfup_2URXFgPUobspSasORo-0_OMrDba9SMLa4a6alofzSL3Gn-cdx8HsFwCBuqU65jIXk0XiR0HgsI2d1D0GCk8Qp6B-nrKvhoR8bNpHts5f1Xy9jZOPHywxlwLGS0PKC65vFZWV-rnB0fpJSCkfizqsJqXqVoYygHBBdiTSbjCCt6Q9PSkrCqmg.png)
2.  Tap Library ![next button picture](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a57fbca7089c30cd946cdd_tHvnQHi7t5LT93lrY2mYxPov-S_kDm3H0vbVCxmEQFQFsERipQpVFkoyacGkqMCtUZSI56xQJ1HC96dR5m5MpWIqrRVH0kSr74M8ONmlKnS99IfE7fitnKc1G33OV4k7tNKzAjuFhZnuF_OdzjnWqkrH3-ew7LAYPBoElTmAA19Wy0r3XvxeDT53NSsapA.png) Movies

##### Record trace

Generally, we recommend recording traces with a [cold start](https://www.productscience.ai/documentation?doc=dictionary&sub=cold-app-start) where everything will be initialized from zero. This type of app launch is usually the slowest because the system has a lot of expensive work to do compared to the other two states (warm and [hot starts](https://www.productscience.ai/documentation?doc=dictionary&sub=hot-app-start) where the system brings the app running from the background to the foreground).

‍

Optimizing any user flow with [cold start](https://www.productscience.ai/documentation?doc=dictionary&sub=cold-app-start) enables you to improve all app processes that are being created from scratch which can enhance the same user flow's performance with warm and [hot starts](https://www.productscience.ai/documentation?doc=dictionary&sub=hot-app-start) as well.

‍

Step

To record App Start Flow

To record any Flow other than App Start

1

[Kill the targeted app](https://support.google.com/android/answer/9079646?hl=en#zippy=%2Cclose-apps)

[Kill the targeted app](https://support.google.com/android/answer/9079646?hl=en#zippy=%2Cclose-apps)

2

Make sure you are logged in to our PS Companion App.

Make sure you are logged in to our PS Companion App.

3

[Start screen recording (optional)*.](https://support.google.com/android/answer/9075928?hl=en)

Open the targeted app.

4

Start recording a trace by selecting the bug icon or 'record trace' button from the quick settings tile. 

Perform the user actions from the (user) flow and stop before the last step

5

Open the targeted app.

[Start screen recording (optional)*.](https://support.google.com/android/answer/9075928?hl=en)

6

Start recording a trace by selecting the bug icon or 'record trace' button from the quick settings tile. 

7

Perform the last step from the (user) flow

8

Once the main page is fully loaded, tap the bug icon or 'stop tracing' button to stop recording the trace. 

Once the main page is fully loaded, tap the bug icon or 'stop tracing' button to stop recording the trace. 

9

Stop screen recording (if needed).

Stop screen recording (if needed).

10

Wait for a "success" dialog drawn on top of your app.

Wait for a "success" dialog drawn on top of your app.

‍

Best Practices

-   Avoid doing any unnecessary actions outside of the [flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow).
-   Click and wait for each screen to fully load and any functions to complete before clicking on the following button (if necessary).
-   Avoid performing the [flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) too fast, and functions from different screens might overlap. 
-   Avoid performing the [flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) too slowly, and you are further away from understanding how a user will interact with the app.
-   [Record your screen!](https://www.productscience.ai/documentation?doc=essentials-steps&sub=screen-recording-optional-but-highly-recommend)\
    [Why? Learn more about it](https://www.productscience.ai/documentation?doc=essentials-steps&sub=record-trace-with-video)*\
    *

### iOS

#### Preparation (Only Needs to be Done Once)

##### Install our PS Companion App

-   Install [our PS Companion App](https://apps.apple.com/au/app/ps-companion-app/id1634153033)
-   Make sure to login before moving on to the next steps

##### Customize share sheet

To make it easier for exporting your traces in the upcoming steps, we recommend to customize your iPhone share sheet so that you can have the PS companion readily available.

-   Tap the icon

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f0_tap_the_icon.png)

-   Share sheet appear
-   If the PS Companion App is not shown, swipe all the way to the right
-   Tap more

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f1_tap_the_icon_more.png)

-   Tap Edit on the top right
-   Tap the green plus icon for PS Companion app

#### Trace and Video Recording

##### Install instrumented app

-   Install the app you [instrumented in the previous steps](https://www.productscience.ai/documentation?doc=essentials-steps&sub=instrumentation). *Make sure it is instrumented. *

##### Screen recording (optional but highly recommend)

-   Capturing how your application functions in real life provides valuable context that helps to understand what's happening - even when the code is hard to follow. With screen recording, you can see when the user interacts with the application (action: start of the user flow) and when the application screen is updated (reaction: end of the user flow). We highly recommend you to record your screen to complement your trace analysis.[\
    Learn more about how to make the most out of videos.](https://www.productscience.ai/documentation?doc=essentials-steps&sub=record-trace-with-video)

Record your phone screen (Source: [Apple](https://support.apple.com/en-us/HT207935))

1.  Go to Settings > Control Center, then tap the Add button ![add button](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a598696ccbdb98f45ec2a1_lTMLy4rLgKRFfvSXlavweyyO8zHvxRoKSiyBW5yleclgwvJpISfWt67Rh08FzOZ_G0-fMvFg90C4xwz-TdTJokjeh6vgAMYqfemrL9vPPhfj8khYnk-DijuEjmJHDED6CZfapu1V_nYePve3KyCnSJyF1A2hbqhKKgP365cT5wKRP2dBVjI9XjyX23JhTA.png) next to Screen Recording.
2.  [Open Control Center on your iPhone](https://support.apple.com/kb/HT202769) , or on your [iPad](https://support.apple.com/kb/HT210974).
3.  Tap the gray Record button ![record button](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a59869a7089cc41096201f_L3E75jeFeEuP5NYT2Fgi9Kk9pY3tV0EhJ9KYnvGcJS5VYTF9x5wQs17hQE1-tem16mg_uSmRush361RFwIhCptlim3oi4YwX5YgHP5Fr9oiUBEWNvmKqfuqhe2l0BfkxSFdW_c9q5MlTOPzrVAf8OgLil9s0zI_3VkVzs0jEUgZDZcxXzGytN6fKdSuVUA.png), then wait for the three-second countdown.
4.  Exit Control Center to record your screen.
5.  To stop recording, open Control Center, then tap the red Record button ![record button](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a5986af8cc912fe9314320_u78nv8cC3awXVnHuwD2nxHrYT-Dxhw_eyn5uADg9hL_UJDjr_QTdC5rgb8yb8RnayIIF_3ZzXlbTR_g2oQAvzvp9KENOXJMicedLkdOOrHgg7T__2J3Ooi4hUZadL4uJ6VABsPZo37yoZxL1Vd62wqBFcEAJ6Xpm5YsaLEhMvWFOgl1Bopb99HitwsjkCA.png). Or tap the red status bar at the top of your screen and tap Stop.

Find screen recordings

1.  Go to the Photos app and select your screen recording.

##### Record trace

Generally, we recommend recording traces with a [cold start](https://www.productscience.ai/documentation?doc=dictionary&sub=cold-app-start) where everything will be initialized from zero. This type of app launch is usually the slowest because the system has a lot of expensive work to do compared to the other two states (warm and [hot starts](https://www.productscience.ai/documentation?doc=dictionary&sub=hot-app-start) where the system brings the app running from the background to the foreground).

‍

Optimizing any user flow with [cold start](https://www.productscience.ai/documentation?doc=dictionary&sub=cold-app-start) enables you to improve all app processes that are being created from scratch which can enhance the same user flow's performance with warm and [hot starts](https://www.productscience.ai/documentation?doc=dictionary&sub=hot-app-start) as well.

‍

Step

To record App Start Flow

To record any Flow other than App Start

1

[Kill the targeted app](https://support.google.com/android/answer/9079646?hl=en#zippy=%2Cclose-apps)

[Kill the targeted app](https://support.google.com/android/answer/9079646?hl=en#zippy=%2Cclose-apps)

2

Make sure you are logged in to our PS Companion App.

Make sure you are logged in to our PS Companion App.

3

[Start screen recording (optional)*.](https://support.google.com/android/answer/9075928?hl=en)

Open the targeted app.

4

![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ffc437b9fbf009f15bc23_ios_start_rec.png)

Tap the ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ef05ff46b61311e879f55_rec_icon.png) button on PS Companion App to start recording

Perform the user actions from the(user) flow and stop before the last step.

5

Open the targeted app.

[Start screen recording (optional)*.](https://support.google.com/android/answer/9075928?hl=en)

6

Perform the user actions from the [(user) flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) and that you want to optimize.

![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ffc437b9fbf009f15bc23_ios_start_rec.png)

Tap the ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ef05ff46b61311e879f55_rec_icon.png) button on PS Companion App to start recording

7

Perform the last step from the (user) flow.

8

![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ffc54367bb5c36b6cf4c6_ios_stop_rec.png)

Once the final step is fully loaded, tap the button ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ef0a4eb698e0328f8c7c7_share_square_icon.png) to stop recording.

![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ffc54367bb5c36b6cf4c6_ios_stop_rec.png)

Once the final step is fully loaded, tap the button ![](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/633ef0a4eb698e0328f8c7c7_share_square_icon.png) to stop recording.

Uploading
---------

Upload recorded traces to PS Tool.

### Android

#### Upload trace to PS Tool

-   After recording a trace file, tap the file to export it. You will be given the option to save it or export it to different apps.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43839_saved_traces_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43839_saved_traces_modal.png)

-   Export your trace file to the PS Companion App\
    ‍\
    Alternatively, you can manually [upload](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=via-manual-upload) traces via web interface.\
    ‍
-   Name the trace, assign it to the relevant [flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) and then upload it to our cloud.
-   Uploaded trace will appear in your productscience.app Flow Library\
    ‍\
    Alternatively, you can enable the "subscribe" functionality in the Flow Library to get an email containing a link to a new trace when it uploads. [*\
    *Want to upload it via web interface? Learn how to.*\
    ‍*](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=add-new-trace)‍
-   For any errors, our system will return a message explaining what went wrong. If you can't resolve the issue, please don't hesitate to contact us at <support@productsience.ai>

#### PS Companion Mobile App Alternative

For the most seamless experience, we highly recommend using our [mobile app](https://www.productscience.ai/documentation?doc=essentials-steps&sub=recording) or uploading traces. 

But in instances where that fails, you can also upload traces via:

#### Export trace from the Files app

-   On mobile devices running Android 10 (API level 29), traces are shown in the Files app

#### Download traces with command line (Optional)

-   Connect your android device to a computer via USB
-   Command-line for downloading traces: adb pull /data/local/traces/

#### Manual upload via Web Interface

-   ‍[Learn How To](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=add-new-trace)

### iOS

#### Upload trace to PS Tool with PS Companion App

-   Tap the "export" button to export your trace file.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f0_tap_the_icon.png)

-   Open it with our PS companion app.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43842_open_with_companion_app.png)

[Don't see PS Companion app? Customize the share sheet](https://www.productscience.ai/documentation?doc=essentials-steps&sub=customize-share-sheet)

-   Name the trace, assign it to the relevant [flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) and then upload it to our cloud.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43843_name_trace_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43843_name_trace_modal.png)

-   Uploaded trace will appear in your productscience.app Flow Library.

    Alternatively, you can open the trace file via the link we sent to your email for every successful upload.*\
    *Or, upload via web interface. [Learn how to](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=add-new-trace).

-   For any errors, our system will return a message explaining what went wrong. If you can't resolve the issue, please contact us at <support@productsience.ai>.

#### View uploaded trace

-   You can find previously recorded traces organized by [user flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) under the Discover Projects tab
-   Select a flow to see the uploaded traces corresponding to that flow

#### Delete trace

-   To delete an uploaded trace, swipe left and select the trash icon

#### PS Companion Mobile App Alternative

##### Export trace file to computer (Optional)

1.  Open Finder > Locations > iPhone > Files
2.  Select the Application‌
3.  Airdrop or share the "trace.json" via iCloud to your computer

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438a1_export_trace_file_to_computer_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438a1_export_trace_file_to_computer_modal.png)

‍

##### Download with command line (Optional)

Also the open source app [ios-deploy](https://github.com/ios-control/ios-deploy) can be used for getting traces.

-   Install with Homebrew

```
brew install ios-deploy
```

-   Download trace.json

```
ios-deploy --bundle_id <APP'S BUNDLE ID>\\
    --download=/Documents/trace.json \\
    --to .
```

#### Manually upload trace to flow library

-   ‍[Learn How To](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=add-new-trace)

### Record Trace with Video

With the Video synced with trace feature you will be able to see what's happening on the phone screen at every point of the recorded trace.

Video synced with trace feature allows you to: 

-   Easily find the beginning and end of user flows
-   See the user actions in real life
-   Visually identify performance opportunities (like jitteriness, lags and long network requests)
-   Visually identify when the screen was updated 

The solid visual cues demonstrate precisely how the app works for your user or errors your app may be receiving that cannot be gained from the code alone. 

-   [Learn how to record your screens. (Android)](https://www.productscience.ai/documentation?doc=essentials-steps&sub=screen-recording-optional-but-highly-recommend)[‍](https://docs.google.com/document/d/1gzr2GEopvw7pbcjuya_Yke04CX5c-JaUdMnGM-OBvIA/edit#heading=h.42xpvpc3bgme)
-   [Learn how to record your screens. (iOS)](https://www.productscience.ai/documentation?doc=essentials-steps&sub=screen-recording-optional-but-highly-recommend1)[‍](https://docs.google.com/document/d/1gzr2GEopvw7pbcjuya_Yke04CX5c-JaUdMnGM-OBvIA/edit#heading=h.dhcsq0xfq99)
-   [Learn more about how to make the most out of the videos.](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=working-with-video)

#### Upload Screen Recordings

You can upload screen recordings to our tool either with our [companion app](https://www.productscience.ai/documentation?doc=essentials-steps&sub=via-ps-companion-app) or directly with [ PS Tool](https://www.productscience.ai/documentation?doc=essentials-steps&sub=via-ps-tool).

##### Via PS Companion App

-   In Flow > Select a user flow > Trace details screen opens.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43939_record_trace_with_video_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43939_record_trace_with_video_1_modal.png)

-   Tap 'Upload'.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393a_record_trace_with_video_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393a_record_trace_with_video_2_modal.png)

-   Phone library opens > select the screen recording > 'Upload'.
-   Wait for the status bar to change from 'Video processing in progress' to 'Video upload successfully'.
-   Upload success. You can now view and annotate the video in the PS Tool.

[Learn more about how to make the most out of the videos.](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=working-with-video)

##### Via PS Tool

-   In Trace Viewer > Open the Video Panel on the right.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393b_record_trace_with_video_3_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393b_record_trace_with_video_3_modal.png)

-   Click 'Upload a video.' 
-   Drag and drop or browse to upload a screen recording.
-   Once the upload is completed, you will see the global timeline replaced by the video.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393c_working_with_video_5_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393c_working_with_video_5_modal.png)

‍[Learn more about how to make the most out of the videos.](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=working-with-video)

#### Delete Screen Recordings

You can delete screen recordings uploaded either with our [companion app](https://www.productscience.ai/documentation?doc=essentials-steps&sub=via-ps-companion-app1) or directly with [ PS Tool](https://www.productscience.ai/documentation?doc=essentials-steps&sub=via-ps-tool1).

##### Via PS Companion App

-   In Flow > Select a user flow > Trace details screen opens.
-   Tap 'Delete'.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43933_record_trace_with_video_5.png)

##### Via PS Tool

-   In Trace Viewer > open up the Video panel on the right.
-   Click the trash icon.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43932_record_trace_with_video_6.png)

‍

[Learn more about how to make the most out of the videos.](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=working-with-video)
