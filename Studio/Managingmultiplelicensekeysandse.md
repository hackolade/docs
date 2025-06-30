# Managing multiple license keys and seats

You should know that there is no such thing as a license "assignment".  Our server merely records validations and releases, plus enforces the number of seats and validity periods.  That's all.  All actions take place on the user's side within the Hackolade Studio License Status screen, which can be accessed via the key icon in the lower left side of the application workspace, or via the Help menu..  

We don't know, or care about, who's who.  We merely record instances of a validation, but we track the machine internal number and an identifier so it makes it easier for you, when viewing the screen described below, to know who uses each seat.&nbsp; The identifier does not have to be a name or an email address.&nbsp; It can be a login code or any identifier that uniquely distinguishes the user of each seat.

This screen allows you to visualize, in real time, the usage of your key(s).&nbsp; It is all self-service, but it is the customer's responsibility to know and manage to whom they give the key.  A license key is a valuable asset, similar to a physical asset like a laptop of equivalent value.&nbsp; If someone should no longer use the key, simply ask them to release the key in their License Status screen, as described later in this page.

If you're a license administrator, you may want to track who's using your licenses of Hackolade. You may do so by accessing the URL [https://quicklicensemanager.com/hackolade/QlmCustomerSite/qlmlicenseinfo.aspx](<https://quicklicensemanager.com/hackolade/QlmCustomerSite/qlmlicenseinfo.aspx> "target=\"\_blank\"")

 ![QLM - License Manager no identification](<lib/QLM - License Manager no identification.png>)

To have identification information appear in the Computer Name column, users need to go to Help \> Software Key Validation, then release their key, copy it to their clipboard, then fill in the identifier (name or whatever other standard you decide), paste the key, and validate again.

![Image](<lib/QLM - License Manager - identification.png>)

\
The identifier entered in the above screen will appear in the web page:

![QLM - License Manager with identification](<lib/QLM - License Manager with identification.png>)

&nbsp;

## To release a seat of an individual license key

Please read [this article](<Transferalicensetoanewcomputer.md>).

## To release seats of a concurrent license key

We encourage to communicate to all users the principles of “good citizenship”.&nbsp; If a user keeps the application opened in the background, it holds the seat, making so it that a colleague probably risks being denied access the application.&nbsp; It is also important to gracefully exit the application, i.e. not just close a remote desktop session or reboot a machine with the application still open.&nbsp; The application only communicates with our server to release a seat if and only if one of the following options is used:

* Menu option File \> Exit
* Keyboard shortcut Alt+F4 (Windows) or Cmd+Q (Mac)
* The X in the top right corner of the application window (Windows) or the red X in the top left of the window (Mac)

&nbsp;

If a seat is kept reserved after an “ungraceful” exit, it is easy to release it.&nbsp; Simply start the application again on the machine or session of the reserved seat, then exit the application gracefully.

&nbsp;

&nbsp;

