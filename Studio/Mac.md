# Mac

## Standard installation

The application is shipped as a signed (with Hackolade's parent company IntegrIT NV Developer ID) .pkg file with an installation wizard automatically placing the app in the proper folder and displaying the License Agreement and Release Notes.&nbsp; After downloading the application from our [download page](<https://hackolade.com/download.html> "target=\"\_blank\""), double-click on the downloaded .pkg file and the wizard will start.&nbsp; You will be prompted for your Mac username and password.

&nbsp;

Starting with the release of macOS 10.15 Catalina, Apple has introduced a new security feature that ensures that 3rd-party applications are manually granted access to the user's file.&nbsp; Hackolade stores settings and logs in your Documents folder, and it cannot operate without it.&nbsp; So, if prompted with this dialog, you must click OK. &nbsp;

![Mac - access to Documents folder](<lib/Mac Catalina - access to Documents folder.png>)

&nbsp;

You may still manage this grant if needed in Security \& Privacy:

![Mac Security Privacy](<lib/Mac Catalina Security Privacy.png>)

&nbsp;

&nbsp;

## The "Git" command requires the command line developer tools

If you don't have XCode installed on your machine, it is possible that you will be presented with this message:

![Mac Git command line developer tools install](<lib/Mac Git command line developer tools install.png>)

&nbsp;

You should install this these tools, then restart Hackolade Studio.

&nbsp;

## To install the application without admin rights

In a corporate environment if you don't have the admin password to perform installation, you should contact your IT department.&nbsp; They can remotely access your computer and install the software for you.&nbsp; You should comply with the IT policy on non-approved software.

![Mac install - admin password](<lib/Mac install - admin password.png>)&nbsp; ![Mac install - failed](<lib/Mac install - failed.png>)

&nbsp;

Nevertheless, it is possible to bypass this restriction and install Hackolade without admin rights.&nbsp; You must be aware that the installation of the software is a tacit acceptance of our [Terms and Conditions and End-User License Agreement](<https://hackolade.com/eulas.html> "target=\"\_blank\""), whether you use the installation wizard or follow the instructions below.

&nbsp;

Manual installation steps:

&#49;. download the application from our [download page](<https://hackolade.com/download.html> "target=\"\_blank\"")

&nbsp;

&#50;. copy the downloaded file **Hackolade-mac-setup-signed.pkg** to the Desktop

&nbsp;

&#51;. You may want to minimize and hide all windows by pressing Command+Option+H+M

![Mac install - step 2](<lib/Mac install - step 2.png>)

&nbsp;

&#52;. Open the search bar by pressing Command+Spacebar, search for terminal and press enter

![Mac install - step 4](<lib/Mac install - step 4.png>)

&nbsp;

&#53;. Type: **pkgutil --expand** , then drag-and-drop the .pkg file in the terminal window, followed by the folder path where you want to install the software, for example /Users/\<homeFolderName\>/HackoladeTMP and press enter to extract the package into the destination folder

![Mac install - step 5](<lib/Mac install - step 5.png>)

&nbsp;

&#54;. Open the destination temp folder HackoladeTMP

&nbsp;

&#55;. You should see a package file Hackolade.pkg&nbsp; Press Ctrl+Right-Click on the the Hackolade.pkg file and choose Show Content

![Mac install - step 7](<lib/Mac install - step 7.png>)

&nbsp;

&#56;. You will see a Payload file

![Mac install - step 8](<lib/Mac install - step 8.png>)

&nbsp;

&#57;. In the Terminal window, type the command: **tar -xvf** , then drag-and-drop the Payload file and add the -C argument (with an uppercase C) plus the final destination folder and press enter

![Mac install - step 9](<lib/Mac install - step 9.png>)

&nbsp;

&#49;0.&nbsp; You should see a list of filenames scroll through the window:

![Mac install - step 10](<lib/Mac install - step 10.png>)

&nbsp;

&#49;1.&nbsp; When the process is finished, if you access the destination folder, you should see the installed app:

![Mac install - step 11](<lib/Mac install - step 11.png>)

&nbsp;

Double-click on the Hackolade.app icon to start the application.

&nbsp;

## Silent installation

**Important license note:** by installing or upgrading, you accept the [license agreement](<Licenseagreement.md>) for the application, even if the silent installation does not prompt you.

&nbsp;

The installer can be invoked in a Terminal window after download of the application pkg file in the Downloads folder.

&nbsp;

On Apple silicon arm64:

> sudo installer -target / -pkg $HOME/Downloads/Hackolade-macARM64-setup-signed.pkg

&nbsp;

On Intel 64-bit:

> sudo installer -target / -pkg $HOME/Downloads/Hackolade-mac-setup-signed.pkg

&nbsp;

&nbsp;

## Homebrew

**Important license note:** by installing or upgrading, you accept the [license agreement](<Licenseagreement.md>) for the application, even if the silent installation does not prompt you.

&nbsp;

Homebrew is a package manager for for MacOS and Linux.&nbsp; A package for Hackolade Studio has been [published](<https://formulae.brew.sh/cask/hackolade> "target=\"\_blank\"") and is maintained by a kind member of the community.&nbsp; Many thanks to him.

&nbsp;

If brew is not installed yet, please do so by following instructions in [this page](<https://brew.sh/> "target=\"\_blank\"").&nbsp; Note that brew requires the installation of XCode Command Line Tools. &nbsp;

&nbsp;

The install command is&nbsp;

&nbsp;

> brew install --cask hackolade

&nbsp;

See this page for [more details](<https://formulae.brew.sh/cask/hackolade> "target=\"\_blank\"").

