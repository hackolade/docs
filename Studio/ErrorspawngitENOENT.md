# Error: spawn git ENOENT

One of the [pre-requisites](<Pre-requisites.md>) to leverage the full user experience of the Workgroup Edition is to be able to use the Git executable installed on your machine. &nbsp;

&nbsp;

The message&nbsp; "errorMsg": "spawn git ENOENT" generally occurs because Windows Group Policies are set to prevent access to either the Command Prompt, or PowerShell, or both. Such access is required for the application to execute OS commands such as running Git binary commands.

&nbsp;

To confirm that your IT department did indeed disable the Command Prompt, type *cmd* in the search box of the Windows taskbar.&nbsp; If you get the message "*The command prompt has been disabled by your Administrator*" you should request to have this access enabled. &nbsp;

&nbsp;

To confirm that your IT department did indeed disable the Command Prompt, type *powershell* in the search box of the Windows taskbar.&nbsp; If you get the message "*The application has been disabled by your Administrator*" or a similar message, then you should request to have this access enabled. &nbsp;

&nbsp;

Without them, it is impossible to operate the Git-related features of Hackolade Studio.

&nbsp;

Follow [these instructions](<https://www.tweakandtrick.com/2013/08/enable-command-prompt.html> "target=\"\_blank\"") to enable the Command Prompt.

