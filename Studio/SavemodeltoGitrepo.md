# Save model to Git repo

**Warning:** this feature, introduced with v8.1.2 is available only to Workgroup Edition license users

&nbsp;

This feature allows to save data models directly to remote Git repositories without requiring a locally-cloned repo. &nbsp; The feature works well with the [*Open From*](<OpenmodelfromGitrepo.md>) feature which allows to open a model directly from a remote Git repository, also without the need for a locally-cloned repo.

&nbsp;

The keyboard accelerator for this entry is Ctrl+Alt+S (Windows/Linux) or ⌃⌘S (Mac).&nbsp;

&nbsp;

![Save to menu option](<lib/Save to menu option.png>)

&nbsp;

Clicking the *Save To..*. option triggers the opening of the *Save To* pane.

&nbsp;

## Save To: This computer

The view for saving a data model to *This computer* looks similar to the one for opening a data model from *This Computer*.&nbsp; You may click the *Save As...* button, which triggers the same behavior as *File \> Save As...* in the menu bar.

&nbsp;

![Save to this computer dialog](<lib/Save to this computer dialog.png>)

## Save To: Remote Repository

If you select a Git provider that you connected to (e.g. *github.com*), a list of the corresponding repositories is displayed.&nbsp; As you enter one of those repositories, you may navigate in the folder structure if necessary, and select the location as the destination to save you data model file.

![Save to remote repository dialog](<lib/Save to remote repository dialog.png>)

(TBA) If necessary, you have the option to create folders by using the *Create folder* button in the footer or an icon that is positioned after the breadcrumb.

Note that newly created folders will not be materialized in the remote repository until the save action is triggered. The reason is that empty folders are not allowed in Git.

&nbsp;

You navigate to the appropriate folder, you must provide a file name for your model. That field is required and automatically pre-filled with a default value (same logic as for the *Save As...* functionality).

You may select the file extension in a drop-down, choosing between **.hck.json** and **.json**. The extension that is selected by default is derived from the preference of the user (*Tools \> Options \> Save models with* **.hck.json** *extension*). Using a separate input component for the file extension simplifies the user experience and prevents user mistakes that could make the model impossible to open (due to a wrong or a missing extension).

Clicking the *Save* button in the footer triggers validation logic. File name field is highlighted by a red border if it's empty.

![Save to remote repository model name dialog](<lib/Save to remote repository model name dialog.png>)

&nbsp;

Once validation passes, the *Save to remote repository* dialog is displayed.

![Save to remote repository commit dialog](<lib/Save to remote repository commit dialog.png>)

Once a data model has been saved to a location, it is not treated as a new data model anymore but as an existing data model for which the location is the one it was saved into. Similarly, if you save a copy of an existing model to a different location, that last location becomes the default location for saving the model in place.&nbsp;

