# Migration to enhanced custom properties

## Migration to enhanced custom properties, starting with v3.6.2

&nbsp;

Read this if you have defined custom properties for Hackolade targets, and might have outside processes reading Hackolade model files.

&nbsp;

Based on user feedback, we have made 2 major enhancements to the way we handle custom properties:

* we have split your custom properties from our plugins.&nbsp; This way, each time we publish a new version of any plugin, you may safely apply the plugin update without fear of losing your custom properties;
* for targets that we call ‘native targets’ (JSON, Couchbase, DynamoDB, and MongoDB) as they did not require a plugin for modeling, the custom properties controls had lagged behind the ‘plugin targets’ (targets that require a plugin for modeling.)&nbsp; We have brought all targets to the same level of controls you can use for your custom properties.&nbsp; As part of this change, we also removed an unnecessary complexity in the schema of Hackolade models for native targets only.&nbsp; Custom properties of native targets will be listed in models with other properties, just like for plugin targets (instead of within a customProperties sub-object.)

&nbsp;

These enhancements have been introduced with the release of v3.6.2.&nbsp; These changes are such that you can safely upgrade to v3.6.2 and beyond, while continuing to work as before, if you wish.&nbsp; But if you want to leverage the above enhancements, it is recommended that you read the rest of this page carefully.&nbsp; You do have full control on the timing of rolling out these enhancements.

&nbsp;

With these enhancements, we introduce a new structure on your local file system where your custom properties are stored separately from our plugins.&nbsp; Historically when a plugin was installed, you could find it in the folder C:\\Users\\%username%\\.hackolade\\**plugins** (on Mac in Users/$USER/.Hackolade/**plugins**) where you made your changes.&nbsp; This is where you were adding your custom properties.

&nbsp;

From now on, and while we will continue to store our offical plugins in that same place, your custom properties will be stored in the folder C:\\Users\\%username%\\.hackolade\\**options** (on Mac in Users/$USER/.Hackolade/**options**)&nbsp; If you use the Excel import/export functionality, this is also where we store the object selection profiles for each target.

&nbsp;

The migration of your custom properties can be performed either automatically next time we publish a new plugin version (we will detect that you have custom properties and we will migrate them to the new structure after user confirmation), or pro-actively by each user.&nbsp; Migration is performed one target at a time.

&nbsp;

**IMPORTANT:** particular care is required if you've customized **native** targets (JSON, Couchbase, DynamoDB, and MongoDB) **and** your Hackolade model files are read/manipulated by outside processes (integrated in a data dictionary or portal, used for code generation, etc…)&nbsp; We will now store custom properties with other properties inside model files (i.e. no longer inside a customProperties sub-object.)&nbsp; Your outside systems may need to be adjusted accordingly.

&nbsp;

### &#49;. Migrate your custom properties for plugin targets

With v3.6.2, we have removed the link "Show Plugin Directory" from the Help menu.&nbsp; A link for each plugin will become available after migration of that plugin.

&nbsp;

Go to Help \> Plugin Manager \> Installed, and you will see a listing like this one:

![CustomProp migration - plugin manager before](<lib/CustomProp migration - plugin manager before.png>)

&nbsp;

In the above, we can see 2 plugins: one for a *native target* (MongoDB) and one for a *plugin target* (Neo4j.)&nbsp; Each shows a Migrate button.

&nbsp;

When you press the Migrate button for a **plugin** target, you get this dialog:

![CustomProp migration - plugin target warning](<lib/CustomProp migration - plugin target warning.png>)

If you confirm, the process will check if you have any custom properties in your old plugin for that target, and will migrate them to the new structure in C:\\Users\\%username%\\.hackolade\\options (on Mac in Users/$USER/.Hackolade/options)

&nbsp;

The success of the operation is confirmed with this dialog:

![CustomProp migration - success dialog](<lib/CustomProp migration - success dialog.png>)

&nbsp;

After restarting the application, and should see no visible changes to your custom properties, but you now have a link to the directory where you can maintain your properties for that plugin.

![CustomProp migration - plugin mgr after 1](<lib/CustomProp migration - plugin mgr after 1.png>)

&nbsp;

Because this is a plugin target (i.e. not JSON, Couchbase, DynamoDB, or MongoDB), no action is required, as there are no schema changes in the Hackolade models.&nbsp; You may now create and maintain custom properties for the migrated plugin.&nbsp; New updates released by us for that plugin can be safely applied without touching your customizations.

&nbsp;

### &#50;. Migration for native targets

**Important note:** you may need to coordinate the migration of your customizations for native target with the evolution of outside systems, if they read Hackolade models.

&nbsp;

When you press the Migrate button for a **native** target, you get this dialog:

![CustomProp migration - native target warning](<lib/CustomProp migration - native target warning.png>)

&nbsp;

The migration process is slightly different than for plugin targets.&nbsp; If you confirm, the process will also check if you have any custom properties in your old plugin for that target, and will migrate them to the new structure in C:\\Users\\%username%\\.hackolade\\options (on Mac in Users/$USER/.Hackolade/options)&nbsp; For native targets, the original plugin is removed entirely (it is no longer necessary), and only customization are kept.&nbsp; Just in case, a zip achive of the plugin is kept under C:\\Users\\%username%\\.hackolade\\tmp (on Mac in Users/$USER/.Hackolade/tmp)

&nbsp;

The success of the operation is confirmed with this dialog:

![CustomProp migration - success dialog](<lib/CustomProp migration - success dialog.png>)

&nbsp;

After restarting the application, and should see no visible changes to your custom properties, but you now have a link to the directory where you can maintain your properties for that plugin.

![CustomProp migration - plugin mgr after 2](<lib/CustomProp migration - plugin mgr after 2.png>)

&nbsp;

Because this is a native target, you should go through step 3 below: adapt your models

&nbsp;

&nbsp;

### &#51;. Adapt your models&nbsp;

This step is only necessary for native targets (JSON, Couchbase, DynamoDB, and MongoDB) and if your models are read by other systems than Hackolade.&nbsp; If no other systems are reading custom properties in your Hackolade models, you don't have to do anything special.

&nbsp;

When a Hackolade model for a migrated native target is opened with the application, the content of the model evolves automatically to the new structure (i.e. the customProperties sub-object is suppressed after moving your custom properties.) &nbsp; You will get this confirmation:

![CustomProp migration - model migration conf](<lib/CustomProp migration - model migration conf.png>)

&nbsp;

You may now create and maintain custom properties for the migrated plugin.&nbsp;

