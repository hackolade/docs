# MCP server

&nbsp;

For most AI assistant applications, Instructions for configuring the MCP server are documented in the Hackolade Model Hub application.&nbsp; Users can access these instructions by opening the hamburger menu ☰ , then clicking on *Connect AI assistants with MCP*

&nbsp;

Administrators are still required to perform some configuration when authentication is enabled. There is one exception: Microsoft 365 Copilot's configuration requires a deeper configuration, described below.

&nbsp;

## Authentication configuration

**Note:** for the Standalone version, please ignore this section and go directly to the the AI Assistant integration section below.

&nbsp;

The same authentication configured to access the Model Hub application can be used to log users in to the MCP server.

&nbsp;

To achieve this, a new redirect URL needs to be added to the configured authentication provider. The URL to add depends on the AI assistant application you're targeting.

&nbsp;

The following is a list of applications with their redirect URL:

&nbsp;

| **Assistant** | **Redirect URL** | **Notes** |
| --- | --- | --- |
| Claude Desktop | https://claude.ai/api/mcp/auth\\\_callback |  |
| Cursor | cursor://anysphere.cursor-mcp/oauth/callback |  |
| VS Code | http://127.0.0.1 | VSCode starts a server on a random port on the host machine to perform the login. |
| Copilot Studio | https://\\\<model-hub-domain-name\>/api/v1/mcp | see infos below |


&nbsp;

**Note:** when configuring these redirect URIs in Azure Entra ID, make sure to add them for the **Mobile and desktop applications** platform

&nbsp;

&nbsp;

## AI Assistant integration

Besides the Model Hub functionality described in [this page](<ModelHubuserinterface.md>),Model Hub provides the ability to connect an AI assistant to your library of data model files via an embedded MCP (Model Context Protocol) server.

&nbsp;

**Note:** each AI assistant chat client uses a different architecture.&nbsp; With the production version of Model Hub, we can easily integrate through APIs.&nbsp; But with the Standalone personal client which runs locally in Electron the integration does not work with all the clients.&nbsp; In particular the test will not work with OpenAI ChatGPT or with Copilot (except is you use Copilot for VS Code, cfr below.)

&nbsp;

To get the instructions tailored to the GenAI chat client of your choice, click on the option *Connect AI assistants with MCP* from the hamburger menu.

&nbsp;

![Hub standalone menu](<lib/Hub standalone menu.png>)

&nbsp;

Then select the appropriate AI assistant.&nbsp; With Cursor and Copilot for VS Code, you just need to click the button and the configuration will be applied.&nbsp; With Claude, you will need to follow instructions and copy/paste the configuration.

&nbsp;

![Hub standalone connect to Claude dialog](<lib/Hub standalone connect to Claude dialog.png>)

&nbsp;

&nbsp;

&nbsp;

Each AI assistant client has a different way of setting up an MCP server.&nbsp; And you might already have some MCP servers defined.

&nbsp;

Follow the on-screen instructions.

&nbsp;

### Claude

In the Claude chat or code client, go to Settings, then Developer, and click the Edit Config button:

&nbsp;

![Hub standalone Claude create MCP server](<lib/Hub standalone Claude create MCP server.png>)

&nbsp;

This will open up your OS Explorer/Finder in the correct location.&nbsp; You must edit the file claude\_desktop\_config.json and insert the appropriate lines copied from the Model Hub dialog above.&nbsp; Make sure to not overwrite or corrupt existing configuration.&nbsp; Make sure that the config is proper JSON.

&nbsp;

![Hub standalone Claude MCP server config](<lib/Hub standalone Claude MCP server config.png>)

&nbsp;

&nbsp;

After saving your edited config file, make sure that the Hackolade Model Hub is running so the MCP server is accessible&nbsp;

&nbsp;

Make sure to close Claude and restart it.&nbsp; On Windows, it often happens that closing the Claude client does not actually stop all processes.&nbsp; You may need to go to the Windows Tast Manager and end the Claude task.

&nbsp;

Unfortunately, a bug in Claude give a false error:

&nbsp;

![Hub standalone Claude MCP false error](<lib/Hub standalone Claude MCP false error.png>)

&nbsp;

You may ignore it and close the message. &nbsp;

&nbsp;

![Hub standalone Claude Developer settings MCP](<lib/Hub standalone Claude Developer settings MCP.png>)

&nbsp;

&nbsp;

However, if you get these 3 messages, it means that the Model Hub has not been started and hence the MCP server is not accessible...

&nbsp;

&nbsp;

![Hub standalone Claude MCP not reachable error](<lib/Hub standalone Claude MCP not reachable error.png>)

&nbsp;

### Copilot in VS Code

**Warning:** the Copilot chat client is incompatible with our Model Hub standalone trial MCP server.&nbsp; It does however work just fine with the production version of Model Hub.&nbsp; To test with Copilot, you must use it inside VS Code.

&nbsp;

**Prerequisite:** you must have VS Code installed running on your machine, and the Model Hub must be running.

&nbsp;

Click on the button Add to VS Code:

&nbsp;

![Image](<lib/Hub standalone connect to Copilot dialog.png>)

&nbsp;

Clicking the button will stgart VS Code and bring you to this screen where you must click the Install button:

&nbsp;

![Hub Copilot MCP server installation](<lib/Hub Copilot MCP server installation.png>)

&nbsp;

Once the MCP Server connection is installed, you can check that it is running by pressing Ctrl + Shift + P, then Run **MCP: List Servers** and make sure that&nbsp; the Hackolade-Hub server is running

&nbsp;

![Hub Copilot MCP server running](<lib/Hub Copilot MCP server running.png>)

&nbsp;

&nbsp;

If you don't already have a chat pane on the right press Ctrl + Alt + I

![Hub Copilot MCP server chat](<lib/Hub Copilot MCP server chat.png>)

&nbsp;

&nbsp;

The first time you run a chat with the Model Hub MCP server, you will be asked for permission:

![Hub Copilot MCP server permissions](<lib/Hub Copilot MCP server permissions.png>)

&nbsp;

&nbsp;

&nbsp;

### Microsoft 365 Copilot

To configure the MCP server to Copilot, you need to be able to create agents in [Copilot Studio](<https://copilotstudio.microsoft.com/> "target=\"\_blank\"").

&nbsp;

Follow these steps to complete the configuration of the MCP server

&nbsp;

* Open on the *Agents* menu, then click on *Create blank agent*
* Give the agent a name like *Hackolade Model Hub agent*
* Go to tools, then click on *+ Add a tool*
* In the modal that opens, select *Add new MCP*
* Fill the form

  * Server name: *hackolade-model-hub*
  * Server description: Use the MCP tools provided by the Hackolade model HUB application
  * Server URL: *https://\\\<model-hub-domain-name\>/api/v1/mcp*
  * Authentication: Select *OAuth 2.0* then *Dynamic discovery* as a type
  * Click on *Create*

&nbsp;

The form should look like the following

&nbsp;

&nbsp;

## Discuss with your Model Hub

You are now ready to have a conversation with your library of models. &nbsp;

&nbsp;

Here are some examples to inspire you.&nbsp; Possibilities are endles...

&nbsp;

> Using the Hackolade Model Hub MCP server, list available models

&nbsp;

> Give me an explanatory overview in words of model xyz

&nbsp;

> Build a SQL query to list customers and thei contact info

&nbsp;

etc.

&nbsp;

