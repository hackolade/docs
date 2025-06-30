# Explore files

When you open a local repository and choose Explore repository \> Files in the left menu, you get a table listing all the Hackolade data models in the repository across the different subfolders, if any.&nbsp; The "Show only models" button lets you toggle the display of all files in the repository, whether they're data models or not.

&nbsp;

![Workgroup explore files](<lib/Workgroup explore files.png>)

&nbsp;

Different strategies are available for discovering data models in a repository, among which you can choose by clicking the cogwheel icon to access the options:

* **Listing all files ending with the extension .hck.json**.

  * Limitation: the models created before the introduction of this extension are not listed.&nbsp; If possible, we advise you to change the extension of these older data models from .json to .hck.json. We introduced this double extension to easily differentiate data models from JSON documents, JSON Schema files, or Swagger/OpenAPI specs.

* **Listing all files ending with the extension .json**.

  * Limitation: if your repository contains other JSON files that are not data models (documents, JSON Schema, OpenAPI, etc.), they are also listed here.&nbsp; If possible, we advise you to change the extension of the data models from .json to .hck.json and to use the first strategy above.

* **Scanning the content of the JSON files**.

  * Limitation: although this strategy may give more accurate results, it can be much slower depending on the size of your repository and of the JSON files present, as the application must open each .json file to determine whether it is a Hackolade data model or not.

&nbsp;

You can pick the strategy that best fits your case through the table's filter.&nbsp; The last strategy selected is saved and restored for your next sessions.

&nbsp;

You can open a data model from the table by clicking on the corresponding file name.&nbsp; You can also open it in a new application instance by clicking on the icon to the left.

&nbsp;

To display the history of commits for a file, you may click on the icon on the left.

&nbsp;

You can create a new data model by clicking on the button at the top-right corner of the pane (or by pressing Ctrl+N / Cmd+N.)&nbsp; If you save a newly created data model while having a repository opened, then Hackolade suggests to save it in that repository by default.&nbsp; This behavior takes precedence over the default folder defined in "Tools \> Options \> Default Paths \> Models".

&nbsp;

Any change made outside Hackolade should be automatically reflected in the table (e.g. deleting a data model through the OS.)&nbsp; If you believe that the content of the table does not properly reflect the state of your filesystem,&nbsp; you can click on the refresh icon next to the title.

&nbsp;

Note that, if Git has been instructed to ignore some files (through the [gitignore](<https://git-scm.com/docs/gitignore> "target=\"\_blank\"") functionality), they are not listed in the table.

