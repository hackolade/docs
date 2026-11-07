---
description: Create a shareable URL to a data model in a Git repository with Hackolade Studio Workgroup Edition, and open shared links.
seoTitle: Share a link to a data model
image: lib/File Share Data Model Link.png
---
# Share model link URL

> [!WARNING]
> The creation of shared model link is available only to Workgroup Edition license users. The resulting URL can be opened by other Editions, possibly with [limitations according to each edition](Editions.md).

Data models are, among other things, a communication tool. Collaboration, consensus, completeness, and much more is better accomplished when a data models is shared among all the stakeholders, and across organizations. As the [Agile Manifesto history](<https://agilemanifesto.org/history.html> "target=\"_blank\"") eloquently states: "We embrace modeling, but not in order to file some diagram in a dusty corporate repository."

In order to socialize and democratize data models, Hackolade Studio now allows for authors of models to share a model hyperlink that can be communicated via email, Jira / Confluence, a portal, EA tools, data dictionaries, Excel, documents, etc.

> [!IMPORTANT]
> Sharing a model link URL is a function that is only available in the Workgroup Edition. The reason is that building the model link requires collecting metadata by executing Git commands, which is only supported in the Workgroup edition of the desktop app. This feature is available for GitHub (online and server), Azure DevOps Repos, GitLab Cloud & Server, and Bitbucket Cloud & Data Center.

> [!NOTE]
> The feature is only available for a model that is available in a Git repo. Simply creating a model on your local machine does not make it shareable. Until you commit and push it to a remote repo, then share the link to that model.

> [!NOTE]
> As a prerequisite, link users must have granted access to the location where the model is stored (the Git provider repository), and must have a validated license seat for at least the Read-Only Viewer Edition of Hackolade Studio.

## Create a shareable link

It is possible to share the data model that is currently opened via a the menu entry: *File* > *Share Data Model Link..., a keyboard shortcut* (Ctrl+K, Cmd+K), or via the toolbar icon.\
![File Share Data Model Link URL](<lib/File Share Data Model Link URL.png>)

These action trigger a dialog displaying the link which the user can copy to the clipboard, and additional useful information and messages:

![File Share Data Model Link](<lib/File Share Data Model Link.png>)

A shareable link is a URL that matches the following pattern.\
*https://studio.hackolade.com ? model=... \[& host=...\]*

Such a URL points to the browser application and passes some query parameters in order to instruct it to open the given model. The link can refer to a given branch, to the default branch or a given commit hash.

> [!WARNING]
> Users should be careful when sharing a model URL within a non-default branch. It may be useful to share the temporary state of model within a feature branch. But the branch will most likely follow a lifecycle with probably merging into a parent branch and subsequent deletion. Persisting model links should only be done when to stable branches.

> [!NOTE]
> Seeing the URL structure above may give the impression that users can assemble their own. Be careful that there is complex logic to calculate this URL depending on model state, provider parameters and APIs.

## Open a shared link

When clicking on a Hackolade Studio model shareable link, the default browser of the user will open a new tab running the browser deployment of Hackolade Studio at [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"_blank\"")

The user is presented with a confirmation dialog to validate the legitimacy of the model URL before it gets loaded by the application:

![File Share Data Model Link Open](<lib/File Share Data Model Link Open.png>)

The model must be accessible by the user. It maybe required to [authenticate](Connecttoarepositoryhub.md), according to the repo provider's methods.

If the model exceeds the limit of the Community Edition, then the license status is checked. Only Viewer and Workgroup editions can open model files with more than 50 objects.

The model referenced in the shareable link opens in the browser tab, provided that the pre-requisites are met.

![View data model in browser](<lib/View data model in browser.png>)
