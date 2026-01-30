# Error: EBUSY: resource busy or locked

If you get this error during installation of a plugin:

"stack": "Error: EBUSY: resource busy or locked, unlink...

&nbsp;

it generally indicates that a file or resource your process is trying to access is currently being used by another process, already locked, or is not available for the requested operation. This error is common when working with Node.js or related tooling, especially on Windows systems.\
 \
It is often caused by another process (including antivirus, cloud sync tools like OneDrive, or another shell/terminal) is using or locking the file or directory you are trying to read, write, or remove.\
 \
Can you please make sure that:

1. \- your folder C:\\Users\\%username% is not enabled to be synchronized with OneDrive, Dropbox, or other similar technology
1. \- your anti-virus allows our installation

 \
Then try to install the plugin again.\
 
