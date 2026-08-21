# Network proxy

By default, Hackolade Studio accesses the Internet using the proxy settings from the PC's browser, as stored in Windows Internet Options \> Connections of the dialog c:\\Windows\\System32\\inetcpl.cpl&nbsp;

&nbsp;

If you have an HTTP proxy server on your network, you may have to manually set in the application the proxy parameters with the hostname or IP address of the proxy server.

&nbsp;

You may enter this info via the menu Tools \> Options \> Network Proxy.&nbsp; Access is allowed, even if the license software key is not yet activated.

&nbsp;

Proxy configuration can be achieved in 4 different ways:

&#49;) using your system or browser config (preferred method, requiring no special changes in Hackolade);

&#50;) using HTTPS\_PROXY environment variables you may have used for your proxy settings

&#51;) using a Proxy Configuration (.pac) file accessed via a URL provided by your network administrator

&#52;) manually entering proxy address/port and possible username/password

&nbsp;

&nbsp;

The default setting is to use the proxy setting from you system/browser:

![Proxy settings - automatic](<lib/Proxy settings - automatic.png>)

&nbsp;

&nbsp;

The HTTPS\_PROXY option should only be used if you knowingly handle proxy setup through HTTPS\_PROXY environment variables.

&nbsp;

In some cases, your network administrator may have created an automatic proxy configuration (.pac) file and made it available via a URL address.

![Proxy settings - proxy auto config file](<lib/Proxy settings - proxy auto config file.png>)

&nbsp;

&nbsp;

Finally, it is possible to enter the hostname or IP address of the proxy server, and the appropriate port number.&nbsp; If the proxy server requires a user name and password, you may include your credentials as well:

![Proxy settings - manual](<lib/Proxy settings - manual.png>)

&nbsp;

&nbsp;

&nbsp;

## Zscaler proxy troubleshooting

**Important:** the following domains must be whitelisted: [https://hackolade.com](<https://hackolade.com> "target=\"\_blank\""),&nbsp; [https://quicklicensemanager.com](<https://quicklicensemanager.com/> "target=\"\_blank\""), [https://qlmdr.com](<https://qlmdr.com> "target=\"\_blank\""), and [https://github.com/hackolade](<https://github.com/hackolade> "target=\"\_blank\"")

&nbsp;

**Warning:** if you have an HTTP proxy server on your network, you may have to manually set in the application the proxy parameters.&nbsp; You will find more information on the [Network Proxy page](<Networkproxy.md>).&nbsp; In particular, in environments with proxies using SSL inspection (Zscaler, BlueCoat, etc.) it is critical that Hackolade Studio be whitelisted to connect properly with SSL/TLS protocols.

&nbsp;

If your organization uses a ZScaler proxy which prevents license key validation, follow the steps below:

&nbsp;

### Step-by-Step Configuration in Zscaler Internet Access (ZIA)

&nbsp;

1. **Log in to Zscaler Admin Portal**

   * URL: **https://admin.zscaler.com** (or your organization's ZIA portal)
   * Navigate to: **Authentication/SSL Policy** → **SSL Policy**

1. **Create a New SSL Decryption Rule**

   * Click **Add SSL Decryption Rule** (or **Add Rule**)

1. **Configure Rule Settings**

| **Field** | **Value** |
| --- | --- |
| **Rule Name** | Skip SSL Decryption - **Hackolade Studio** |
| **Action** | **Skip Decryption** (or **Bypass SSL Inspection**) |
| **Users/Groups** | Select applicable users (or **All Users**) |
| **Locations** | Select applicable locations (or **All Locations**) |
| **URLs** | Add domains: [https://hackolade.com](<https://hackolade.com> "target=\"\_blank\""),&nbsp; [https://quicklicensemanager.com](<https://quicklicensemanager.com/> "target=\"\_blank\""), [https://qlmdr.com](<https://qlmdr.com> "target=\"\_blank\""), and [https://github.com/hackolade](<https://github.com/hackolade> "target=\"\_blank\"") |
| **URL Categories** | (Optional) Select **Business and Industry** |
| **Priority** | Set to **High** (above general decryption rules) |


4. **Save and Deploy**
- &nbsp;

  - Click Save
  - Deploy the policy to apply changes

&nbsp;

&nbsp;

### Process-Based Bypass (Zscaler Client Connector)

If your organization uses **Zscaler Client Connector (ZCC)** with process-based policies:

1. Navigate to: **Client Connector Policy** → **Application Bypass/Exclusion**
1. Add your app's executable:

| **Field** | **Value** |
| --- | --- |
| **Process Name** | Hackolade.exe (Windows) or Hackolade (macOS/Linux) |
| **Action** | **Bypass Proxy** or **Exclude from Inspection** |
| **Path** | Full path to executable (e.g., C:\\Program Files\\Hackolade\\Hackolade.exe) |


3. **Save** and **Deploy**

&nbsp;

&nbsp;

