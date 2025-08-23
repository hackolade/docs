# Download additional target plugins

The latest version of each plugin is always available for download from the Plugin Manager?&nbsp; Just go to Help \>&nbsp; Plugin Manager

&nbsp;

![Plugin Manager menu new](<lib/Plugin Manager menu new.png>)

&nbsp;

&nbsp;

You may choose which plugin to install on your computer.

![Plugin - manager available custom props](<lib/Plugin - manager available custom props.png>)

&nbsp;

This will result in the plugin appearing in the Installed tab of the plugin manager.

![Plugin - Manager installed custom props](<lib/Plugin - Manager installed custom props.png>)

&nbsp;

&nbsp;

&nbsp;

## Are you experiencing issues with plugin download?

Do you have your network proxy set correctly?&nbsp; See more details [here](<Networkproxy.md>).

&nbsp;

Does&nbsp; your organization prevent access to GitHub?&nbsp; You may need to have [https://github.com/hackolade](<https://github.com/hackolade> "target=\"\_blank\"") whitelisted.

&nbsp;

There is an alternative: you may download the plugin from [our GitHub repo](<https://github.com/hackolade> "target=\"\_blank\""), then go to the plugin of your choice, and click on link in the About section on the right-hand side of the page:

&nbsp;

&nbsp;

&nbsp;

![GitHub Plugin Download](<lib/GitHub Plugin Download.png>)

&nbsp;

This link leads you to a page with the latest release, where you can click on the link **\<plugin\>-\<version\>.zip** link to download the zip file:

&nbsp;

&nbsp;

![GitHub Plugin Download step 2](<lib/GitHub Plugin Download step 2.png>)

&nbsp;

&nbsp;

​

&nbsp;

Then to install the plugin, go to Help \> Plugin Manager and click the button Install from Zip.

&nbsp;

![Plugin Manager - Install from zip](<lib/Plugin Manager - Install from zip.png>)

&nbsp;

&nbsp;

## You get the message "Hackolade Studio doesn't have enough rights to install a plugin..."

While you, as a user may have the rights to the folder where plugins are installed, it is possible that some environments limit the rights of our application.&nbsp; It can be a virtualization or sandboxing setup or most likely an anti-virus software. &nbsp;

![Plugins - Virus Threat Protection error](<lib/Plugins - Virus Threat Protection error.png>)

&nbsp;

If your anti-virus is Windows Defender, you, or your IT department, can create an exclusion in Windows Defender. Follow these steps:

**Open Windows Security:**

\- Press the **Windows key + I** to open Settings.

\- Select "Privacy \& Security."

\- Click on "Windows Security" in the left sidebar.

&nbsp;

**Access Virus \& Threat Protection Settings:**

\- In the Windows Security window, click on "Virus \& threat protection."

![Image](<lib/Plugins - Virus Threat Protection.png>)

&nbsp;

&nbsp;

**Manage Settings:**

\- Under the "Virus \& threat protection settings" section, click on "Manage settings."

&nbsp;

![Plugins Windows Defender Manage settings](<lib/Plugins Windows Defender Manage settings.png>)

&nbsp;

&nbsp;

**Add or Remove Exclusions:**

\- Scroll down to the bottom, to the "Exclusions" section.

\- Click on "Add or remove exclusions."

&nbsp;

![Plugins Windows Defender add exclusion](<lib/Plugins Windows Defender add exclusion.png>)

&nbsp;

**Add a Folder Exclusion:**

\- Click on "Add an exclusion."

\- Choose "Folder" from the drop-down menu.

&nbsp;

If you get the message that you don't have the permission to create this exclusion, you will need for your IT Security team to access your machine and allow this operation.&nbsp; Or ask them to perform it for you.

&nbsp;

![Image](<lib/Plugins - Windows Defender no permission.png>)

&nbsp;

&nbsp;

**Specify the Folder Path:**

\- Navigate to the folder **C:\\Users\\%username%\\.hackolade** and select it.

![Plugins Windows Defender add folder path](<lib/Plugins Windows Defender add folder path.png>)

&nbsp;

**Save Changes:**

\- Save your changes.

This exclusion tells Windows Defender not to scan or interfere with files and processes within the specified folder. Hackolade Studio should now have the necessary WRITE or EXECUTE permissions in the specified directory.\
\
Remember to replace **%username%** in the folder path with the actual username. After making these changes, the application should be able to operate in the specified directory without being blocked by Windows Defender.

&nbsp;

## Plugin Manager options for an installed plugin

In the Installed tab of the Plugin Manager, you may see multiple buttons:

![Plugin Manager Installed tab - buttons](<lib/Plugin Manager Installed tab - buttons.png>)

&nbsp;

**Remove:** this button deletes the plugin from your machine

**Disable:** this button keeps the plugin on your machine but turns it OFF, so it no longer appears in the targets available to create models.

**Migrate:**  this has to do with customizations you may have made to this plugin.  The whole thing is documented in [this page](<Migrationtoenhancedcustompropert.md>). If you don't have customizations dating prior to v3.6.2, you may probably ignore.  But it is safer to first migrate just in case, then update to the latest version of the plugin.

&nbsp;

&nbsp;

## Share downloaded plugins with team members

While this step is not required, and may not be desirable if some teams work with different targets, it is possible, in some organizations, to centralization the installation and update of plugins. In such case, one user would download and install the plugin or plugin updates in their Git-enabled folder, then push the changes to the remote Git repository so other users could pull them on their local machine.

&nbsp;

In such scenario, there 2 options: the Git enabling of only the folder of the plugins, or (preferably) Git-enabling the folder that contains both the plugins and the custom properties.&nbsp; In the latter case, this would replace the process described [here](<https://hackolade.com/help/Userdefinedcustomproperties.html#Share%20customization%20with%20team%20members>).

&nbsp;

For the rest of the description below, we assume the latter scenario.&nbsp; In such case, the user clones locally in C:\\Users\\%username%\\.hackolade (on Mac in Users/$USER/.Hackolade)&nbsp; That way, all that teams members need to do is to pull regularly, and they will get your latest plugins and custom properties.

&nbsp;

For changes to take effect on each computer, it is required to exit Hackolade Studio and restart it.

&nbsp;

### One-time setup of the Git repository for the organization's custom properties

This step is required once per organization, to be executed by the Hackolade Studio superuser or maintainer.

&nbsp;

The process to git-enable your options folder may vary, depending on your OS and your repo provider.&nbsp; Here is an example using GitHub and Windows:

&nbsp;

&#49;) in Windows Explorer, go to C:\\Users\\%username%\\.hackolade and make sure that the folder is empty. &nbsp;

&#50;) if the folder C:\\Users\\%username%\\.hackolade is not empty, then cut the content and place it in a safe place

&#51;) in GitHub, create a new repository, for example called "hck\_plugins\_and\_custom\_props" and copy the Git URL, for example in our case "https://github.com/\<yourorg\>/hck\_plugins\_and\_custom\_props.git" (finishing in .git)

&#52;) in Hackolade Studio, go to the repository context (or the menu option "Repository \> Open Repository Context, or keyboard shortcut Ctrl + G)&nbsp;

&#53;) in the top bar, select the Source "URL", then paste the Git URL you had copied in step 3), then click the Clone button

&#54;) in the OS destination folder dialog, select the folder C:\\Users\\%username%\\.hackolade which must be an empty folder

&#55;) if you had in step 2) to put in a safe place previous content of the options folder, now is the time to copy it back to the C:\\Users\\%username%\\.hackolade folder

&#56;) commit and push to the central remote repository the changes of step 7) and any other changes to custom properties

&nbsp;

### One-time setup of each user's plugins and custom properties

When a new user installs the application, it should be part of the organizations documented process, right after license key validation, to clone locally the organization's custom properties repository.

&#49;) in Hackolade Studio, go to the repository context (or the menu option "Repository \> Open Repository Context, or keyboard shortcut Ctrl + G)&nbsp;

&#50;) in the top bar, select the Source "URL", then paste the Git URL you copied in step 3) , then click the Clone button

&#51;) in the OS destination folder dialog, select the folder C:\\Users\\%username%\\.hackolade\\ which must be an empty folder

&#52;) select or possibly clone locally the models repository

&nbsp;

### Share plugin or custom properties changes with Hackolade Studio users

When the superuser(s) or maintainer(s) downloads plugin updates, or develop, fine-tune and test new or adapted custom properties, it is useful to share them with the rest of the Hackolade Studio community of users in the organization.

&nbsp;

They should:

&#49;) using Hackolade Studio, select the custom props repository

&#50;) go to the Commit screen and click the Push button

&#51;) notify your community of Hackolade users to pull the changes from the remote repo of custom properties

&#52;) go back to your models repository

&nbsp;

Other users should simply:

&#49;) using Hackolade Studio, select the custom props repository

&#50;) go to the Pull screen and click the Pull button

&#51;) close and restart Hackolade Studio

&#52;) go back to your models repository

&nbsp;

