Navigating PS Tool Components / PS Suit Main Components/ Product Science Tools
----------
_in the title trying to avoid confusion wether PS Tool reffers to the web tool 
for trace visualisation and analysis or for the whole PS offering_

Product Science offers a set of tools for advanced
mobile app tracing and intuitive performance analysis.

It consists of 3 main components:
- Product Science Plugin - a plugin used to autimatically
  instrument your app's code
- PS Companion App - an app used to seamlesly uplad traces and
  screen recordings to the cloud
- Product Science Tool - a web tool used for trace visualisation
  and performance analysis

See more details on each component below

### Product Science Plugin

PS Plugin, available for both Android and iOS, is a plugin that instruments your app's 
codebase.
It runs during the build process, instrumenting all functions and 
frameworks automatically without sampling.
For each instrumented method, PS Plugin allows to capture the following
data on a trace file:
- when it starts
- how long it run
- on which thread it runs
- which processes they call (child or async)
- additional data allowing to synchronise what was happening on the screen while 
this method was executing
  
#### AI-based filtering 
While PS Tool instruments all functions and frameworks of your app, recording 100% of that
data would create an enormous performance overhead, slowing your up down to the point when
it has nothing in common with real user experience.

There are different ways how different tools solve the overhead problem:
- **Sampling**: ... what it is and link to profiling
- **Manual instrumentation**: ... what it is, hard to maintain
- **Filtering**: ... what it is, finding the sweet spot, PS uses proprietary ML-based model...

**To integrate PS Plugin with your app**
- [click here](../integration/android/gradle.md) for Android instructions
- [click here](../integration/ios/xcode.md) for iOS instructions

### PS Companion App

PS Companion App, available both for Android and iOS, is an app that serves two main purposes:
- Easy uploading of trace and screen recording to PS Tool (trace viewer). 

  _Add why it is important_
- For iOS apps, to capture app start 

  _Add why it is important_

Download:
- Android PS Companion App
- iOS PS Companion App

### Product Science Tool (PS Tool)

PS Tool is you main destination to analyse traces
once your app had been instrumented and traces were recorded.


### Navigating PS Tool

If you already have an account, visit [productscience.app](http://productscience.app/)
and log in using your company email.

If you are new to PS Tool, and work with an Android app written on Java or Kotlin with 
Gradle build system, follow this link to sign-up for a free PS Tool self-serve beta. _insert link_

If you have an iOS app or your Android app does not satisfy the above criterea, follow us here
_insert link_


#### Team Space

Admin Screen
------------

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438fd_admin_screen_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438fd_admin_screen_modal.png)

#### Team

Team is the representation of a company. This is where you can create projects (per single app and operation system) that contain all [flows](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) and traces.

-   ‍[Learn more about what you can do as a Team Admin.](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=team-admin)

#### Project

Project is where you can create different flows and traces for a single app. You can join and contribute via an invitation from the team's or project's admin.

-   ‍[Learn more about what you can do as a Project Admin.](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=project-admin)

#### Collaborating

Roles and Permissions

‍

Every team member can have team-level permissions that determine their default access to projects.

#### Team Admin

##### Update Project Icons and Details

1. In Project > click "project settings"

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c8_update_project_settings_icon_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c8_update_project_settings_icon_modal.png)

2. Hover over the thumbnail > click on the image icon.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438fa_update_project_details_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438fa_update_project_details_modal.png)

##### Remove a Project

1. In Project > click "project settings"

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c8_update_project_settings_icon_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c8_update_project_settings_icon_modal.png)

2. Click "delete project"

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438fb_delete_project_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438fb_delete_project_modal.png)

##### Update Team Member's Role

1. In Team > click on "team contributors" to view the table.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cc_update_team_members_role_icon_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cc_update_team_members_role_icon_modal.png)

2. Click and choose new role under the "Role" Column.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438fc_update_team_member_role_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438fc_update_team_member_role_modal.png)

3. Click out to save

##### Resend Invitation Link

1. In Team> Team contributors > click on "team contributors" to view the table.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cc_update_team_members_role_icon_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cc_update_team_members_role_icon_modal.png)

2. Click the ".." button on the right of the table > menu appears.

3. Click "resend invitation link".

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ce_project_admin_resend_invitation_link_icon_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ce_project_admin_resend_invitation_link_icon_2_modal.png)

‍

##### Remove a Team Member

1. Project screen > click on "project contributors" to view the table.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cb_project_admin_remove_team_member_icon_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cb_project_admin_remove_team_member_icon_1_modal.png)

2. Click the "..." button on the right  side of the table > menu will appear.

3. Click "delete account".

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ce_project_admin_resend_invitation_link_icon_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ce_project_admin_resend_invitation_link_icon_2_modal.png)

##### Update Email Domain

1. Home page > click "team settings"

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cf_update_email_domain_icon_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cf_update_email_domain_icon_1_modal.png)

2. Update your company email domain so that everyone with the specified email domain can log in.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d0_update_email_domain_icon_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d0_update_email_domain_icon_2_modal.png)

#### Project Admin

##### Update Team Member's Role in Project

1. In Project > click on "project contributors" to view the table.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cb_project_admin_remove_team_member_icon_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cb_project_admin_remove_team_member_icon_1_modal.png)

2. Click and choose a new role under the "Role" Column.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438fc_update_team_member_role_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438fc_update_team_member_role_modal.png)

3. Click out to save

##### Remove Team Member

1. In Project > Project contributor > click on "project contributors" to view the table

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cb_project_admin_remove_team_member_icon_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cb_project_admin_remove_team_member_icon_1_modal.png)

2. Click the ".." button on the rightest of the table > menu appears

3. Click "delete account'"

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ce_project_admin_resend_invitation_link_icon_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ce_project_admin_resend_invitation_link_icon_2_modal.png)

##### Invite New Team Member

1. In Project > Project contributor > click "invite contributor" on the top right corner.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d1_project_admin_invite_team_member_icon_1.png)

2. Input the email and select the role.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d2_project_admin_invite_team_member_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d2_project_admin_invite_team_member_modal.png)

3. Click "Invite"

##### Resend Invitation Link

1. In Project > Project contributor > click on "project contributors": to view the table.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cb_project_admin_remove_team_member_icon_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438cb_project_admin_remove_team_member_icon_1_modal.png)

2. Click the ".." button on the far right side of the table of the table > menu will appear.

3. Click "resend invitation link".

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ce_project_admin_resend_invitation_link_icon_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ce_project_admin_resend_invitation_link_icon_2_modal.png)

#### Flow Library

Flow library organizes all traces by [(user) flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow). This is where you can view, subscribe, manage and create [flows](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow). Like a folder in a file system, each [flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) contains traces of user flows that your team records and optimizes. Use Flow Library to group traces by [flows](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow) that make the most sense to you and your team. Add a description to communicate the context of the [flows](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow).

### Open a trace in PS Tool

Flow Library > Select a flow card > Flow Table > right click any trace > click "open"

### Create new flow

1. In Flow Library > click "Create new flow"

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438a9_create_new_flow.png)

2. Enter your flow name & description

(User) Flow Screen
------------------

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438e4_flow_screen_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438e4_flow_screen_modal.png)

The Flow Screen is where you can find all the traces uploaded associated with a single [flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow). This is where you can [add](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=add-new-trace), [delete](https://www.productscience.ai/documentation?doc=essentials-steps&sub=delete-trace), [edit](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=edit-flow-description), and [assign](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=assign-trace-to-another-flow) your trace.

‍

We encourage you to record more than one trace for every [flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow). More recordings can increase the statistical significance of your "findings". Specifically for flows containing asynchronous I/O operations like network requests, recording multiple traces can increase your confidence in locating patterns of performance issues within the trace.

### Add new trace

#### Via our PS Companion app

-   ‍[Learn How To](https://www.productscience.ai/documentation?doc=essentials-steps&sub=uploading)

#### Via manual upload

1. Click the "Add new trace" button on the Flow screen

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438aa_via_manual_upload.png)

2. Upload traces by dragging the trace or browse from computer

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ab_upload_new_trace_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ab_upload_new_trace_modal.png)

3. Once the trace is uploaded successfully, you shall see the message

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ac_uploaded_trace_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ac_uploaded_trace_modal.png)

#### Via select from unassigned

Alternatively, you can use traces that were previously uploaded but not assigned.

‍

1. Click on "Review and assign" button

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ad_review_and_assign.png)

2. Check the box for the trace you would like to assign

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ae_select_from_unassigned_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ae_select_from_unassigned_modal.png)

3. Select the flow you would like to flow to be assigned to

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438af_assign_trace_name_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438af_assign_trace_name_modal.png)

#### Delete flow

1. In Flow Library > hover over the bottom right corner of flow

2. Click on the "..." button on the flow card

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b1_delete_flow.png)

#### Edit flow description

1. Flow Library > Flow card > Flow settings

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b2_edit_flow_description_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b2_edit_flow_description_modal.png)

#### Assign trace to another flow

1. In the Flow screen

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b4_assign_trace_to_another_flow_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b4_assign_trace_to_another_flow_modal.png)

2. Click on the trace > menu will appear > click "Assign"

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b5_assign_trace_to_another_flow_btns_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b5_assign_trace_to_another_flow_btns_modal.png)

3. Select one or multiple flows you want to assign the trace to > Click "Done"
