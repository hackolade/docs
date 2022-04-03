# Pre-requisites

There are 2 pre-requisites for using the Workgroup Edition of Hackolade Studio:

* you or your organization must have purchased the Workgroup Edition, or the Workgroup upgrade option to the Professional Edition. This repository feature is not available in the Community, Personal or Professional Editions. If you don't have the Workgroup Edition yet, you may contact us at [sales@hackolade.com](<mailto:sales@hackolade.com?subject=Interested%20in%20Workgroup%20Edition>).
* a Git client must be installed on your computer.&nbsp;

&nbsp;

Here are the steps to verify that your installation meets both criteria...

&nbsp;

In Hackolade Studio, **open the repository context**.

* choose Repository \> Open Repository Context in the top menu;
* use the keyboard shortcut Ctrl+G (Cmd+G on MacOS);
* switch to the repository context through the vertical Context Bar on the left;
* move up or down in the Context bar by using the shorcut Ctrl+Up/Down arrow (Cmd+Up/Down arrow on MacOS).

&nbsp;

If you do have the Workgroup Edition, then **look at the top bar while in the Repository Context**.&nbsp; If you don't see any error message in the top bar, then everything is fine: you already have a Git client and it is ready to be used by Hackolade Studio. If you do see an error message in the top bar, then there is a problem.&nbsp; Read on...

&nbsp;

![Image](<lib/Workgroup%20invalid%20git%20client.png>)

&nbsp;

Either you do have a Git client but it has not been made available globally through the PATH environment variable.&nbsp; You can then configure the path to your Git client in Hackolade Studio: click the "Open Git settings" button or go to Tools \> Options \> Repository.&nbsp;

&nbsp;

![Workgroup Git diagnostic](<lib/Workgroup%20Git%20diagnostic.png>)

&nbsp;

Or you don't have a Git client yet and you need to install one.&nbsp; You may have to ask your IT department to install the latest version of the Git client from [the official Git website](<https://git-scm.com/downloads> "target=\"\_blank\""), and follow [these instructions](<https://git-scm.com/book/en/v2/Getting-Started-Installing-Git> "target=\"\_blank\"").&nbsp; During the installation process, make sure to NOT disable the use of the credential manager (it is enabled by default).&nbsp; This is the safest way for your Git client to store your credentials and to avoid prompting you every time they are needed.

&nbsp;

![Image](<lib/Workgroup%20Git%20for%20Windows%20Installation.png>)

&nbsp;

&nbsp;

Note that, in case of problems, you can perform at any time a diagnostic of your Git installation in Tools \> Options \> Repository.

