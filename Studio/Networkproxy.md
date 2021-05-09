# Network proxy

If you have an HTTP proxy server on your network, you may have to manually set in the application the proxy parameters with the hostname or IP address of the proxy server.

&nbsp;

You may enter this info via the menu Tools \> Options \> Network Proxy.&nbsp; Access is allowed, even if the license software key is not yet activated.

&nbsp;

Proxy configuration can be achieved in 3 different ways:

&#49;) using your system or browser config (preferred method, requiring no special changes in Hackolade);

&#50;) using HTTPS\_PROXY environment variables you may have used for your proxy settings

&#51;) manually entering proxy address/port and possible username/password

&nbsp;

&nbsp;

The default setting is to use the proxy setting from you system/browser:

![Image](<lib/Proxy%20settings%20-%20automatic.png>)

&nbsp;

&nbsp;

The following option should only be used if you knowingly handle proxy setup through HTTPS\_PROXY environment variables:

![Image](<lib/Proxy%20settings%20-%20HTTPS\_PROXY%20environment%20var.png>)

&nbsp;

&nbsp;

If that fails, you should enter the hostname or IP address of the proxy server, and the appropriate port number.&nbsp; If the proxy server requires a user name and password, you may include your credentials as well:

&nbsp;

![Image](<lib/Proxy%20settings%20--%20manual.png>)

&nbsp;

If necessary, you may also want to whitelist 2 domains: [https://hackolade.com](<https://hackolade.com> "target=\"\_blank\"") and [https://quicklicensemanager.com](<https://quicklicensemanager.com> "target=\"\_blank\"") (for our license server), and and [https://github.com](<https://github.com> "target=\"\_blank\"") (for plugin downloads.)

&nbsp;


***
_Created with the Personal Edition of HelpNDoc: [Free Web Help generator](<https://www.helpndoc.com>)_
