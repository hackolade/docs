# Vulnerabilities

We commit to acknowledging vulnerability reports within 5 business days, and addressing them as soon as we are able to. We publish the results in the form of security advisories in this vulnerability page.

&nbsp;

**\[22-Oct-26\]** [NodeJS vulnerability Out-of-Bounds Write in Google Brotli Decoder](<https://nvd.nist.gov/vuln/detail/cve-2026-111497> "target=\"_blank\"")\
Node.js shipped a security update for a flaw in how it decompresses Brotli data, a bug people are already calling Node2Shell (CVE-2026-111497). If an attacker can get a malicious payload in front of your app, the flaw can crash the process, leak part of its memory, or potentially let them run their own code.

&nbsp;

Who is affected: anyone running [Node.js](<https://nodejs.org/> "target=\"_blank\"") whose app decompresses Brotli data that an attacker could control.

&nbsp;

This vulnerability does not affect our product. Hackolade uses Electron, the open-source software framework developed and maintained by GitHub. While Electron combines the Node.js runtime, the app is not loading random/potentially malicious payloads from the internet, but only static predefined content, and in controlled use cases.

&nbsp;

No publicly available exploit code exists for the CVE-2026-111497 vulnerability.

&nbsp;

Nevertheless, and as a precautionary measure, we will upgrade our Electron version as soon as they publish one with the latest NodeJS security update.

&nbsp;

**\[21-Oct-2026\]** [Critical Vulnerabilities in PHP](<https://cert.europa.eu/publications/security-advisories/2026-018/> "target=\"_blank\"")\
On 20 October 2026, the PHP project announced an upcoming security release addressing two critical vulnerabilities in PHP. Public reports indicated that these vulnerabilities could lead to remote code execution.

&nbsp;

The PHP team released the fixes on 21 October 2026 at 13:30 UTC, in PHP versions 8.5.12, 8.4.27, 8.3.36 and 8.2.35. Both vulnerabilities can allow unauthenticated remote code execution.

&nbsp;

There is not a line of PHP being used at Hackolade. Not on our website. Not in any of products.

&nbsp;

**\[18-May-26\]** [Popular node-ipc npm Package Infected with Credential Stealer](<https://socket.dev/blog/node-ipc-package-compromised> "target=\"_blank\"")\
Early analysis indicates that node-ipc@9.1.6, node-ipc@9.2.3, and node-ipc@12.0.1 contain obfuscated stealer/backdoor behavior. The malware appears to fingerprint the host environment, enumerate and read local files, compress and chunk collected data, wrap the payload in a cryptographic envelope, and attempt exfiltration through a network endpoint selected via DNS/address logic.

&nbsp;

While Hackolade uses the node-ipc library, versions are pinned down, and we never downloaded or used the compromised versions.

&nbsp;

**\[13-May-26\]** [TanStack npm Packages Compromised in Ongoing Mini Shai-Hulud Supply-Chain Attack](<https://socket.dev/blog/tanstack-npm-packages-compromised-mini-shai-hulud-supply-chain-attack> "target=\"_blank\"")\
Socket detected 84 compromised TanStack npm package artifacts modified with suspected CI credential-stealing malware.

&nbsp;

While Hackolade uses the TanStack library, versions are pinned down, and we never downloaded or used the compromised versions.

&nbsp;

Besides, all our developers are equipped with the [Socket Firewall](<https://docs.socket.dev/docs/socket-firewall-overview> "target=\"_blank\"") intelligent proxy. And all packages had flagged by Socket AI Scanner in six minutes or less after publication.

&nbsp;

**\[30-Mar-26\]** [Compromised NPM package Axios](<https://www.stepsecurity.io/blog/axios-compromised-on-npm-malicious-versions-drop-remote-access-trojan> "target=\"_blank\"")\
Compromised versions of axios (1.14.1 and 0.30.4), a widely used JavaScript package were published to NPM. The affected versions inject the malicious dependency plain-crypto-js@4.2.1. This deployed a cross-platform remote access trojan (RAT) which allows attackers to remotely execute code on affected Windows, MacOS, and Linux devices and take full control of the system.

&nbsp;

While Hackolade uses the axios library, versions are pinned down, and we never downloaded or used the compromised versions.

&nbsp;

Note also that each developer workstation is equipped with the [Socket Firewall](<https://docs.socket.dev/docs/socket-firewall-overview> "target=\"_blank\"") intelligent proxy to provide real-time protection against software supply chain threats at the point of dependency usage. And also that each software build is accompanied by the generation of a comprehensive Software Bill of Materials (SBOM), providing full visibility into all included third-party and open-source components. This SBOM is systematically analyzed using [Aqua Security Trivy](<https://www.aquasec.com/products/trivy/> "target=\"_blank\"") to identify known vulnerabilities across dependencies and the software supply chain. The build pipeline enforces strict security gates: if any vulnerability exceeding defined risk thresholds is detected, the build is blocked from release until the issue is remediated or formally risk-accepted. This approach ensures continuous assurance of component integrity and prevents the introduction of known supply chain risks into distributed software artifacts.

&nbsp;

**\[05-Dec-25\]** [React2Shell affecting server-side use of React.js](<https://react2shell.com/> "target=\"_blank\"")\
This critical severity vulnerability affects server-side use of React.js, tracked as [CVE-2025-55182](https://react.dev/blog/2025/12/03/critical-security-vulnerability-in-react-server-components) in React.js and [CVE-2025-66478](https://github.com/vercel/next.js/security/advisories/GHSA-9qr9-h5gf-34mp) specifically for the Next.js framework.

&nbsp;

While Hackolade uses ReactJS, we do not use it for server-side rendering. We do not use react-server-... components. And we do not use the ReactJS versions impacted.

&nbsp;

**\[05-Dec-25\]** [interpretation-conflict (CWE-436) vulnerability in node-forge versions 1.3.1 and earlier (CVE-2025-12816)](<https://nvd.nist.gov/vuln/detail/CVE-2025-12816> "target=\"_blank\"")\
This vulnerability in node-forge versions 1.3.1 and earlier would enable man-in-the-middle attackers to craft ASN.1 structures to desynchronize schema validations, yielding a semantic divergence that may bypass downstream cryptographic verifications and security decisions.

&nbsp;

No publicly available exploit code exists for node-forge's CVE-2025-12816 vulnerability. Security advisories and reports confirm that researcher Hunter Wodzenski from Palo Alto Networks provided a proof-of-concept (PoC) internally during responsible disclosure, but it has not been released publicly. No GitHub repositories, exploit-db entries, or public PoCs were found across vulnerability databases like NVD, OSV, or CERT/CC. Hackolade Studio Desktop v8.7.2 and above run more recent versions of the library than those affected by this vulnerability.

&nbsp;

**\[16-Sept-2025\]** [Supply Chain Attack Targets CrowdStrike npm Packages](<https://socket.dev/blog/ongoing-supply-chain-attack-targets-crowdstrike-npm-packages> "target=\"_blank\"")\
Multiple CrowdStrike npm packages published by the [**crowdstrike-publisher**](<https://socket.dev/npm/user/crowdstrike-publisher> "target=\"_blank\"") npm account were compromised. This looks like a continuation of the ongoing malicious supply chain campaign known as the “Shai-Halud attack”.

&nbsp;

While Hackolade uses NPM, this vulnerability does not affect our product. We have promptly confirmed that none of the compromised dependencies have been used in Hackolade Studio or its plugins, or in Hackolade Model Hub.

&nbsp;

**\[08-Sept-2025\]** [npm Author Qix Compromised via Phishing Email in Major Supply Chain Attack](<https://socket.dev/blog/npm-author-qix-compromised-in-major-supply-chain-attack> "target=\"_blank\"")\
Socket has detected a supply chain attack targeting the NPM ecosystem. The account of prolific maintainer **Qix** has been compromised, and attackers have already published malicious versions of widely used packages. A list of package versions have been confirmed as malicious.

&nbsp;

While Hackolade uses NPM, this vulnerability does not affect our product. We have promptly confirmed that none of the compromised dependencies have been used in Hackolade Studio or its plugins, or in Hackolade Model Hub.

&nbsp;

**\[19-Jul-2025\]** [NPM package 'is' CVE-2025-54313](<https://www.cve.org/CVERecord?id=CVE-2025-54313> "target=\"_blank\"")\
The popular NPM package 'is' has been compromised in a supply chain attack that injected backdoor malware, giving attackers full access to compromised devices. More details are available in [this article](<https://www.bleepingcomputer.com/news/security/npm-package-is-with-28m-weekly-downloads-infected-devs-with-malware/> "target=\"_blank\"").

&nbsp;

While Hackolade uses NPM, this vulnerability does not affect our product. First because none of the infected libraries or libraries with infected dependencies are used in Hackolade Studio or its plugins, or in Hackolade Model Hub. But also because, if used in dev dependencies, we do not use any of the versions infected.

&nbsp;

**\[12-Aug-2022\]** [Chromium CVE-2022-2162](<https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-2162> "target=\"_blank\"")\
We are aware of this vulnerability due to insufficient policy enforcement in the File System API of Google Chrome on Windows prior to 103.0.5060.53, allowing a remote attacker to bypass file system access via a crafted HTML page. Hackolade uses Electron, the open-source software framework developed and maintained by GitHub. Electron combines the Chromium rendering engine and the Node.js runtime.

&nbsp;

While Electron comes with Chromium built-in, it is not used as a regular browser. Meaning that the app is not loading random/potentially malicious html/js from the internet, but only static predefined content.

&nbsp;

Nevertheless, and as a precautionary measure, Hackolade Studio’s version 6.4.0 has been upgraded to a version of Electron that includes a backported fix to patch this vulnerability. Users of Hackolade Studio are encouraged to [upgrade](https://hackolade.com/download.html) to the latest version of Hackolade Studio, currently v6.4.0 or higher.

&nbsp;

**\[08-Apr-22\]** [Chromium CVE-2022-1096 vulnerability](<https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-1096> "target=\"_blank\"")\
We are aware of this vulnerability due to [type confusion in V8](<https://chromereleases.googleblog.com/2022/03/stable-channel-update-for-desktop_25.html> "target=\"_blank\""). Hackolade uses Electron, the open-source software framework developed and maintained by GitHub, which is owned by Microsoft. Electron combines the Chromium rendering engine and the Node.js runtime. Chromium uses V8, Google's open source JavaScript engine.

&nbsp;

The technical details for this vulnerability are unknown and an exploit is not publicly available. While Electron comes with Chromium built-in, it is not used as a regular browser. Meaning that the app is not loading random/potentially malicious html/js from the internet, but only static predefined content.

&nbsp;

Nevertheless, and as a precautionary measure, Hackolade Studio’s current version 6 as well as the previous major version 5 have both been upgraded to a version of Electron that includes a [version of Chromium that officially patches this vulnerability](<https://github.com/electron/electron/pull/33472#issuecomment-1086399138> "target=\"_blank\""). Users of Hackolade Studio are encouraged to [upgrade](https://hackolade.com/download.html) to the latest version of Hackolade Studio, currently v6.0.4 or higher, or v5.4.12 or higher.

&nbsp;

**\[13-Dec-21\]** [Log4j CVE-2021-44228 vulnerability](<https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44228> "target=\"_blank\"")\
We are aware of this vulnerability report. But Hackolade does not use Java. The application is written in JavaScript, Typescript, and ReactJS. This vulnerability does not affect us.
