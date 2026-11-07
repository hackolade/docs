---
description: Connect Hackolade Studio to a Cassandra instance on AWS, Azure or elsewhere through an SSH tunnel on port 22.
seoTitle: Connect to Cassandra through an SSH tunnel
image: lib/Cassandra connection settings.png
---
# SSH

If your Cassandra instance is located in the Cloud at Amazon Web Services for example or Microsoft Azure, your preferred access to your instance will be over SSH through port 22.

In the Connection tab, there are 3 fields:\
***Name:*** enter the name you want to give to the connection.\
***Address:*** in this case, this field should be 'localhost' that will be tunneled via SSH to the actual server\
***Port***: the port number of the Cassandra instance

![Cassandra connection settings](<lib/Cassandra connection settings.png>)

In the SSH tab, first check the box 'Use SSH tunnel' to enable the rest of the form:

![Reverse-engineering Cassandra - SSH w Private Key](<lib/RE - MongoDB - SSH w Private Key.png>)

Then fill in the fields:

***SSH Address:*** IP address or DNS name of server in the cloud

***Port:*** Tunnel port used for the SSH connection. This defaults to 22, the standard port for SSH.

***SSH User Name:*** Username of the profile to log into on the remote system, for which you want to establish the SSH connection.

***SSH Auth method:*** Choice between a Private key file (typically of extension .pem) or a Password

***Private key:*** Identity file from which the identity (private key) for SSH public key authentication is read.\
On OS X using OpenSSH, identity files are found in ~/.ssh. By default, the filenames of private keys are one of the following:\
id_dsa\
id_ecdsa,\
id_ed25519\
id_rsa\
On Windows, the location of identify files depends on your choice of SSH client. PuTTY is one commonly used SSH client.

***Passphrase:*** Used to decrypt your private keys (stored in the specified identity file), providing an extra layer of security for an SSH connection. This field is not required.

Or, if the SSH Auth Method is password:\
***Client key password:*** Used to secure the SSH connection. This is required if you are not using an identity file.

![Reverse-engineering Cassandra- SSH w Password](<lib/RE - MongoDB - SSH w Password.png>)

Consult [this page](SSH-RSAkeyrejectedwithmessagenom.md) if your SSH-RSA key rejected with message "no mutual signature algorithm"
