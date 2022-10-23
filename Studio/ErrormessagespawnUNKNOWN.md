# Error message: spawn UNKNOWN

The message&nbsp; "errorMsg": "spawn UNKNOWN" generally occurs because Windows Group Policies are set to prevent access to the Command Prompt, while such access is required for the application to execute OS commands such as fetching the processor UUID or running Git binary commands.

&nbsp;

To confirm that your IT department did indeed disable the Command Prompt, type *cmd* in the search box of the Windows taskbar.&nbsp; If you get the message "*The command prompt has been disabled by your Administrator*" you should request to have this access enabled.&nbsp; Without it, it is impossible to validate the license key for, or to operate the Hackolade Studio software.

&nbsp;

Follow [these instructions](<https://www.tweakandtrick.com/2013/08/enable-command-prompt.html> "target=\"\_blank\"") to enable the Command Prompt.
