# Vulnerabilities

\[08-Apr-22\] [Chromium CVE-2022-1096 vulnerability](<https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-1096> "target=\"\_blank\"")

We are aware of this vulnerability due to [type confusion in V8](<https://chromereleases.googleblog.com/2022/03/stable-channel-update-for-desktop\_25.html> "target=\"\_blank\"").&nbsp; Hackolade uses Electron, the open-source software framework developed and maintained by GitHub.&nbsp; Electron combines the Chromium rendering engine and the Node.js runtime.&nbsp; Chromium uses V8, Google's open source JavaScript engine.

&nbsp;

The technical details for this vulnerability are unknown and an exploit is not publicly available.&nbsp; While Electron comes with Chromium built-in, it is not used as a regular browser.&nbsp; Meaning that the app is not loading random/potentially malicious html/js from the internet, but only static predefined content. &nbsp;

&nbsp;

Nevertheless, and as a precautionary measure, Hackolade Studio’s current version 6 as well as the previous major version 5 have both been upgraded to a version of Electron that includes a [version of Chromium that officially patches this vulnerability](<https://github.com/electron/electron/pull/33472#issuecomment-1086399138> "target=\"\_blank\""). &nbsp; Users of Hackolade Studio are encouraged to [upgrade](<https://hackolade.com/download.html>) to the latest version of Hackolade Studio, currently v6.0.4 or higher, or v5.4.12 or higher.

&nbsp;

\
\[13-Dec-21\] [Log4j CVE-2021-44228 vulnerability](<https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44228> "target=\"\_blank\"")

We are aware of this vulnerability report. But Hackolade does NOT use Java. The application is written in JavaScript. This vulnerability does not affect us.
