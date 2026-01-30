# Deployment policy

At Hackolade, we want to let customers benefit from newly developed features as soon as they are developed and tested.&nbsp; As we say: "application code only comes to life when it’s deployed to production and used by real users.”&nbsp; or "what’s the point of building a feature if it’s destined to gather dust in a drawer?" &nbsp; ;-)&nbsp; This is why we release a new version of the application every single week of the year.

&nbsp;

But some large customers don't want users to be able to upgrade, and prefer to deploy our desktop app with a specific configuration whereby they turn off the checks for application and plugin updates.&nbsp; The main drawback is that users are not aware of the availability of newly developed enhancements, resulting in customers not taking advantage of the heavy investments that Hackolade makes in continuously enhancing the application.

&nbsp;

## Deployment policy file

A deployment policy file allows configuration by the customer. &nbsp;

&nbsp;

The policy allows to selectively turn off the checks for application and plugin updates. As a result, users would not get prompted to update the application and/or the plugins at startup.

&nbsp;

The deployment policy file name is

> hackolade-deployment-policy.toml

&nbsp;

### Policy file format

The application looks for the presence and content the deployment policy file every time the application starts, we apply the configuration, and adjust the application behavior accordingly. &nbsp;

&nbsp;

We have chosen [TOML](<https://en.wikipedia.org/wiki/TOML> "target=\"\_blank\"") for the format of our policy file.

* it has a formal open source [specification](<https://toml.io/en/v1.0.0> "target=\"\_blank\"");
* it allows comments (contrary to JSON for example);
* it supports data types;
* it can be parsed using [smol-toml](<https://github.com/squirrelchat/smol-toml#readme> "target=\"\_blank\""), a small dependency-free library that is fully compliant with the latest version of the TOML specification.

&nbsp;

### Check whether application updates are disallowed

* By default, the check for application updates on startup is enabled.

&nbsp;

Update checks are disabled if the deployment policy file contains the line:

> canCheckForApplicationUpdates = false

&nbsp;

The default application behavior is altered so that:

* the check for application updates on startup becomes disabled.
* the related configuration parameter becomes hidden in *Tools \> Options \> General*.
* the related entry becomes hidden in the Help menu.

​

### Check whether plugin updates are disallowed

* By default, the check for plugin updates on startup is enabled.

&nbsp;

Update checks are disabled if the deployment policy file contains the line:

> canCheckForPluginUpdates = false

&nbsp;

The default application behavior is altered so that:

* the check for application updates on startup becomes disabled.
* the related configuration parameter becomes hidden in *Tools \> Options \> General*.
* the related entry becomes hidden in the Help menu
* users don't get prompted to install plugins (e.g. when opening a model for a target for which the plugin is not installed).

&nbsp;

### Check whether plugin installation is disallowed

* By default, users are allowed to install plugins, provided that they have access to [https://hackolade.com](<https://hackolade.com> "target=\"\_blank\"") and [https://github.com/hackolade](<https://github.com/hackolade> "target=\"\_blank\"").

&nbsp;

Plugin installation are disabled if the deployment policy file contains the line:

> canInstallPlugin

&nbsp;

The default application behavior is altered so that:

* the plugin manager is hidden
* users don't get prompted to install plugins (e.g. when opening a model for a target for which the plugin is not installed).

&nbsp;

### Policy file location

The file location is different depending on the Operating System:

&nbsp;

#### Windows

The deployment policy file is located in the application folder, next to the executable file.&nbsp;

&nbsp;

By default the installer places places the application in:&nbsp;

> C:\\Program Files\\Hackolade

&nbsp;

Although this location may be different if the user changes it during installation, or if the IT image is configured to locate it elsewhere.

&nbsp;

#### Linux

The deployment policy file is located in the application folder where it was unzipped, next to the executable file.

&nbsp;

#### MacOS

On MacOS, the application is installed as one single .app bundle whose content must comply with [a predefined structure](<https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFBundles/BundleTypes/BundleTypes.html#//apple\_ref/doc/uid/10000123i-CH101-SW1> "target=\"\_blank\"").&nbsp; Every file in that package also has a signature (in Contents / \_CodeSignature / CodeResources). The MacOS [Gatekeeper](<https://support.apple.com/en-gb/guide/security/sec5599b66df/web>) ensures that the files still match their original signature before starting the app.&nbsp; As a result alteration of any file in the package would lead to Gatekeeper refusing to start the application.&nbsp;

&nbsp;

The deployment policy file is therefore located in&nbsp;

> Hackolade.app/Contents/Plug-Ins

&nbsp;

## Logging and error handling

In the application log file Hackolade.log, that can be found in Help \> AccessApplication Logs, we keep track of the policy

&nbsp;

If the policy file is empty (aka by default), the log contains this entry:

> Policy: {}

&nbsp;

If a custom policy has been defined, the policy is documented, for example:

> Policy: {\
&nbsp; &nbsp; "canCheckForApplicationUpdates": false,\
&nbsp; &nbsp; "canCheckForPluginUpdates": false\
}

&nbsp;

If there is an error (e.g. a parsing error), the entry may contain:

> Policy: failed (see below)\
Error while parsing the deployment policy: /Users/%username%/.hackolade/hackolade-deployment-policy.toml\
\[cause\]: Invalid TOML document: invalid value\
\
&#49;1: # Whether or not the installation of plugins is allowed\
&#49;2: canInstallPlugin = false;\
&nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \^

&nbsp;

If the policy file could not be found, the entry may contain:

> Policy: null

&nbsp;

