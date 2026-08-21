# Standalone personal trial

The [Model Hub Playground](<https://hub.hackolade.com/> "target=\"\_blank\"") is ideal for a quick introduction to the platform’s capabilities, but it falls short when it comes to conducting a meaningful evaluation with your own data models.

The standalone personal trial changes that. With a lightweight executable running locally, you can import your own Hackolade Studio models into the Model Hub repository.&nbsp; It allows you to explore, validate, and experience the full power of Model Hub in the context of your real-world use cases.

**Warning:** as you would expect, this environment is designed strictly for evaluation and is not intended for production use. Because it runs locally on your machine, collaboration features are not available, and models cannot be accessed or opened in a browser.

&nbsp;

## Download and install the Model Hub

The latest version of the Model Hub standalone personal trial is downloaded here.

\- [Windows 64-bit (signed installer)](<https://hackolade.s3.eu-west-1.amazonaws.com/model-hub/standalone/current/Hackolade-Model-Hub-win64-setup-signed.exe> "target=\"\_blank\"")

\- [Mac Intel 64-bit (notarized installer)](<https://s3-eu-west-1.amazonaws.com/hackolade/model-hub/standalone/current/Hackolade-Model-Hub-macX64-setup-signed.pkg> "target=\"\_blank\"")

\- [Mac Apple arm64 (notarized installer)](<https://s3-eu-west-1.amazonaws.com/hackolade/model-hub/standalone/current/Hackolade-Model-Hub-macARM64-setup-signed.pkg> "target=\"\_blank\"")

\- [Linux 64-bit zip](<https://s3-eu-west-1.amazonaws.com/hackolade/model-hub/standalone/current/Hackolade-Model-Hub-linux-x64.zip> "target=\"\_blank\"") (SHA-256 checksum can be downloaded [here](<https://s3-eu-west-1.amazonaws.com/hackolade/model-hub/standalone/current/Hackolade-Model-Hub-linux-x64.SHASUM256.txt.asc> "target=\"\_blank\""))

&nbsp;

Run the downloaded installer which includes all the necessary components to run without requiring additional dependencies:&nbsp;

\- an embedded PGlite database

\- a NodeJS application server

\- the Hackolade Model Hub front-end and backend applications

\- an [MCP server](<https://en.wikipedia.org/wiki/Model\_Context\_Protocol> "target=\"\_blank\"") to interact from a GenAI client with the library of models imported from your Git repositories

&nbsp;

Once the application has started, you must enter a valid license key.&nbsp; If you don't have one, you can obtain one from support@hackolade.com

&nbsp;

![Hub standalone personal trial key validation](<lib/Hub standalone personal trial key validation.png>)

&nbsp;

&nbsp;

Once the license key has been validated, you're ready to use the application.

&nbsp;

![Hub standalone personal trial key validated](<lib/Hub standalone personal trial key validated.png>)

&nbsp;

&nbsp;

In the production deployment of the application, there is a setup to connect to one or more repositories via webhooks and APIs.&nbsp; But with the standalone personal trial here,&nbsp;

&nbsp;

To populate the standalone personal trial instance database with model requires to use the explorer buttons, either "Choose a folder" and/or "Choose a file", then select using the operating system dialog.&nbsp; It is perfectly acceptable to select, as a source, one or more folders of locally-clone repository/repositories.&nbsp; Depending on the number and size of the models, this process can take a few minutes.

&nbsp;

![Hub standalone personal trial home screen](<lib/Hub standalone personal trial home screen.png>)

&nbsp;

&nbsp;

Once the models have been ingested in the database, you are ready to use the application.&nbsp; You may want to consult [this page](<ModelHubuserinterface.md>) for further information.

&nbsp;

&nbsp;

## MCP server AI Assistant integration

Besides the Model Hub functionality described in [this page](<ModelHubuserinterface.md>), this standalone trial version of the Model Hub lifts the veil on many exciting upcoming AI-related capabilities.&nbsp; One has to do with the ability to connect an AI assistant to your library of model files via an embedded MCP (Model Context Protocol) server.

&nbsp;

Refer to this page for more information.

