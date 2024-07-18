# Integration for JVM based app

The JVM Agent allows both dynamic attaching to an already running JVM application and 
starting the application with the Agent attached.

## Attaching the Agent to a Running JVM Application

Attaching the Agent is described on the [integration](/cloudcost/integration/integration.md) page. 
Run your application as usual, then attach the CodeTuner Agent using the following command:

```bash
java -jar code-tuner-agent.jar \
    --pid <PROCESS_ID> \
    --control-panel-url <PS_CONTROL_PANEL_URL> \
    --token <PS_AGENT_APPLICATION_API_KEY> \
    --app-name <PS_AGENT_APPLICATION_NAME>
```

## Running the Application with the Agent Attached

To attach the agent at startup, follow these steps:

#### 1. Set environment variables

1. `PS_CONTROL_PANEL_URL` - - The URL for the Control Panel, provided by Product Science.

2. `PS_AGENT_APPLICATION_API_KEY` - The security token, provided by Product Science.

3. `PS_AGENT_APPLICATION_NAME` - The name of your application.

#### 2. Modify command to run the app

Typically, you run the application with a command like this:

```bash
java -jar myapp.jar
```

To attach CodeTuner Agent command should be modified to:
```bash
java \
    -javaagent:code-tuner-agent.jar
    -jar myapp.jar
```

If you need to analyze several instances, the agent should be attached to all of them. 
The same URL, application name, and token can be used for each instance.
