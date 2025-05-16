# Authentication

A Git repository can be private and secured, which makes it impossible for non-authenticated users to clone it, pull remote commits, and push their local commits.&nbsp; If you need to interact with such a repository, then Hackolade Studio prompts you for your credentials when needed.

&nbsp;

Note that Hackolade Studio does not store your Git credentials: your Git client does, in the [credential store](<https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage> "target=\"\_blank\"") that it has been configured to use. If you are repeatedly prompted for credentials, then it could be that the option to use the credential manager was disabled during the Git installation process (see [pre-requisites](<Pre-requisites.md>)).&nbsp; The easiest solution is to re-install the Git client with the credential manager.

&nbsp;

## HTTPS username and password

If your repository has an HTTPS URL, then you might have to provide the username and password that you use to connect to the Git platform that hosts your private repository (e.g. GitHub, GitLab, etc.).

&nbsp;

![Workgroup auth https](<lib/Workgroup auth https.png>)

&nbsp;

**Warning**: if you use GitHub, then you cannot connect with your traditional password from a Git client.&nbsp; You must [generate a personal access token](<https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token> "target=\"\_blank\"") and use it as your password. You may need to ask for a token from your GitHub administrator or IT department.

&nbsp;

## Git Credentials Manager

The [Git Credential Manager](<https://github.com/git-ecosystem/git-credential-manager> "target=\"\_blank\"") is a cross-platform [credential helper](<https://git-scm.com/docs/gitcredentials> "target=\"\_blank\"") that aims to provide a consistent and secure authentication experience, including multi-factor auth, to every major repository hub (e.g. GitHub, GitLab, Bitbucket). It comes as the default credential helper with [Git for Windows](<https://gitforwindows.org/> "target=\"\_blank\"") since the version 2.29 (Oct 19, 2020).

&nbsp;

The Git Credential Manager does not only store your credentials, it also takes over from Hackolade Studio the responsibility of prompting you when credentials are missing. If your Git client has been configured to use the Git Credential Manager, then you will be prompted for credentials outside Hackolade Studio, through the user interface below that belongs to the Git Credential Manager.

![Git Gredential Manager prompt](<lib/Git Gredential Manager prompt.png>)

The easiest option is for you to choose *Sign in with your browser*. Clicking that button will open your browser and direct you to your repository hub in order to grant the Git Credential Manager access to your account. Make sure to complete the authentication flow by clicking the *Authorize* button.

![Git Credential Manager GtiHub Auth](<lib/Git Credential Manager GtiHub Auth.png>)

&nbsp;

If the option to sign in with your browser is not supported by your repository hub, then you can fallback to providing your username / password or a token. Another alternative is to cancel the prompt of the Git Credential Manager and [connect to the repository hub](<Connecttoarepositoryhub.md>) using Hackolade Studio.

&nbsp;

## SSH passphrase

If your repository has an SSH URL and if your SSH key is protected by a passphrase, then you might be prompted for that passphrase.

&nbsp;

![Workgroup auth SSH](<lib/Workgroup auth SSH.png>)

&nbsp;

If you don't have an SSH key yet, then you need to create one. Follow the links below to get more details about the SSH key creation procedure for your specific repository hub provider:

* [Connect to GitHub with SSH](<https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh> "target=\"\_blank\"")
* [Connect to Bitbucket with SSH](<https://support.atlassian.com/bitbucket-cloud/docs/set-up-an-ssh-key/> "target=\"\_blank\"")
* [Connect to Azure Repos with SSH](<https://docs.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate?view=azure-devops> "target=\"\_blank\"")
* [Connect to GitLab with SSH](<https://docs.gitlab.com/ee/user/ssh.html> "target=\"\_blank\"")

[](<https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-ssh-unixes.html> "target=\"\_blank\"")

Consult this page for more information on connecting to a [repository hub.](<Connecttoarepositoryhub.md>).

&nbsp;

&nbsp;

