# Vulnerabilities

We commit to acknowledging vulnerability reports within 5 business days, and addressing them as soon as we are able to. We will publish the results in the form of security advisories in this vulnerability page.

&nbsp;

&nbsp;

**\[19-Jul-2025\] [**NPM package 'is' CVE-2025-54313](<https://www.cve.org/CVERecord?id=CVE-2025-54313> "target=\"\_blank\"")

The popular NPM package 'is' has been compromised in a supply chain attack that injected backdoor malware, giving attackers full access to compromised devices.&nbsp; More details are available in [this article](<https://www.bleepingcomputer.com/news/security/npm-package-is-with-28m-weekly-downloads-infected-devs-with-malware/> "target=\"\_blank\"").

&nbsp;

While Hackolade uses NPM, this vulnerability does not affect our product.&nbsp; First because none of the infected libraries or libraries with infected dependencies are used in Hackolade Studio or its plugins, or in Hackolade Model Hub.&nbsp; But also because, if used in dev dependencies, we do not use any of the versions infected.

&nbsp;

&nbsp;

**\[12-Aug-2022\] [**Chromium CVE-2022-2162](<https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-2162> "target=\"\_blank\"")

We are aware of this vulnerability due to insufficient policy enforcement in the File System API of Google Chrome on Windows prior to 103.0.5060.53, allowing a remote attacker to bypass file system access via a crafted HTML page.&nbsp; Hackolade uses Electron, the open-source software framework developed and maintained by GitHub.&nbsp; Electron combines the Chromium rendering engine and the Node.js runtime. &nbsp;

&nbsp;

While Electron comes with Chromium built-in, it is not used as a regular browser.&nbsp; Meaning that the app is not loading random/potentially malicious html/js from the internet, but only static predefined content. &nbsp;

&nbsp;

Nevertheless, and as a precautionary measure, Hackolade Studio’s version 6.4.0 has been upgraded to a version of Electron that includes a backported fix to patch this vulnerability.&nbsp; Users of Hackolade Studio are encouraged to [upgrade](<https://hackolade.com/download.html>) to the latest version of Hackolade Studio, currently v6.4.0 or higher.

&nbsp;

&nbsp;

**\[08-Apr-22\] [**Chromium CVE-2022-1096 vulnerability](<https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-1096> "target=\"\_blank\"")

We are aware of this vulnerability due to [type confusion in V8](<https://chromereleases.googleblog.com/2022/03/stable-channel-update-for-desktop\_25.html> "target=\"\_blank\"").&nbsp; Hackolade uses Electron, the open-source software framework developed and maintained by GitHub, which is owned by Microsoft.&nbsp; Electron combines the Chromium rendering engine and the Node.js runtime.&nbsp; Chromium uses V8, Google's open source JavaScript engine.

&nbsp;

The technical details for this vulnerability are unknown and an exploit is not publicly available.&nbsp; While Electron comes with Chromium built-in, it is not used as a regular browser.&nbsp; Meaning that the app is not loading random/potentially malicious html/js from the internet, but only static predefined content. &nbsp;

&nbsp;

Nevertheless, and as a precautionary measure, Hackolade Studio’s current version 6 as well as the previous major version 5 have both been upgraded to a version of Electron that includes a [version of Chromium that officially patches this vulnerability](<https://github.com/electron/electron/pull/33472#issuecomment-1086399138> "target=\"\_blank\""). &nbsp; Users of Hackolade Studio are encouraged to [upgrade](<https://hackolade.com/download.html>) to the latest version of Hackolade Studio, currently v6.0.4 or higher, or v5.4.12 or higher.

&nbsp;

\
**\[13-Dec-21\] [**Log4j CVE-2021-44228 vulnerability](<https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44228> "target=\"\_blank\"")

We are aware of this vulnerability report. But Hackolade does not use Java. The application is written in JavaScript, Typescript, and ReactJS. This vulnerability does not affect us.

