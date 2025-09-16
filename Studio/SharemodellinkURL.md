# Share model link URL

**Warning:** the creation of shared model link is available only to Workgroup Edition license users.&nbsp; The resulting URL can be opened by other Editions, possibly with [limitations according to each edition](<Editions.md>).

&nbsp;

Data models are, among other things, a communication tool.&nbsp; Collaboration, consensus, completeness, and much more is better accomplished when a data models is shared among all the stakeholders, and across organizations.&nbsp; As the [Agile Manifesto history](<https://agilemanifesto.org/history.html> "target=\"\_blank\"") eloquently states: "We embrace modeling, but not in order to file some diagram in a dusty corporate repository."

&nbsp;

In order to socialize data models, Hackolade Studio now allows for authors of models to share a model link URL that can be communicated via email, Jira / Confluence, a portal, EA tools, data dictionaries, etc. &nbsp;

&nbsp;

**Important:** sharing a model link URL is a function that is only available in the Workgroup Edition.&nbsp; The reason is that building the model link requires collecting metadata by executing Git commands, which is only supported in the Workgroup edition of the desktop app.&nbsp; This feature is available for GitHub (online and server), Azure DevOps Repos, GitLab Cloud \& Server, and Bitbucket Cloud.

&nbsp;

**Note:** the feature is only available for a model that is available in a Git repo.&nbsp; Simply creating a model on your local machine does not make it shareable.&nbsp; Until you commit and push it to a remote repo, then share the link to that model.

&nbsp;

**Note:** as a prerequisite, link users must have granted access to the location where the model is stored (the Git provider repository), and must have a validated license seat for at least the Read-Only Viewer Edition of Hackolade Studio. &nbsp;

&nbsp;

## Create a shareable link

It is possible to share the data model that is currently opened via a the menu entry: *File* \> *Share Data Model Link..., a keyboard shortcut* (Ctrl+K, Cmd+K), or via the toolbar icon.

![File Share Data Model Link URL](<lib/File Share Data Model Link URL.png>)

&nbsp;

&nbsp;

These action trigger a dialog displaying the link which the user can copy to the clipboard, and additional useful information and messages:

&nbsp;

![File Share Data Model Link](<lib/File Share Data Model Link.png>)

&nbsp;

&nbsp;

A shareable link is a URL that matches the following pattern.

> https://studio.hackolade.com ? model=... \[\& host=...\]

&nbsp;

Such a URL points to the browser application and passes some query parameters in order to instruct it to open the given model.&nbsp; The link can refer to a given branch, to the default branch or a given commit hash.&nbsp;

&nbsp;

**Warning:** users should be careful when sharing a model URL within a non-default branch.&nbsp; It may be useful to share the temporary state of model within a feature branch.&nbsp; But the branch will most likely follow a lifecycle with probably merging into a parent branch and subsequent deletion. Persisting model links should only be done when to stable branches.

&nbsp;

**Note:** seeing the URL structure above may give the impression that users can assemble their own.&nbsp; Be careful that there is complex logic to calculate this URL depending on model state, provider parameters and APIs.

&nbsp;

## Open a shared link

When clicking on a Hackolade Studio model shareable link, the default browser of the user will open a new tab running the browser deployment of Hackolade Studio at [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"\_blank\"")&nbsp;

&nbsp;

The user is presented with a confirmation dialog to validate the legitimacy of the model URL before it gets loaded by the application:

&nbsp;

![File Share Data Model Link Open](<lib/File Share Data Model Link Open.png>)

&nbsp;

The model must be accessible by the user.&nbsp; It maybe required to [authenticate](<Connecttoarepositoryhub.md>), according to the repo provider's methods.

&nbsp;

If the model exceeds the limit of the Community Edition, then the license status is checked so at least a Read-Only Viewer Edition is present. &nbsp;

&nbsp;

The model referenced in the shareable link opens in the browser tab, provided that the pre-requisites are met.

&nbsp;

