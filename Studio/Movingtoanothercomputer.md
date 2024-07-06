# Moving to another computer

When moving to another machine requires some preparation.&nbsp; This page walks you through several important attention points.

&nbsp;

## Application

The latest version of the application can be fetched from our [Download page](<https://hackolade.com/download.html> "target=\"\_blank\"").&nbsp; If you need an older version, if can be found by setting the chosen application number in these link examples:

**\- Windows:** https://s3-eu-west-1.amazonaws.com/hackolade/previous/v6.11.9/Hackolade-win64-setup-signed.exe

**\- Mac Intel:** https://s3-eu-west-1.amazonaws.com/hackolade/previous/v6.11.9/Hackolade-mac-setup-signed.pkg

**\- Mac ARM:** https://s3-eu-west-1.amazonaws.com/hackolade/previous/v6.11.9/Hackolade-macARM64-setup-signed.pkg

**\- Linux:** https://s3-eu-west-1.amazonaws.com/hackolade/previous/v6.11.9/Hackolade-linux-x64.zip

&nbsp;

## Plugins

The latest version of each plugin is always available for download from the Plugin Manager, as described in [this page](<DownloadadditionalDBtargetplugin.md>).

&nbsp;

If you application version is not the latest version, it is possible that your plugin version is not the latest either (as some later plugin versions require a minimum core application version.)&nbsp; In that case, you may have to install the plugin from Zip file.&nbsp; You can find earlier releases of each plugin in the Releases section (on the right-hand side) of the GitHub page for each plugin.&nbsp; To determine the plugin version on your old computer, simply go to Help \> Plugin Manager \> Installed. &nbsp;

&nbsp;

## Custom properties

The location of the custom properties JSON configuration files depends on your environment:

\- If you use the desktop application on Windows, you can find the JSON files in C:\\Users\\%username%\\.hackolade\\options. You can edit those files in-place.

\- If you use the desktop application on MacOS, you can find the JSON files in /Users/$USER/.hackolade/options. You can edit those files in-place.

\- If you use the browser application, you can load the config from *Tools \> Options \> Custom Properties*

&nbsp;

In many organizations, custom properties are maintained by an administrator and stored in a Git repository.&nbsp; It is then simple to clone that repo into the location detailed above.&nbsp; Otherwise, you should copy this .hackolade/options folder from your old computer to the new one.

&nbsp;

## Data models

Ideally, your models are in a Git repository, on a shared drive, or in a folder synchronized with the cloud (OneDrive, Google Drive, iCloud, Dropbox, etc...) in which case changing to another client machine should not affect your data models.&nbsp; Make sure, when you get your new machine, to set things up so you again have access to your data models.&nbsp; Note that we strongly suggest to **avoid** combining your Git clone with a cloud-synchronized folder\!&nbsp; Do not clone your repo in a folder which synchronized with the cloud (OneDrive, Google Drive, iCloud, Dropbox, etc...)&nbsp; The sync mechanism may cause perverse performance effects and sometimes conflicts with the Git processes.

&nbsp;

If you store your models on your local hard drive, then you need to migrate them to the new machine, either through a backup, or manually.

&nbsp;

## Personal preferences and connection settings

To facilitate the migration of your parameters, Hackolade Studio provides a handy backup and restore capability.&nbsp; Just go to Tools \> Options \> General, and you will find the possibility to extract all your parameters and store them in a binary encrypted file.

&nbsp;

![Backup preferences parameters connections](<lib/Backup%20preferences%20parameters%20connections.png>)

&nbsp;

Then, you just need to move that file to your new machine and go through the restore process also in Tools \> Options \> General.

&nbsp;

## License key

The Hackolade Studio licensing terms for individual/dedicated license keys are "per seat" (aka [node-locked](<https://en.wikipedia.org/wiki/Node-locked\_licensing> "target=\"\_blank\""))&nbsp; As a result, your seat for the old computer must first be released before you can validate the license key on your new computer.&nbsp; This process is very simple and self-service.&nbsp; The steps are described in [this page](<Transferalicensetoanewcomputer.md>).

