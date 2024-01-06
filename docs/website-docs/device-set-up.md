To record a trace, first let’s get you set up.

These preparatory steps only need to be once.

Android
---------

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

![enable-developer-settings](https://images.ctfassets.net/tab8wfn9nvlu/54N2rjGPoLV3gNwjbc0fEQ/3f7085aff9471a77678fa56156fa1da2/enable-developer-settings.png)

#### Enable tracing and adjust corresponding settings

- Settings &gt; System &gt; Developer Options &gt; Debugging section &gt; System Tracing
- Make sure to turn off all options in __Categories__ except 'view: View System' and 'sched: CPU Scheduling'.

![enable-tracing](https://images.ctfassets.net/tab8wfn9nvlu/40myKppYxWNrExW8jAwYVx/b5c41fd6bb91711159c87a33023696e0/enable-tracing.png)

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

iOS
---------

### 1. Install [PS Companion app](https://apps.apple.com/au/app/ps-companion-app/id1634153033)

You will use PS Companion app later to upload traces and screen recordings to PS Tool.
Additionally, when recording app start, PS Companion app will be the place to start trace recording.

### 2. Log in with your PS Tool credentials

To log in to PS Companion app, you can use the same credentials you created while registering at productscience.app or use Google authentication.

[Click here](https://productscience.app/recovery-token) if you forgot your credentials.

[Click here](https://productscience.app/sign-up-trial) if you don't have an account yet.

### 3. Customize share sheet

To make it easier for upload your traces via PS PS Companion app, we recommend customizing your iPhone share sheet.

To complete this step, you can choose any file on your iPhone that can be shared or return to this step when uploading your first trace.

-   Tap the icon

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f0_tap_the_icon.png)

-   Once share sheet appears, look for PS Companion app among sharing options
-   If PS Companion App is not shown, swipe all the way to the right and tap "more"

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f1_tap_the_icon_more.png)

-   On the top right tap "Edit"
-   Tap the add button ![add button](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a598696ccbdb98f45ec2a1_lTMLy4rLgKRFfvSXlavweyyO8zHvxRoKSiyBW5yleclgwvJpISfWt67Rh08FzOZ_G0-fMvFg90C4xwz-TdTJokjeh6vgAMYqfemrL9vPPhfj8khYnk-DijuEjmJHDED6CZfapu1V_nYePve3KyCnSJyF1A2hbqhKKgP365cT5wKRP2dBVjI9XjyX23JhTA.png) next to PS Companion app

### 4. Make sure that Screen Recording is added to Control Center

Source: [Apple](https://support.apple.com/en-us/HT207935)

- Go to Settings &gt; Control Center, then tap the add button ![add button](https://assets-global.website-files.com/624bf3a77903d8b7ce4cc457/63a598696ccbdb98f45ec2a1_lTMLy4rLgKRFfvSXlavweyyO8zHvxRoKSiyBW5yleclgwvJpISfWt67Rh08FzOZ_G0-fMvFg90C4xwz-TdTJokjeh6vgAMYqfemrL9vPPhfj8khYnk-DijuEjmJHDED6CZfapu1V_nYePve3KyCnSJyF1A2hbqhKKgP365cT5wKRP2dBVjI9XjyX23JhTA.png) next to Screen Recording.
