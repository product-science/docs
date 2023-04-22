# iOS Application Distribution Instructions
iOS applications are distributed as IPA archives. To export application it must be signed with some Apple Development Team certificate.


## Option 1: TestFlight
TestFlight is the default Apple tool for beta testing: [https://developer.apple.com/testflight/](https://developer.apple.com/testflight/)

### Distribution Process
1. _PS_: Send employee emails
2. _Client_: Build PS-injected app and upload it in TestFlight
3. _Client_: Invite Product Science emails as testers for uploaded app


## Option 2: Ad-Hoc IPA 
App can be distributed directly as **IPA** with two options for signing

### Distribution Process
1. _Client_: Build PS-injected app and export it as Ad-Hoc
2. _Client_: Send exported **IPA** to PS

<details>
  <summary>How to export app as ad-hoc in XCode</summary>
Product → Archive
  <img src="https://user-images.githubusercontent.com/80590/233219394-d0bfe1bc-08ca-4d84-8f32-50f4b803709c.png" alt="Archive">

Window → Organizer
<img src="https://user-images.githubusercontent.com/80590/233219478-dfca5016-a4cd-45dc-80bc-d2ce97fa02d9.png" alt="Organizer">

Distribute App → Ad-Hoc
<img src="https://user-images.githubusercontent.com/80590/233219560-9a10ba0c-8182-4348-b7be-fadba787fe62.png" alt="Ad-hoc">
</details>



### Signing Options
#### Best Option: Add PS Devices to Apple Development Account
App can be distributed directly as **IPA** and installed on device if device’s **UUID** is added to Apple Development account.

1. _PS_: Send employee devices **UUIDs**
2. _Client_: Add device to company’s devices list: [https://developer.apple.com/account/resources/devices/list](https://developer.apple.com/account/resources/devices/list)

*Limitations:* Apple Development allows only 100 added devices simultaneously. 

#### Risky Option: Re-Signing IPA After Build
In most cases an **IPA** can be re-signed with another Apple Development account after build, but this process is not guaranteed to work. *We don’t recommend to use it.*
