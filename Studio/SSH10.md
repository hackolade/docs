# SSH

If your Teradata instance is located in the Cloud at Amazon Web Services RDS for example or Microsoft Azure, your preferred access to your instance will be over SSH through port 22.

&nbsp;

In the SSH tab, first check the box 'Use SSH tunnel' to enable the rest of the form:

&nbsp;

![Reverse-engineering PostgreSQL - SSH w Private Key](<lib/RE%20-%20MongoDB%20-%20SSH%20w%20Private%20Key.png>)

&nbsp;

Then fill in the fields:

&nbsp;

***SSH Address:*** IP address or DNS name of server in the cloud

&nbsp;

***Port:*** Tunnel port used for the SSH connection.&nbsp; This defaults to 22, the standard port for SSH.

&nbsp;

***SSH User Name:*** Username of the profile to log into on the remote system, for which you want to establish the SSH connection.

&nbsp;

***SSH Auth method:*** Choice between a Private key file (typically of extension .pem) or a Password

&nbsp;

***Private key:*** Identity file from which the identity (private key) for SSH public key authentication is read.

On OS X using OpenSSH, identity files are found in ~/.ssh. By default, the filenames of private keys are one of the following:

id\_dsa

id\_ecdsa,

id\_ed25519

id\_rsa

On Windows, the location of identify files depends on your choice of SSH client. PuTTY is one commonly used SSH client.

&nbsp;

***Passphrase:***&nbsp; Used to decrypt your private keys (stored in the specified identity file), providing an extra layer of security for an SSH connection. This field is not required.

&nbsp;

Or, if the SSH Auth Method is password:

***Client key password:*** Used to secure the SSH connection.&nbsp; This is required if you are not using an identity file.

&nbsp;

&nbsp;

![Reverse-engineering PostgreSQL - SSH w Password](<lib/RE%20-%20MongoDB%20-%20SSH%20w%20Password.png>)

&nbsp;

Consult [this page](<SSH-RSAkeyrejectedwithmessagenom.md>) if your SSH-RSA key rejected with message "no mutual signature algorithm"
