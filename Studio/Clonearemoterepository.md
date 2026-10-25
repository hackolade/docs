# Clone a remote repository

You may skip this section if you already have a local copy of the remote repository.

&nbsp;

If you don't have a local copy of the remote repository yet, then you first need to clone it. You can do this from Hackolade Studio by following the steps below:

&nbsp;

![Workgroup clone](<lib/Workgroup clone.png>)

&nbsp;

> [!IMPORTANT]
> We strongly suggest to **avoid** cloning your repo in a folder which is synchronized with the cloud (OneDrive, Google Drive, iCloud, Dropbox, etc...) The sync mechanism may cause perverse performance effects and sometimes conflicts with the Git processes.

&nbsp;

- **Open the repository context**.
  - choose Repository > Open Repository Context in the top menu;
  - use the keyboard shortcut Ctrl+G (Cmd+G on MacOS);
  - or switch to the repository context via the icon in the vertical Context Bar on the left;
  - move up or down in the Context bar by using the shortcut Ctrl+Up/Down arrow (Cmd+Up/Down arrow on MacOS).
- In the top bar, **select "URL" as source**. Every remote repository has a URL to clone it.
- **Provide the URL** of the repository you want to clone. The protocols HTTPS and SSH are both supported.
- **Click on "Clone"**.
- **Select or create the local folder** where you want the remote repository to be cloned. That folder can be located anywhere on your local machine, but must be empty. You will get an error message if it is not.
- **Provide the requested credentials** if needed. Read more about Git authentication [here](Authentication.md).

&nbsp;

You're done! You now have a local copy of the remote repository in the specified folder. And it has been opened automatically.

&nbsp;

![Workgroup explore files](<lib/Workgroup explore files.png>)
