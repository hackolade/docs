# Network proxy

By default, Hackolade Studio accesses the Internet using the proxy settings from the PC's browser, as stored in Windows Internet Options \> Connections of the dialog c:\\Windows\\System32\\inetcpl.cpl&nbsp;

&nbsp;

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

![Proxy settings - automatic](<lib/Proxy%20settings%20-%20automatic.png>)

&nbsp;

&nbsp;

The following option should only be used if you knowingly handle proxy setup through HTTPS\_PROXY environment variables:

![Proxy settings - HTTPS\_PROXY environment var](<lib/Proxy%20settings%20-%20HTTPS\_PROXY%20environment%20var.png>)

&nbsp;

&nbsp;

If that fails, you should enter the hostname or IP address of the proxy server, and the appropriate port number.&nbsp; If the proxy server requires a user name and password, you may include your credentials as well:

&nbsp;

![Proxy settings -- manual](<lib/Proxy%20settings%20--%20manual.png>)

&nbsp;

If necessary, you may have to whitelist the domains: [https://hackolade.com](<https://hackolade.com> "target=\"\_blank\""), [https://quicklicensemanager.com](<https://quicklicensemanager.com> "target=\"\_blank\"") and [https://qlmdr.com](<https://qlmdr.com> "target=\"\_blank\"") (for our license servers), and and [https://github.com](<https://github.com> "target=\"\_blank\"") (for plugin downloads.)

&nbsp;

In particular, in environments with proxies using SSL inspection (Zscaler, BlueCoat, etc.) it is critical that Hackolade be whitelisted to connect properly with SSL/TLS protocols.

