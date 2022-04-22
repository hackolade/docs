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

&nbsp;

&nbsp;

## Why aren't physically-local attacks in Hackolade Studio's threat model?

The answer is greatly inspired by Google's [position for Chrome](<https://chromium.googlesource.com/chromium/src/%20/master/docs/security/faq.md#Why-arent-physically\_local-attacks-in-Chromes-threat-model> "target=\"\_blank\"").

&nbsp;

Could an attacker compromise Hackolade Studio and steal connections settings to the databases?&nbsp; We consider these attacks outside Hackolade Studio's threat model, because there is no way for Hackolade Studio (or any application) to defend against a malicious user who has managed to log into your device as you, or who can run software with the privileges of your operating system user account.&nbsp; Such an attacker can modify executables and DLLs, change environment variables like PATH, change configuration files, read any data your user account owns, email it to themselves, and so on.&nbsp; Such an attacker has total control over your device, and nothing Hackolade Studio can do would provide a serious guarantee of defense. This problem is not special to Hackolade Studio — all applications must trust the physically-local user.

There are a few things you can do to mitigate risks from people who have physical control over **your** computer, in certain circumstances.

* Take advantage of your operating system’s screen lock feature.
* If you share your computer with other people, take advantage of your operating system’s ability to manage multiple login accounts, and use a distinct account for each person.&nbsp;
* To stop people from reading your data in cases of device theft or loss, use full disk encryption (FDE). FDE is a standard feature of most operating systems, including Windows Vista and later, Mac OS X Lion and later, and some distributions of Linux. (Some older versions of Mac OS X had partial disk encryption: they could encrypt the user’s home folder, which contains the bulk of a user’s sensitive data.) Some FDE systems allow you to use multiple sources of key material, such as the combination of both a password and a key file on a USB token. When available, you should use multiple sources of key material to achieve the strongest defense. Chrome OS encrypts users’ home directories.

&nbsp;

## What about unmasking of passwords in Connection Settings?

This is just one of the physically-local attacks described in the previous section, and all of those points apply here as well.&nbsp; The reason the password is masked is only to prevent disclosure via “shoulder-surfing” (i.e. the passive viewing of your screen by nearby persons), not because it is a secret unknown to the application. The application knows the password at many layers, including JavaScript, developer tools, process memory, and so on.&nbsp; When you are physically local to the computer, and only when you are physically local to the computer, there are, and always will be, tools for extracting the password from any of these places.

