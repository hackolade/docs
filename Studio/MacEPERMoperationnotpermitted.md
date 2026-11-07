---
description: 'Grant Hackolade Studio access to your Documents folder on macOS to fix the "EPERM: operation not permitted" error.'
seoTitle: "Mac EPERM: operation not permitted"
image: lib/Mac Catalina Security Privacy.png
---
# Mac EPERM: operation not permitted

Starting with the release of macOS 10.15 Catalina, Apple has introduced a new security feature that ensures that 3rd-party applications are manually granted access to the user's file. Hackolade stores settings and logs in your Documents folder, and it cannot operate without it. So, if prompted with this dialog, you must click OK.\
![Mac - access to Documents folder](<lib/Mac Catalina - access to Documents folder.png>)

You may still manage this grant if needed in Security & Privacy:\
![Mac Security Privacy](<lib/Mac Catalina Security Privacy.png>)

To avoid the error "EPERM: operation not permitted", you must grant access to the application as described above.
