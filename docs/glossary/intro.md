Introduction and General Terms
----------

**Welcome to PS Tool Glossary!**

At Product Science, our mission is to make mobile performance engineering
intuitive and accessible to developers of all levels through the advancement
of performance analysis and tracing techniques. 
PS Tool is a clear reflection of this commitment, 
designed to empower developers in efficiently identifying
and resolving performance bottlenecks within their applications.

**Purpose of This Glossary**

This glossary is here to support your understanding 
and use of PS Tool by providing clear explanations of terms,
concepts, and components essential to performance engineering.

It is crafted to:

1. **Clarify**: Provide clear explanations of both broad mobile 
performance engineering terms, as well as any specific terminology
used within PS Tool.
2. **Aid Navigation**: Serve as a comprehensive reference guide on how 
to find specific features within PS Tool and understand their purpose,
ensuring you have the necessary knowledge to streamline your analysis process.

### General Terms in Mobile Performance Engineering

Here are the basics you need to know if you're new to performance 
or tracing to get started with PS Tool. 
**[OPTIONAL - can combine both PS blogs and external resources]** Obviously, 
there's much more to performance engineering than this list provides - 
we've left some helpful resources at the end of this page in case you want to dive deeper.


#### Performance and Related Optimization Techniques

- **Mobile Performance**:
How fast and smooth your app runs on a device. 
Covers everything from startup times, memory usage, data consumption, to battery impact.

- **Performance Metrics**: 
The key figures that tell you how your app is performing, 
including frame rate, load time, memory usage, CPU load, and network times.

- **Tracing**: 
A method of capturing and recording specific events or actions within 
an application over a period. 
It allows developers to analyze these events to understand the behavior 
and performance of their application in detail.

- **Profiling**: 
Profiling is a technique for capturing an application's behavior, 
continuously monitoring various metrics and selectively sampling data. 
This approach captures only a portion of the data, focusing on those 
statistically most representative of the application's performance, 
thus providing insights into resource usage trends and optimization opportunities.

- **Profiling vs. Tracing**:
While profiling offers a broad view of an application's resource 
utilization over time, tracing provides a focused narrative on why 
those resources are used, clarifying the sequence of events leading 
to performance issues. 
Profiling aggregates data to identify general trends, whereas tracing 
is indispensable for diagnosing specific bottlenecks and understanding 
the detailed context of performance impacts.

- **Instrumentation**:
TBD

- **Critical Path**:
TBD

#### Front-End and Back-End Optimization 

- **Network Performance**: 
Critical in mobile apps, where data exchange with a server significantly
impacts user experience. It involves optimizing app interactions with the
network to improve data retrieval times and reduce latency.

- **Front-End Performance**: 
Pertains to the optimization of the mobile app's user interface and experience. 
This includes reducing render times, optimizing animations and transitions, and 
ensuring smooth scrolling and interaction. 
Techniques such as lazy loading, efficient asset management, and minimizing 
re-renders are key to maintaining high front-end performance, directly affecting 
user perception and engagement.

- **Front-End vs Back-End Optimization**:
It's a common assumption that improving back-end processes is the key 
to reducing user wait times, particularly since much of these waits 
are tied to network response. 
However, significant opportunities for enhancing app speed 
actually lie within the front-end domain. 
Effective front-end optimization involves parallelizing processes wherever possible — 
such as executing independent network requests in parallel rather than sequentially — 
and optimizing UI elements (like animations and transitions) to occupy the user during 
network calls, thereby masking delay. 
These strategies ensure that the front-end does not add to the wait time 
but rather enhances the user experience, 
leveraging the existing back-end and network response times more effectively.

#### App Components

- **User Flow**: 
Refers to the sequence of steps a user takes within an app to complete a specific task, 
such as making a purchase, signing up for an account, or accessing content. 
Understanding and optimizing user flows is crucial for enhancing the user experience, 
ensuring that tasks can be completed efficiently and intuitively. At Product Science, 
to achieve maximal clarity during the analysis, we recommend, 
to focus on a single user's action followed by app's reaction.

- **App Start**: 
The process of launching an application, which can vary in performance impact 
based on the state of the app prior to launch. 
There are several types of app starts, including:

  - **Cold Start**: Occurs when an app starts from scratch, with no prior process existing in memory. This is the most resource-intensive type of start, as it involves loading the app from storage, initializing it, and setting up the initial state.
  - **Warm Start**: Happens when the app's process is still in memory from a previous session, making the start-up time quicker than a cold start. The app may only need to refresh its user interface and update its state rather than initialize everything from scratch.
  - **Hot Start**: Refers to an app becoming active again after being paused or stopped, with all resources already loaded in memory. This is the quickest type of start, often involving merely bringing the app's user interface to the foreground without needing to reload the app's state or resources.

### More resources on performance optimization (optional, may delete later)

- [Performance Debugging - MAD Skills](https://www.youtube.com/playlist?list=PLWz5rJ2EKKc-xjSI-rWn9SViXivBhQUnp)  - YouTube Playlist by Android Developers
- [Code Instrumentation for Performance Optimization](https://www.productscience.ai/webinars/3-trace-tools-for-addressing-performance-issues-on-android-current-inadequacies-and-new-solutions-gdg-meetup) by Gleb Morgachev at Google Developer Group Meetup
- react native post + add something on iOS?

### Start working with PS Tool

To instrument and trace your own app, follow these instructions for [Android](../integration/android/gradle.md) and [iOS](../integration/ios/xcode.md).
To learn more about PS Tool components and capabilities, continue to the next section of this [glossary](ps-tool-components.md).