# Linux

Hackolade is a desktop application with a GUI.  By default it requires a Desktop environment like Gnome, Mate, Xfce etc...
Given the nature of Linux that is often used to run servers (especially on Cloud infrastructures), please note that it is also possible to only run Hackolade in CLI mode even though a better solution might be to leverage our [Docker deployment](../Studio/Dockercontainer.md) for that purpose.

## Installation

### Pre-requisites

Hackolade requires some packages to be installed on your system to run properly.

#### On Red Hat / Fedora / Centos / Amazon Linux (and other RPM packaging based Linux distributions)

The following .rpm packages need to be installed:

```bash
    yum install at-spi2-atk cups-libs libdrm libgbm gtk3 alsa-lib libsecret
```

#### On Ubuntu / Debian (and other Deb packaging based Linux distributions)

The following .deb packages need to be installed
```bash
    apt-get install \
        libgbm1 \
		libglib2.0-0 \
		libgtk-3-0 \
		libkrb5-3 \
		libnss3 \
		libnss-wrapper \
		libsecret-1-0 \
		libssl-dev
```

##### On servers

If you want to run Hackolade only in cli on a server without a GUI environment installed you'll still require some more tooling:

```bash
   yum install Xvfb
```
or
```bash
   apt-get install xvfb
```

### Installation

Download the [latest release](<https://s3-eu-west-1.amazonaws.com/hackolade/current/Hackolade-linux-x64.zip> "target=\"\_blank\"")
```bash
    wget https://s3-eu-west-1.amazonaws.com/hackolade/current/Hackolade-linux-x64.zip
```

Then unzip:
```bash
    unzip hackolade.zip
    rm hackolade.zip
    cd Hackolade-linux-x64
```
&nbsp;

*Notice*:
File “chrome-sandbox” must be owned by root user and have permissions 4755.

```bash
    sudo chown root:root chrome-sandbox
    sudo chmod 4755 chrome-sandbox
```

&nbsp;

The application must be executed by a non-root user.

### Start application

#### With a Desktop GUI environment

You just have to execute in the terminal.
The application can be run from the terminal or from a script by terminal from the extracted folder `/path/to/unzipped/folder/Hackolade`
&nbsp;

```bash
    ./Hackolade --help
```

#### On a server with XVFB

```bash
    xvfb-run ./Hackolade --help
```

## FAQ

### Unable to run from File Manager

Unfortunately, the issue with running executable file from the file manager still is not resolved:\
[https://github.com/electron/electron/issues/15406](<https://github.com/electron/electron/issues/15406> "target=\"\_blank\"")

### How to reate a Desktop file for easier access

To workaround the previous issue or ease your user life you can create a desktop file to launch the application:\
[https://stackoverflow.com/questions/55060402/electron-executable-not-recognized-by-nautilus](<https://stackoverflow.com/questions/55060402/electron-executable-not-recognized-by-nautilus> "target=\"\_blank\"")\
\
Create a file called myapp.desktop with the following contents.\

```
[Desktop Entry]
Name=My Application
Exec=/path/to/binary
Terminal=false
Type=Application
StartupNotify=true
Encoding=UTF-8
```

Then, mark the desktop file executable by issuing `chmod +x myapp.desktop`.&nbsp; Double clicking the file should launch the application as expected.

### Run Hackolade over remote connection

In case of remote connection, you need VNC server:

[https://wiki.centos.org/HowTos/VNC-Server](<https://wiki.centos.org/HowTos/VNC-Server> "target=\"\_blank\"")
