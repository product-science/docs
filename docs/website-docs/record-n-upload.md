Android
---------

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

### 6. Upload your trace and video

- Open your notification panel &gt; “Tap to share you trace”
- Tap the notification. You will have the option to save it or export it to different apps.

![upload-trace](//images.ctfassets.net/tab8wfn9nvlu/6Ax8quUV01SWijAhbaE7mp/611cb00ff510667efb9050f26832bb82/upload-trace.png)

- Select the Product Science app (PS)

- Name the trace, then assign it to the relevant user flow.

### If you have a screen recording…

- On the same screen, while the trace details screen is still opened, tap "Upload"
![upload-video](//images.ctfassets.net/tab8wfn9nvlu/7Ct8YPq7xdoqN7I4WAfo93/c9a4fe817c49c36c041d41a184aaa5a6/upload-video.png)
- Phone library opens &gt; select the screen recording &gt; "Upload"
- Wait for the status bar to change from "Video processing in progress" to "Video upload successfully"
- Tap "Upload"
- You can now view your trace in the PS Companion App

iOS
---------
