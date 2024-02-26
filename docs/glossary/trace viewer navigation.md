 Trace Viewer
----------

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b6_trace_viewer_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b6_trace_viewer_modal.png)

A trace is a time series snapshot of your app. Our dynamic, multi-threaded tracing tool captures and measures all functions executed during the recording. While millions of events and functions might be executed on the system level, our AI filters key functions that impact your user experience the most while filtering out all irrelevant information.

Slices

‍

The width of the trace represents duration of the executed process while where it positions indicates the start time. A slice represents a single unit of work done by the CPU, and the width (X-Axis) of the slice represents the duration of the executed process and its position indicates the start time. Learn more

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d3_slicename.png)\
The nesting (Y-Axis) of slices represents the call stack of a specific function.

In the image below, you can see how function B ( Slice B ) was called by function A (slice A)

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f2_trace_viewer_slicenames.png)

-   ‍[Learn how to](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=Slices)\
    ‍

Execution Path

‍

The execution path is the most helpful tool to determine where the delays are coming from. It shows which function call stacks  are called by which function call stacks, so you can quickly see not just how individual functions are related but by how groupings of functions are related, creating an elevated perspective of the code which makes it easier to zoom-out and quickly find the root cause of a problem.

-   ‍[Learn how to](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=execution%20paths)

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d8_execution_paths_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d8_execution_paths_modal.png)

#### Navigate main timeline

The center of the dashboard is what we call *the main timeline *of your user flow. It tells you about your different processes at a specific time. Though you won't be able to view the details of slices here, you can see when your app is fully loaded and when it's idling.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b7_navigate_aggregation_view_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b7_navigate_aggregation_view_modal.png)

To navigate the main timeline view, in addition to your trackpad, you can use the following key commands:

W - Zoom in

S - Zoom out

A - Move left

D - Move right

#### Navigate aggregation view (global timeline)

In the timeline near the top of the dashboard, you'll see what looks like a measuring tape.

-   Numbers at the top indicate where you are based on the trace's timeline.
-   Numbers at the bottom measure the distance between functions on the trace or the time it takes for a function to execute.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d9_navigate_global_timeline_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d9_navigate_global_timeline_2_modal.png)

You can adjust the focus area by dragging the blue limit handles located on the edges.

#### Slices

The visual representation of a code's function/process. The length of the slice indicates how long it takes that process to execute.

‍

The width of the slice represents the duration of the executed process and its position indicates the start time.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d3_slicename.png)

#### Property Panel

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d8_execution_paths_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d8_execution_paths_modal.png)

The property panel allows you and your contributors to:

-   View and copy details of the slices including slice name, thread name, slice ID, object ID, start time, and duration.
-   [Create manual connections](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=create-manual-connections)
-   Find [execution path](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=execution-paths)-related tools such as:\
    ‍\
    Show/hide all paths

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4394b_show_hide_paths_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4394b_show_hide_paths_modal.png)

Sort threads by execution path

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4394a_sort1_to_prioritize_exec_path_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4394a_sort1_to_prioritize_exec_path_modal.png)

Dim slices outside of execution path

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4394c_dim_slices_outside_paths_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4394c_dim_slices_outside_paths_modal.png)

-   Review connections
-   Customize [flags](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=place-a-flag)

#### Execution Paths

1. Click on any slice and our system will automatically check any [connections](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=create-manual-connections) linked to this slice. In other words, we highlight actions and processes that occurred resulting in the slice you chose.

2. Once an execution path -- a one-directional linked list of slices --  is found, you should see lines like the example below. For example, if Slice A calls Slice B, they will be connected.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d8_execution_paths_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d8_execution_paths_modal.png)

The green path is what we refer to as the main execution path; it usually contains more slices than the other lines and gives you a better image of where the delays are located.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438bc_execution_paths_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438bc_execution_paths_1_modal.png)

3. Open property panel

4. Click the button below to hide/show other non-main execution paths

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438bd_execution_paths_icon.png)

Example of clicking the filtering button to only show the main execution path

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438be_execution_paths_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438be_execution_paths_2_modal.png)

5. View slice and connection details on the property panel (right side)

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438bf_execution_paths_3_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438bf_execution_paths_3_modal.png)

#### Create manual connections

1. Click on a slice > Slice details show in the [property panel](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=property-panel).

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d8_execution_paths_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438d8_execution_paths_modal.png)

2. Click the "create connection" icon next to the slice or press C while the slice is selected.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c0_create_manual_connections_icon%20.png)

‍

3. Slices that cannot be connected to the slice clicked are dimmed.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c1_create_manual_connections_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c1_create_manual_connections_1_modal.png)

4. Repeat step 2 to connect more slices.

#### Working with Video

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393d_working_with_video_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393d_working_with_video_1_modal.png)

In the Trace Viewer, you can find the Video panel next to the Details panel where you can view, [upload,](https://www.productscience.ai/documentation?doc=essentials-steps&sub=upload-screen-recordings) [play, pause](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=play-pause-video) and [remove](https://www.productscience.ai/documentation?doc=essentials-steps&sub=delete-screen-recordings) screen recording of your traces.

##### Switch between Aggregated and Video views 

Option 1: Use the View Toggle [Soon to be released]

-   Trace Viewer > Left of the global / aggregated view timeline;
-   Click on the button toggle to switch between aggregated or video views.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43946_working_with_video_timeline_toggle_11.png)

Option 2: Switch between Panels

-   Click on the Video panel > Bring you to the video view where the video frames replace the global timeline.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393c_working_with_video_5_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393c_working_with_video_5_modal.png)

-   Click on the Details panel >  Bring you back to the default, aggregated view of the trace.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393e_working_with_video_4_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393e_working_with_video_4_modal.png)

##### Set Focus Area

On the Main Timeline

-   Trace Viewer > [Enable video view](https://www.productscience.ai/documentation?doc=working-with-ps-tool&sub=working-with-video).
-   Shift-drag the beginning or end of the focus area - it will adjust the beginning and the end of what you see on the main timeline.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393c_working_with_video_5_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393c_working_with_video_5_modal.png)

-   The focus area selected will automatically sync with the Video panel.

##### Current Time Indicator

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393f_working_with_video_6_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4393f_working_with_video_6_modal.png)

Current Time Indicator (the purple flag) highlights the current position of the screen recording video on the trace timeline. It is like a vertical ruler that enables you to see how all the threads and slices the current time indicator touches are associated with the video frames shown on the video panel.

‍

Previewer

‍

Hover the top part of the global timeline and you will see the Current Time Indicator Previewer (white flag) appears. Move the previewer along the timeline and you can preview the video on the video panel.

‍

If you click while you're in preview mode - the current time indicator (purple flag) will move to the clicked position. If you move your cursor out of the global timeline, the video preview in the video panel changes to the current-time indicator position.

‍

Important Tips

-   You can only set current time indicators within the focus area limits.

##### Play/ Pause Video

-   Open the Video panel.
-   Press 'play' button at the bottom of the video.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43944_working_with_video_play_7.png)

-   Screen recording and the current time indicator on the main timeline play in a loop within the limits of the focus area.
-   Press 'pause' button at the bottom of the video to pause both the video and current time indicator.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43945_working_with_video_pause_8.png)

##### Loop Video

To make the video repeat continuously

-   For the video to loop from beginning to the end of the video - press

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43942_working_with_video_loop_btn_9.png)

-   For the video to loop within the focus area - press the same button that has now turned blue.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb43943_working_with_video_loop_btn_blue_10.png)

-   To turn the loop feature off - press the button again.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb4394d_working_with_video_loop_same_btn_blue_12.png)

#### Use Search

1. Search for any framework and function using the search box at the bottom right

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c4_use_search_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c4_use_search_modal.png)

2. All related instances should be immediately highlighted (while all the other unrelated functions should be dimmed).

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c5_use_search_1_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c5_use_search_1_modal.png)

3. Use arrows inside the search box to navigate among the search results

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c6_use_search_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c6_use_search_2_modal.png)

4. Press Esc or click "x" to exist search

#### Measure Time

To understand the duration of one function to another, you can use our measurement tool by holding shift + click.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438c7_measure_time.png)

#### Threads

Smallest executable task of the system. PS multi-threaded code profiling tool highlights critical functions and frameworks that impact user experience, revealing the root cause of problems.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f6_threads_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f6_threads_modal.png)

#### Pin Threads

Click the star to the right of a thread name to pin the thread to the top of the window for easy comparison and reference.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f7_pin_threads_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f7_pin_threads_modal.png)

#### Deprioritize Threads

Click the downward button to the left of a thread to pin the thread at the bottom of the window if you find that particular thread not as informative.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f8_deprioritize_threads_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438f8_deprioritize_threads_modal.png)

#### Place a flag

We recommend placing flags at the beginning and the end of a [flow](https://www.productscience.ai/documentation?doc=dictionary&sub=user-flow). You also get to choose colors of placed flags, which is helpful when you need to keep track of different information.

‍

1. Hover over the timeline, and you'll see a gray flag.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b9_place_a_flag_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438b9_place_a_flag_modal.png)

2. Click on the timeline to place the flag.

3. Our tool will randomly pick a color for your flag, which you can manually edit on the right-hand side of the screen. This is also where you can add labels to your flag.

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ba_place_a_flag_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ba_place_a_flag_2_modal.png)

Pro tip: You can also use the label field for quick notes. Simply click on the "label", press shift + enter and start typing. That way, the notes you typed won't show in the timeline, but you can use the notes for future reference.

#### Delete a Flag

When a flag is no longer relevant, you can remove it by:

‍

1. Clicking on the flag

2. Clicking on the "trash can" button when the flag details menu is shown on the right; or pressing "Del" on your keyboard.

![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438bb_delete_a_flag_icon.png)

[![](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ba_place_a_flag_2_modal.png)](https://assets-global.website-files.com/64be9ec9522055d42cb435e3/64be9ec9522055d42cb438ba_place_a_flag_2_modal.png)

