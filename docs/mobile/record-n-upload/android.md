# Android Trace Recording

## Record


### 1. Install instrumented app

Install the app you want to analyze that is instrumented with PS plugin. Don't have the app? Learn how to build the instrumented app [here](../integration/android/gradle.md).

### 2. Select a user flow you want to analyze

At Product Science, performance optimization starts with defining key user flows that bring the most value to users.

##### What is a user flow?

There are several ways to select a user flow:

- [**Preferred**] __An "Action-Reaction" one-step flow__. Here, the user starts with an "Action" (pressing a button, swiping, selecting a menu item, etc) and you measure until a "Reaction" (new page being fully displayed, etc). These flows are clean and simple to analyze.
- __More complex flows__. Sometimes, there are multiple steps that need to be strung together to get an idea of the performance of a feature. It can make sense to have flows like these, but consider carefully if they can be broken down into smaller parts.

Either way, a sequence of functions execute before the user finally arrives at the final state ("Reaction"). This is where our AI technology comes into play—highlighting the sequences that formed into what we call __execution paths__.

**Note: User flows should be short in length, 30 seconds or less, to enable the analysis to be a manageable size.**

### 3. Get to the beginning of your user flow
Before you start recording:
1. [Optional Step] [Quit all open apps](https://support.google.com/android/answer/9079646?hl=en-IN#zippy=%2Cclose-apps) so nothing slows down the app you are measuring.
2. Navigate to the beginning of your user flow. If recording a trace for app start, just navigate to the icon for your app on the Home screen.

### 4. Start screen and trace recording
Start both the screen and trace recording as described above.

The 'Record trace' button should be available in your quick settings tile. If it is not, go back to the section on [enabling trace recording](../device-set-up/android.md#3-make-sure-tracing-is-enabled) and ensure you enabled the __Show Quick Settings tile__.

![quick-settings](../../images/quick-settings.png)

### 5. Execute your user flow
Perform the user action to execute the user flow you are analyzing.

### 6. Stop recordings at the end of your flow
When you have reached the end of the user flow ("Reaction"), swipe down from the top of your screen again to access Quick Settings and tap both the "Record trace" and "Screen recorder" buttons to turn the recordings off.

## Upload

There are two ways to upload a trace file and video to PS Tool, via web or via the PS Companion app. 

### 7. Upload your trace and video to PS Tool via web

- To transfer traces from your phone to your computer, use adb pull /data/local/traces/ or any file sharing method of your choice
- Go to PS Tool https://productscience.app/ on your computer
- Select or create a user flow folder for the analysis
- Open the user flow folder and click on Add trace in the top right corner of the screen 
- Once your trace is uploaded, open it and go to the the Annotations screen
- From the Annotations screen, click Upload video and select the video file

<img width="550" alt="Screenshot 2025-01-17 at 4 09 17 PM" src="https://github.com/user-attachments/assets/752f3589-a0a9-43ee-ac07-16cd20f1c219" />


### 8. Upload your trace and video to PS Tool via the PS Companion app

- Open your notification panel &gt; “Tap to share you trace”
- Tap the notification. You will have the option to save it or export it to different apps

![upload-trace](../../images/upload-trace.png)

- Select the Product Science app (PS)

-   Name the trace, assign it to the relevant user flow folder
  
#### Attach screen recording
- On the same screen, while the trace details screen is still opened, tap "Select"

- Phone library opens &gt; select the screen recording

![name-trace-android](../../images/name-trace-android.png)

- Once the trace and video finish uploading and processing, you can view your trace in PS Tool. The uploaded trace will appear in your productscience.app User Flow Library.
