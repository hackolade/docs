# Windows access denied error during upgrade

You should NOT install a new version of Hackolade while the application is running.&nbsp; All instances of the application must be closed for the upgrade to proceed properly. &nbsp;

&nbsp;

If you get this error message:

![Installation error - application running2](<lib/Installation%20error%20-%20application%20running2.png>)

it is an indication that the application is opened.&nbsp; You should close all instances, then choose Try again in the dialog above.

&nbsp;

If the installation still fails, choose the option Cancel installation, then follow these steps:

&#49;) make sure to close all instances of the application\
&#50;) access the Task Manager (ctrl+alt+delete), then click more details if necessary.  You should have a Processes tab with first an Apps group, then a Background Processes group\
&#51;) in the Background processes, if there are Hackolade entries, select the Hackolade entry showing the highest Memory value\
&#52;) press the button "End task"\
&#53;) repeat steps 3) and 4) if necessary\
&#54;) close the Task Manager\
&#55;) start the installation process again

