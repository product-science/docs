# Integration of CodeTuner for Cloud

The following instructions describe the integration process for CodeTuner for Cloud with your backend application.


## Architecture 
CodeTuner for Cloud is an agent that connects to your working application, 
providing low-overhead runtime instrumentation to track the cost of interactions with the server. 
The agent sends data to the Control Panel, which stores and processes the data.

The Control Panel, a part of CodeTuner, stores data from agents, processes it, and manages the agent's configuration. 
The data is available for analysis in the CodeTuner UI.


!!! info
    By default, CodeTuner and the Control Panel are hosted on Product Science servers. 
    If your company's security rules do not allow sending data outside of the private network, 
    CodeTuner and the Control Panel are available for on-premises distribution.  
    Please contact the Product Science Team for more details.


## Running Your Application

Run your application as usual. 
The agent will be attached to the already running application. 
Make sure to save the process ID to attach the agent.



## Attach Agent to the app's process

The Product Science Team will provide you with the Control Panel URL and a security token for communication between the agent and the Control Panel.

When attaching the agent, you need to configure three parameters:

1. `PS_CONTROL_PANEL_URL` - - The URL for the Control Panel, provided by Product Science.

2. `PS_AGENT_APPLICATION_API_KEY` - The security token, provided by Product Science.

3. `PS_AGENT_APPLICATION_NAME` - The name of your application.


Then, run the JAR file `code-tuner-agent.jar` with the following command:

```bash
java -jar code-tuner-agent.jar \
    --pid <PROCESS_ID> \
    --control-panel-url <PS_CONTROL_PANEL_URL> \
    --token <PS_AGENT_APPLICATION_API_KEY> \
    --app-name <PS_AGENT_APPLICATION_NAME>

```

If you need to analyze several instances, the agent should be attached to all of them. 
The same URL, application name, and token can be used for each instance.

