# Pre-requisites

There are 2 pre-requisites for using the Workgroup Edition of Hackolade Studio:

* you or your organization must have purchased the Workgroup Edition, or the Workgroup upgrade option to the Professional Edition. This repository feature is not available in the Community, Personal or Professional Editions. If you don't have the Workgroup Edition yet, you may contact us at [sales@hackolade.com](<mailto:sales@hackolade.com?subject=Interested%20in%20Workgroup%20Edition>).
* you must have a Git client installed on your computer.&nbsp;

&nbsp;

Here are the steps to verify that your installation meets both criteria...

&nbsp;

In Hackolade Studio, **open the repository context**.

* choose Repository \> Open Repository Context in the top menu;
* use the keyboard shortcut Ctrl+G (Cmd+G on MacOS);
* switch to the repository context through the vertical Context Bar on the left;
* move up or down in the Context bar by using the shorcut Ctrl+Up/Down arrow (Cmd+Up/Down arrow on MacOS).

&nbsp;

If you do have the Workgroup Edition, then **look at the top bar while in the Repository Context**.&nbsp; If you don't see any error message in the top bar, then everything is fine: you already have a Git client and it is ready to be used by Hackolade Studio. If you do see an error message in the top bar, then there is a problem.&nbsp; Read on...

&nbsp;

![Image](<lib/Workgroup%20invalid%20git%20client.png>)

&nbsp;

## The Git executable is already present

If you already have a Git client installed, it should normally be available globally through the PATH environment variable.&nbsp; You can perform a diagnostic of your Git installation in Tools \> Options \> Repository.

&nbsp;

![Workgroup tools options repository](<lib/Workgroup%20tools%20options%20repository.png>)

&nbsp;

&nbsp;

You may also specify a custom path to your Git client. &nbsp;

&nbsp;

**Note:** Be careful that GitHub Desktop, SourceTree and other visual applications are NOT the Git client the we're looking for here.&nbsp; They are GUI applications also leveraging the system Git executable.&nbsp; If you specify a custom path, it must be to the Git executable.

&nbsp;

With GitHub Desktop, it is possible that the installation did not declare the location of the Git executable in the system PATH.&nbsp; This is a [well documented situation](<https://stackoverflow.com/questions/26620312/git-installing-git-in-path-with-github-client-for-windows> "target=\"\_blank\"")...&nbsp; Hackolade Studio has been enhanced to auto-detect the Git executable installed by GitHub Desktop, if in one of its standard locations: &nbsp;

**C:\\Program Files\\Git\\bin\\git.exe**

**C:\\Users\\%username%\\AppData\\Local\\GitHubDesktop\\app-3.0.0\\resources\\app\\git\\cmd\\git.exe** (GitHub Desktop version 1.1 and above)

&nbsp;

If installed elsewhere, like&nbsp;

**C:\\Users\\%username%\\AppData\\Local\\GitHub\\PortableGit\_\<guid\>\\cmd\\git.exe** (GitHub for Windows prior to version 1.1)

you may have to declare the custom path manually.

&nbsp;

## Installing the Git executable

You need to install a Git client if one is not yet present on your machine.&nbsp; You may have to ask your IT department to install the latest version of the Git client from [the official Git website](<https://git-scm.com/downloads> "target=\"\_blank\""), and follow [these instructions](<https://git-scm.com/book/en/v2/Getting-Started-Installing-Git> "target=\"\_blank\"").&nbsp; During the installation process, make sure to NOT disable the use of the credential manager (it is enabled by default).&nbsp; This is the safest way for your Git client to store your credentials and to avoid prompting you every time they are needed.

&nbsp;

![Image](<lib/Workgroup%20Git%20for%20Windows%20Installation.png>)

&nbsp;

&nbsp;

In the .gitconfig file, typically found on Windows in **C:\\Users\\%username%**, you make sure that the following values are set correctly:

\[core\]

&nbsp; &nbsp; autocrlf = true

&nbsp; &nbsp; longpaths = true

&nbsp; &nbsp; fsmonitor = false

&nbsp;

&nbsp;

