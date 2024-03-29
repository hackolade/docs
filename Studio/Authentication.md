# Authentication

A Git repository can be private and secured, which makes it impossible for non-authenticated users to clone it, pull remote commits, and push their local commits.&nbsp; If you need to interact with such a repository, then Hackolade Studio prompts you for your credentials when needed.

&nbsp;

Note that Hackolade Studio does not store your Git credentials: your Git client does, in the [credential store](<https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage> "target=\"\_blank\"") that it has been configured to use. If you are repeatedly prompted for credentials, then it could be that the option to use the credential manager was disabled during the Git installation process (see [pre-requisites](<Pre-requisites.md>)).&nbsp; The easiest solution is to re-install the Git client with the credential manager.

&nbsp;

## HTTPS username and password

If your repository has an HTTPS URL, then you might have to provide the username and password that you use to connect to the Git platform that hosts your private repository (e.g. GitHub, GitLab, etc.).

&nbsp;

![Workgroup auth https](<lib/Workgroup%20auth%20https.png>)

&nbsp;

**Warning**: if you use GitHub, then you cannot connect with your traditional password from a Git client.&nbsp; You must [generate a personal access token](<https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token> "target=\"\_blank\"") and use it as your password. You may need to ask for a token from your GitHub administrator or IT department.

&nbsp;

## SSH passphrase

If your repository has an SSH URL and if your SSH key is protected by a passphrase, then you might be prompted for that passphrase.

&nbsp;

![Workgroup auth SSH](<lib/Workgroup%20auth%20SSH.png>)

&nbsp;

If you don't have an SSH key yet, then you need to create one. Follow the links below to get more details about the SSH key creation procedure for your specific repository hub provider:

* [Connect to GitHub with SSH](<https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh> "target=\"\_blank\"")
* [Connect to Bitbucket with SSH](<https://support.atlassian.com/bitbucket-cloud/docs/set-up-an-ssh-key/> "target=\"\_blank\"")
* [Connect to Azure Repos with SSH](<https://docs.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate?view=azure-devops> "target=\"\_blank\"")
* [Connect to GitLab with SSH](<https://docs.gitlab.com/ee/user/ssh.html> "target=\"\_blank\"")
* [Connect to AWS CodeCommit with SSH](<https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-ssh-unixes.html> "target=\"\_blank\"")

&nbsp;

Consult this page for more information on connecting to a [repository hub.](<Connecttoarepositoryhub.md>).

