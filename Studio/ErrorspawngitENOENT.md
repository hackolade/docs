---
description: Fix the "spawn git ENOENT" error in Hackolade Studio Workgroup Edition when Git or the command prompt is unavailable.
seoTitle: "Error: spawn git ENOENT"
---
# Error: spawn git ENOENT

One of the [pre-requisites](Pre-requisites.md) to leverage the full user experience of the Workgroup Edition is to be able to use the Git executable installed on your machine.

The message "errorMsg": "spawn git ENOENT" generally occurs because Windows Group Policies are set to prevent access to either the Command Prompt, or PowerShell, or both. Such access is required for the application to execute OS commands such as running Git binary commands.

To confirm that your IT department did indeed disable the Command Prompt, type *cmd* in the search box of the Windows taskbar. If you get the message "*The command prompt has been disabled by your Administrator*" you should request to have this access enabled.

To confirm that your IT department did indeed disable the Command Prompt, type *powershell* in the search box of the Windows taskbar. If you get the message "*The application has been disabled by your Administrator*" or a similar message, then you should request to have this access enabled.

Without them, it is impossible to operate the Git-related features of Hackolade Studio.

Follow [these instructions](<https://www.tweakandtrick.com/2013/08/enable-command-prompt.html> "target=\"_blank\"") to enable the Command Prompt.
