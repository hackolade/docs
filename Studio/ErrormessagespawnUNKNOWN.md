# Error message: spawn UNKNOWN

The message&nbsp; "errorMsg": "spawn UNKNOWN" generally occurs because Windows Group Policies are set to prevent access to either the Command Prompt, or PowerShell, or both. Such access is required for the application to execute OS commands such as fetching the processor UUID.

&nbsp;

![Spawn error message](<lib/Spawn error message.png>)

&nbsp;

or

&nbsp;

![Spawn license screen error](<lib/Spawn license screen error.png>)

&nbsp;

To confirm that your IT department did indeed disable the Command Prompt, type *cmd* in the search box of the Windows taskbar.&nbsp; If you get the message "*The command prompt has been disabled by your Administrator*" you should request to have this access enabled. &nbsp;

&nbsp;

To confirm that your IT department did indeed disable the Command Prompt, type *powershell* in the search box of the Windows taskbar.&nbsp; If you get the message "*The application has been disabled by your Administrator*" or a similar message, then you should request to have this access enabled. &nbsp;

&nbsp;

Without them, it is impossible to validate the license key for, or to operate the Hackolade Studio software.

&nbsp;

Follow [these instructions](<https://www.tweakandtrick.com/2013/08/enable-command-prompt.html> "target=\"\_blank\"") to enable the Command Prompt.

