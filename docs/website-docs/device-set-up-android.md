Android
---------

To record a trace, first let’s get you set up.

These preparatory steps only need to be once.

### 1. Install [PS Companion app](https://play.google.com/store/apps/details?id=com.ps.companion&hl=en_US&gl=US&pli=1) 

You will use PS Companion app later to upload traces and screen recordings to PS Tool.

### 2. Log in with your PS Tool credentials

To log in to PS Companion app, you can use the same credentials you created while registering at productscience.app or use Google authentication.

[Click here](https://productscience.app/recovery-token) if you forgot your credentials.

[Click here](https://productscience.app/sign-up-trial) if you don't have an account yet.

### 3. Make sure tracing is enabled
Individual phones may have different ways to do this, but these are general guidelines. **Please review these settings even if you are familiar with trace recording on Android, there are some specific settings**

For complete documentation, see the [Official Android Documentation](https://developer.android.com/studio/debug/dev-options)

#### Enable developer options and USB debugging

- Settings &gt; About Phone &gt; Software information &gt; Build Number
- Tap the Build Number option __7 times__

![enable-developer-settings](../images/dev-options.png)

#### Enable tracing and adjust corresponding settings

- Settings &gt; System &gt; Developer Options &gt; Debugging section &gt; System Tracing
- Make sure to turn off all options in __Categories__ except 'view: View System' and 'sched: CPU Scheduling'.

![enable-tracing](../images/enable-tracing.png)

- Set __Per-CPU buffer size__ to maximum
- Enable __Long traces__
- Enable __Show Quick Settings tile__. This will add Record Trace tile to the Quick Settings panel

### 4. Make sure that you have Screen Recording at hand

Source [Google](https://support.google.com/android/answer/9075928?hl=en)

- Swipe down twice from the top of your screen to reveal Quick Settings tiles.
- You might need to swipe right to find Screen Recorder
- If it's not there, tap 'Edit buttons' and drag Screen recorder to your Quick Settings. 'Edit buttons' can be accessed using the more options button in the upper right.
- If you don't have the build in screen recorder
We recommend you to download 3rd party apps such as [Screen Recorder - XRecorder](https://play.google.com/store/apps/details?id=videoeditor.videorecorder.screenrecorder&hl=en_US&gl=US)

