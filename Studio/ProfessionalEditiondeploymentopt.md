# Professional Edition deployment options

Our large customers generally use one out of 3 different strategies to handle our frequent application updates:

&#49;) IT policy allows them to install software individually, and they like the reactivity and high frequency of Hackolade updates.  Individual users update the application as soon as it becomes available, knowing that Hackolade data models are backward-compatible (a model saved with a newer version can be read with an older version of the software, except for some extremely rare well documented and communicated exceptions.)  So there is no worry if users temporarily run a different version of the software.

&#50;) At the other extreme, IT does not allow software installation by individual users.  The IT department periodically downloads and validates a target Hackolade version, then deploys to specific users via ghost/image or other software deployment mechanism.   The typical complaint we've heard about this approach is that, due to heavy administration/bureaucracy, releases only become available to users once or twice per year.  As a result, users miss out on the constant enhancements to the application.

&#51;) The following middle ground seems to be happening as well.  A Virtual Machine is set up where a team deploys a Hackolade version once, and all users logged in via Remote Desktop  run their own instance of the same software version.  The only drawbacks being mentioned about this approach are as follows:

* usability of RDP is not as smooth as running software directly on the local desktop
* some users require extra training for RDP
* some organizations are not familiar with VM setup
* user login should be integrated with the org's Active Directory.

Note that licensing rules do not change because the software is deployed on a VM.  Licensing is still "per seat" whereby each user client on the VM will be counted as a seat.

&nbsp;

As a reminder, Hackolade installation does not require admin rights as it does not interact with Windows Registry.  But installation by individual users may be forbidden by IT policy, even if it is technically possible.

Don't hesitate to contact [support@hackolade.com](<mailto:support@hackolade.com>) if you have other questions.


***
_Created with the Personal Edition of HelpNDoc: [News and information about help authoring tools and software](<https://www.helpauthoringsoftware.com>)_
