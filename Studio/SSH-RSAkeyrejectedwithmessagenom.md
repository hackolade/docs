# SSH-RSA key rejected with message "no mutual signature algorithm"

The RSA SHA-1 hash algorithm is being quickly deprecated across operating systems and SSH clients because of various security vulnerabilities, with many of these technologies now outright denying the use of this algorithm.

&nbsp;

In the event that you are using an operating system or SSH client whose version has this algorithm disabled, it's possible that any SSH keys previously generated using this algorithm will no longer be accepted by these technologies. 

&nbsp;

When attempting to use an SSH key generated using the ssh-rsa sha-1 hash algorithm, the SSH key isn't accepted (the user receives a '**Permission denied**' message)

&nbsp;

Users must generate a key with another algorithm.

To generate a key using this updated algorithm, it's recommended that you consult the documentation for the usual software that your team uses for SSH key generation.

For OpenSSH's **ssh-keygen** command in particular, the full list of algorithms for this command can be found [on SSH.com: choosing an algorithm](<https://www.ssh.com/ssh/keygen/#choosing-an-algorithm-and-key-size> "target=\"\_blank\""). In addition, here is an example command that creates a new SSH key using the ED25519 algorithm:

ssh-keygen -t ed25519 -C "your\_email@example.com"

&nbsp;

When configuring your connection settings in Hackolade, use "~/.ssh/id\_ed25519" as private key

