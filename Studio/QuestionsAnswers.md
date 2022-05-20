# Questions & Answers

### How to work with Git submodules?

Git submodules allow you to keep a Git repository as a subdirectory of another Git repository. This lets you clone another repository into your project while keeping your commits separate.

&nbsp;

The presence of Git submodules in a repository will not prevent you from using Hackolade Studio. But there is no handling of Git submodules currently in Hackolade Studio.

&nbsp;

In case Git submodules are important for the handling of your data models, please [submit a feature request](<https://hackolade.zendesk.com/hc/en-us/requests/new> "target=\"\_blank\"").

&nbsp;

### How to deal with non-ASCII symbols in file names?

By default, Git replaces non-ASCII symbols in file names with octal notation. For example, a file named "TrainScheduleф.json" will be treated by Git as "TrainSchedule\\321\\204.json".

&nbsp;

If you need to deal with non-ASCII symbols in file names, then open a terminal and run the command below in order to modify the default behavior of your local Git client (omit the $ sign in Windows).

&nbsp;

$ git config core.quotepath off

&nbsp;

See the official documentation about the Git configuration parameter [core.quotepath](<https://git-scm.com/docs/git-config#Documentation/git-config.txt-corequotePath> "target=\"\_blank\"") for more details.

&nbsp;

## Where is my .gitconfig file?

From time to time, you may have to adjust [Git configuration parameters](<https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup> "target=\"\_blank\"").&nbsp; The problem might be to find the location of the .config file first... You can view all of your settings and where they are coming from using to following command (omit the $ sign in Windows):

$ git config --list --show-origin

&nbsp;

## In Task Manager, I see many orphan background processes for Git for Windows

The issue is not specific to Hackolade and is linked to an experimental feature introduced in Git version 2.31.0.&nbsp; If selected, Git will use a built-in file-system monitor, without the need to install Watchman.&nbsp; However, this feature is not yet stable so it is strongly advised to run the following command:

&nbsp;

For Git versions up to 2.35.x:

$ git config --global core.useBuiltinFSMonitor false

&nbsp;

&nbsp;

For Git version 2.36.0 and above:

$ git config --global core.fsmonitor false

&nbsp;

## I'm getting an error core.useBuiltinFSMonitor=true is deprecated

Starting with version 2.36.0, the congif keyword useBuiltinFSMonitor has been deprecated, and replaced by fsmonitor. When opening a repository, if you get the error:

![Image](<lib/Workgroup%20useBuiltinFSMonitor%20deprecated%20erro.png>)

&nbsp;

The hint is accurate.&nbsp; You should run the following command at a command prompt (omit the $ sign in Windows):

$ git config --global core.fsmonitor false

&nbsp;

&nbsp;

## I have GitHub Desktop installed on my machine.&nbsp; Is it not a Git client?

Be careful that GitHub Desktop, SourceTree and other visual applications are NOT the Git client the we're looking for here.&nbsp; They are GUI applications also leveraging the system Git executable.&nbsp; If you specify a custom path, it must be to the Git executable.

&nbsp;

![Workgroup tools options repository](<lib/Workgroup%20tools%20options%20repository.png>)

&nbsp;

With GitHub Desktop, it is possible that the installation did not declare the location of the Git executable in the system PATH.&nbsp; This is a [well documented situation](<https://stackoverflow.com/questions/26620312/git-installing-git-in-path-with-github-client-for-windows> "target=\"\_blank\"")...&nbsp; Possible locations for the Git executable are:

**C:\\Program Files\\Git\\bin\\git.exe**

**C:\\Users\\%username%\\AppData\\Local\\GitHub\\PortableGit\_\<guid\>\\cmd\\git.exe** (GitHub for Windows prior to version 1.1)

**C:\\Users\\%username%\\AppData\\Local\\GitHubDesktop\\app-3.0.0\\resources\\app\\git\\cmd\\git.exe** (GitHub Desktop version 1.1 and above)

&nbsp;

See more info in the [pre-requisites page](<Pre-requisites.md>).

