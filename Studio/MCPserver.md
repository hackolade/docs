# MCP server

For most AI assistant applications, Instructions for configuring the MCP server are documented in the Hackolade Model Hub application. Users can access these instructions by opening the hamburger menu ☰ , then clicking on *Connect AI assistants with MCP*

&nbsp;

Administrators are still required to perform some configuration when authentication is enabled. There is one exception: Microsoft 365 Copilot's configuration requires a deeper configuration, described below.

&nbsp;

## Authentication configuration

> [!NOTE]
> For the Standalone version, please ignore this section and go directly to the the AI Assistant integration section below.

&nbsp;

The same authentication configured to access the Model Hub application can be used to log users in to the MCP server.

&nbsp;

To achieve this, a new redirect URL needs to be added to the configured authentication provider. The URL to add depends on the AI assistant application you're targeting.

&nbsp;

The following is a list of applications with their redirect URL:

&nbsp;

<table style="width:75%">
<colgroup><col style="width:17%"><col style="width:28%"><col style="width:55%"></colgroup>
<thead>
<tr>
<th>Assistant</th>
<th>Redirect URL</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr>
<td>Claude Desktop</td>
<td>https://claude.ai/api/mcp/auth\_callback</td>
<td></td>
</tr>
<tr>
<td>Cursor</td>
<td>cursor://anysphere.cursor-mcp/oauth/callback</td>
<td></td>
</tr>
<tr>
<td>VS Code</td>
<td>http://127.0.0.1</td>
<td>VSCode starts a server on a random port on the host machine to perform the login.</td>
</tr>
<tr>
<td>Copilot Studio</td>
<td>https://\&lt;model-hub-domain-name&gt;/api/v1/mcp</td>
<td>see infos below</td>
</tr>
</tbody>
</table>

&nbsp;

> [!NOTE]
> When configuring these redirect URIs in Azure Entra ID, make sure to add them for the **Mobile and desktop applications** platform

&nbsp;

## AI Assistant integration

Besides the Model Hub functionality described in [this page](ModelHubuserinterface.md),Model Hub provides the ability to connect an AI assistant to your library of data model files via an embedded MCP (Model Context Protocol) server.

&nbsp;

> [!NOTE]
> Each AI assistant chat client uses a different architecture. With the production version of Model Hub, we can easily integrate through APIs. But with the Standalone personal client which runs locally in Electron the integration does not work with all the clients. In particular the test will not work with OpenAI ChatGPT or with Copilot (except is you use Copilot for VS Code, cfr below.)

&nbsp;

To get the instructions tailored to the GenAI chat client of your choice, click on the option *Connect AI assistants with MCP* from the hamburger menu.

&nbsp;

![Hub standalone menu](<lib/Hub standalone menu.png>)

&nbsp;

Then select the appropriate AI assistant. With Cursor and Copilot for VS Code, you just need to click the button and the configuration will be applied. With Claude, you will need to follow instructions and copy/paste the configuration.

&nbsp;

![Hub standalone connect to Claude dialog](<lib/Hub standalone connect to Claude dialog.png>)

&nbsp;

Each AI assistant client has a different way of setting up an MCP server. And you might already have some MCP servers defined.

&nbsp;

Follow the on-screen instructions.

&nbsp;

### Claude

In the Claude chat or code client, go to Settings, then Developer, and click the Edit Config button:

&nbsp;

![Hub standalone Claude create MCP server](<lib/Hub standalone Claude create MCP server.png>)

&nbsp;

This will open up your OS Explorer/Finder in the correct location. You must edit the file claude_desktop_config.json and insert the appropriate lines copied from the Model Hub dialog above. Make sure to not overwrite or corrupt existing configuration. Make sure that the config is proper JSON.

&nbsp;

![Hub standalone Claude MCP server config](<lib/Hub standalone Claude MCP server config.png>)

&nbsp;

After saving your edited config file, make sure that the Hackolade Model Hub is running so the MCP server is accessible

&nbsp;

Make sure to close Claude and restart it. On Windows, it often happens that closing the Claude client does not actually stop all processes. You may need to go to the Windows Tast Manager and end the Claude task.

&nbsp;

Unfortunately, a bug in Claude give a false error:

&nbsp;

![Hub standalone Claude MCP false error](<lib/Hub standalone Claude MCP false error.png>)

&nbsp;

You may ignore it and close the message.

&nbsp;

![Hub standalone Claude Developer settings MCP](<lib/Hub standalone Claude Developer settings MCP.png>)

&nbsp;

However, if you get these 3 messages, it means that the Model Hub has not been started and hence the MCP server is not accessible...

&nbsp;

![Hub standalone Claude MCP not reachable error](<lib/Hub standalone Claude MCP not reachable error.png>)

&nbsp;

### Copilot in VS Code

Copilot is not a model provider. It is a client product (a coding assistant, or Microsoft's assistant/agent ecosystem) that *consumes* models from those providers. Microsoft 365 Copilot itself can use models from OAzure OpenAI, OpenAI, and others.

&nbsp;

> [!WARNING]
> The Copilot chat client is incompatible with our Model Hub standalone trial MCP server. It does however work just fine with the production version of Model Hub. To test with Copilot, you must use it inside VS Code.

&nbsp;

**Prerequisite:** you must have VS Code installed running on your machine, and the Model Hub must be running.

&nbsp;

Click on the button Add to VS Code:

&nbsp;

![Hub standalone connect to Copilot dialog](<lib/Hub standalone connect to Copilot dialog.png>)

&nbsp;

Clicking the button will stgart VS Code and bring you to this screen where you must click the Install button:

&nbsp;

![Hub Copilot MCP server installation](<lib/Hub Copilot MCP server installation.png>)

&nbsp;

Once the MCP Server connection is installed, you can check that it is running by pressing Ctrl + Shift + P, then Run **`MCP: List Servers`** and make sure that the Hackolade-Hub server is running

&nbsp;

![Hub Copilot MCP server running](<lib/Hub Copilot MCP server running.png>)

&nbsp;

If you don't already have a chat pane on the right press Ctrl + Alt + I\
![Hub Copilot MCP server chat](<lib/Hub Copilot MCP server chat.png>)

&nbsp;

The first time you run a chat with the Model Hub MCP server, you will be asked for permission:\
![Hub Copilot MCP server permissions](<lib/Hub Copilot MCP server permissions.png>)

&nbsp;

### Microsoft 365 Copilot

To configure the MCP server to Copilot, you need to be able to create agents in [Copilot Studio](<https://copilotstudio.microsoft.com/> "target=\"_blank\"").

&nbsp;

Follow these steps to complete the configuration of the MCP server

- Open on the *Agents* menu, then click on *Create blank agent*
- Give the agent a name like *Hackolade Model Hub agent*
- Go to tools, then click on *+ Add a tool*
- In the modal that opens, select *Add new MCP*
- Fill the form
  - Server name: *hackolade-model-hub*
  - Server description: Use the MCP tools provided by the Hackolade model Hub application
  - Server URL: *https://\\\<model-hub-domain-name>/api/v1/mcp*
  - Authentication: Select *OAuth 2.0* then *Dynamic discovery* as a type
  - Click on *Create*

&nbsp;

The form should look like the following

&nbsp;

## Discuss with your Model Hub

You are now ready to have a conversation with your library of models.

&nbsp;

Here are some examples to inspire you. Possibilities are endles...

&nbsp;

```text
Using the Hackolade Model Hub MCP server, list available models

Give me an explanatory overview in words of model xyz

Build a SQL query to list customers and thei contact info
```

&nbsp;

etc.
