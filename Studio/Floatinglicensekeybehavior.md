# Floating license key behavior

Dedicated license keys are for exclusive use by regular, intensive users of the application. Whereas the floating license key is for shared use, across many occasional users. While the cost a floating key is higher, there is a benefit for customers to be able to spread the cost across multiple users.

&nbsp;

Watch this [short video](<https://hackolade.odoo.com/slides/slide/concurrent-license-key-behavior-66> "target=\"_blank\"") to view in action the behavior of floating license keys.

&nbsp;

***Behavior***\
With a floating license key, you may install the software on an unlimited number PCs, but only the licensed number of simultaneous users are allowed to use the application. If the maximum number of seats has been reached, the next user will be denied access to the application until another user exits the application.

&nbsp;

Let's illustrate with an example of 5 users sharing a pool of 3 concurrent/floating seats, meaning that, in this example, a maximum of 3 seats can be in use at any time.

&nbsp;

<table>
<colgroup><col style="width:9%"><col style="width:13%"><col style="width:13%"><col style="width:12%"><col style="width:14%"><col style="width:15%"><col style="width:24%"></colgroup>
<thead>
<tr>
<th>Time</th>
<th>User 1</th>
<th>User 2</th>
<th>User 3</th>
<th>User 4</th>
<th>User 5</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr>
<td>9:00 AM</td>
<td>✅ Active</td>
<td>✅ Active</td>
<td>✅ Active</td>
<td>-</td>
<td>-</td>
<td>3 seats in use</td>
</tr>
<tr>
<td>9:10 AM</td>
<td>✅ Active</td>
<td>✅ Active</td>
<td>✅ Active</td>
<td>⏳ Access denied</td>
<td>⏳ Access denied</td>
<td>Users 4 &amp; 5 attempt to access</td>
</tr>
<tr>
<td>9:20 AM</td>
<td>✅ Active</td>
<td>X Closes app</td>
<td>✅ Active</td>
<td>✅ Active</td>
<td>⏳ Access denied</td>
<td>Seat freed, User 4 can join</td>
</tr>
<tr>
<td>9:30 AM</td>
<td>✅ Active</td>
<td>-</td>
<td>✅ Active</td>
<td>✅ Active</td>
<td>⏳ Access denied</td>
<td>Still full</td>
</tr>
<tr>
<td>9:40 AM</td>
<td>X Closes app</td>
<td>-</td>
<td>✅ Active</td>
<td>✅ Active</td>
<td>✅ Active</td>
<td>Seat freed, User 5 can join</td>
</tr>
<tr>
<td>9:50 AM</td>
<td>-</td>
<td>-</td>
<td>✅ Active</td>
<td>X Closes app</td>
<td>✅ Active</td>
<td>Seat freed again</td>
</tr>
<tr>
<td>9:50:01 AM</td>
<td>-</td>
<td>-</td>
<td>✅ Active</td>
<td>-</td>
<td>✅ Active</td>
<td>2 seats in use</td>
</tr>
</tbody>
</table>

&nbsp;

While dedicated seats are assigned to a specific user, a floating seat is floating, and is only assigned to a given user while the application is opened for that user. As the user closes the application, the seat becomes available to be used by another user.

&nbsp;

![Dedicated vs floating license seat 1](<lib/Dedicated vs floating license seat 1.png>)\
![Dedicated vs floating license seat 2](<lib/Dedicated vs floating license seat 2.png>)\
![Dedicated vs floating license seat 3](<lib/Dedicated vs floating license seat 3.png>)

&nbsp;

In the above example, the floating license was for a single seat, meaning that only one user at a time could use Hackolade Studio. If you purchase a floating license key with 2 seats, now you can have any combination of 2 simultaneous users:\
![Dedicated vs floating license with 2 seats](<lib/Dedicated vs floating license with 2 seats.png>)

&nbsp;

Note that if you have one virtual machine with multiple users, each user will be counted as a separate seat.

&nbsp;

## Virtual Machines

> [!NOTE]
> It is critical that the VM setup is such that you access a **persistent** VM instance of the application. Non-persistent instances will cause license issues. See [this article](<https://www.parallels.com/blogs/ras/persistent-vdi-vs-non-persistent/> "target=\"_blank\"") for a good discussion of persistent vs non-persistent (or stateless) VDI.

&nbsp;

Regardless of the license seat reservation, the lack of session persistence would mean that parameters, preferences, custom properties, etc.. are all lost between sessions.

&nbsp;

For all these reasons, you must have persistent VMs/VDIs.

&nbsp;

![Persistent vs non-persistent VDI](<lib/Persistent vs non-persistent VDI.png>)

&nbsp;

## Cloud-based license server

There is no need to install and maintain a server inside your infrastructure. The number of seats being used is automatically tracked by our license server in the cloud.\
![License keys tracked in the cloud](<lib/License keys tracked in the cloud.png>)

&nbsp;

[This article](Managingmultiplelicensekeysandse.md) provides the link to an admin page where you can track, in real time, the usage of your license key.

&nbsp;

A floating license key must be entered just once by each user and validated. After that, the process should be seamless for users. If enough seats are available, all that is required is for users to open the application when they need it, then exit the application when they are done. Seat reservation and release are automatically operated by the software.

&nbsp;

Users may exit Hackolade Studio using several accepted methods. Probably the most common one is by clicking the "X" in the top right-hand corner of the application. You may also use the menu File, then Exit. Or you may use the keyboard shortcut, for example in Windows, with Alt plus F4, or Command plus Q on a Mac.

&nbsp;

If you have multiple instances of the application running, it is of course necessary to close all of them. Only the last one running will communicate the seat release to our license server upon exit.

&nbsp;

## Be considerate of others

An important word of advice: all users should be mindful and considerate of others, and exit the application when they no longer need it, so as to release the seat and render it available for someone else in the organization. When just switching focus to another application, Hackolade Studio remains active in the background, and continues to occupy the reserved seat.

&nbsp;

![Concurrent license key - be considerate](<lib/Concurrent license key - be considerate.png>)

&nbsp;

Also important is the fact that you must exit the application "gracefully" in order to allow for the application to communicate with our license server in the cloud, and release the seat. Just rebooting the machine while Hackolade Studio is running does not release the seat. Neither does closing the Remote Desktop session.

&nbsp;

![Elegantly exiting Hackolade Studio](<lib/Elegantly exiting Hackolade Studio.png>)

&nbsp;

If this situation ever happened accidentally, don't worry. You just need to access the application again, then exit it "elegantly", and the seat will be released as expected. Similarly, if you notice in the license information screen that a user seems to be holding on to a seat, you may ask them to simply access the application again, then exit all instances.
