# Concurrent license key behavior

Dedicated license keys are for exclusive use by regular, intensive users of the application.  Whereas the concurrent license key is for shared use, across many occasional users. While the cost a concurrent key is higher, there is a benefit for customers to be able to spread the cost across multiple users.

&nbsp;

Watch this [short video](<https://hackolade.odoo.com/slides/slide/concurrent-license-key-behavior-66> "target=\"\_blank\"") to view in action the behavior of concurrent license keys. &nbsp;

&nbsp;

***Behavior*** 

With a concurrent license key, you may install the software on an unlimited number PCs, but only the licensed number of simultaneous users are allowed to use the application.  If the maximum number of seats has been reached, the next user will be denied access to the application until another user exits the application. &nbsp;

&nbsp;

![Dedicated vs concurrent license seat](<lib/Dedicated vs concurrent license seat 1.png>)

![Dedicated vs concurrent license seat 2](<lib/Dedicated vs concurrent license seat 2.png>)

![Dedicated vs concurrent license seat 3](<lib/Dedicated vs concurrent license seat 3.png>)

&nbsp;

In the above example, the concurrent license was for a single seat, meaning that only one user at a time could use Hackolade Studio.&nbsp; If you purchase a concurrent license key with 2 seats, now you can have any combination of 2 simultaneous users:

![Dedicated vs concurrent license with 2 seats](<lib/Dedicated vs concurrent license with 2 seats.png>)

&nbsp;

Note that if you have one virtual machine with multiple users, each user will be counted as a separate seat. &nbsp;

&nbsp;

## Virtual Machines

**Note:** it is critical that the VM setup is such that you access a **persistent** VM instance of the application.&nbsp; Non-persistent instances will cause license issues.&nbsp; See [this article](<https://www.parallels.com/blogs/ras/persistent-vdi-vs-non-persistent/> "target=\"\_blank\"") for a good discussion of persistent vs non-persistent (or stateless) VDI.

&nbsp;

![Persistent vs non-persistent VDI](<lib/Persistent vs non-persistent VDI.png>)

 

&nbsp;

## Cloud-based license server

There is no need to install and maintain a server inside your infrastructure.  The number of seats being used is automatically tracked by our license server in the cloud. &nbsp;

![License keys tracked in the cloud](<lib/License keys tracked in the cloud.png>)

 

[This article](<Managingmultiplelicensekeysandse.md>) provides the link to an admin page where you can track, in real time, the usage of your license key.

 

A concurrent license key must be entered just once by each user and validated.  After that, the process should be seamless for users.  If enough seats are available, all that is required is for users to open the application when they need it, then exit the application when they are done.  Seat reservation and release are automatically operated by the software.

&nbsp;

Users may exit Hackolade Studio using several accepted methods.  Probably the most common one is by clicking the "X" in the top right-hand corner of the application.  You may also use the menu File, then Exit.  Or you may use the keyboard shortcut, for example in Windows, with Alt plus F4, or Command plus Q on a Mac.

 

If you have multiple instances of the application running, it is of course necessary to close all of them.  Only the last one running will communicate the seat release to our license server upon exit.

 

## Be considerate of others

An important word of advice: all users should be mindful and considerate of others, and exit the application when they no longer need it, so as to release the seat and render it available for someone else in the organization.  When just switching focus to another application, Hackolade Studio remains active in the background, and continues to occupy the reserved seat.

&nbsp;

![Concurrent license key - be considerate](<lib/Concurrent license key - be considerate.png>)

 

Also important is the fact that you must exit the application "gracefully" in order to allow for the application to communicate with our license server in the cloud, and release the seat.  Just rebooting the machine while Hackolade Studio is running does not release the seat.  Neither does closing the Remote Desktop session. &nbsp;

&nbsp;

![Elegantly exiting Hackolade Studio](<lib/Elegantly exiting Hackolade Studio.png>)

 

If this situation ever happened accidentally, don't worry.  You just need to access the application again, then exit it "elegantly", and the seat will be released as expected.  Similarly, if you notice in the license information screen that a user seems to be holding on to a seat, you may ask them to simply access the application again, then exit all instances.

&nbsp;

