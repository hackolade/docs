# Linux

Hackolade Studio is a desktop application with a GUI. By default it requires a Desktop environment like Gnome, Mate, Xfce etc... Given the nature of Linux that is often used to run servers (especially on Cloud infrastructures), please note that it is also possible to only run Hackolade Studio in CLI mode even though a better solution might be to leverage our [Docker deployment](https://github.com/hackolade/docs/blob/0a59fff31d4ba35b7b64d924d5a534e9f96d1d26/Studio/Dockercontainer.md) for that purpose.

&nbsp;

> [!NOTE]
> You must be aware that the installation of the software is a tacit acceptance of our [Terms and Conditions and End-User License Agreement](<https://hackolade.com/eulas.html> "target=\"_blank\"").

&nbsp;

The application is shipped as a .zip file. To install, you simply unzip the file in the folder of your choice, then start the executable.\
The application can be run from the terminal or from a script by terminal:\
/path/to/unzipped/folder/Hackolade

&nbsp;

## Installation

### Pre-requisites

Hackolade Studio requires some packages to be installed on your system to run properly.

&nbsp;

#### On Red Hat / Fedora / Centos / Amazon Linux (and other RPM packaging based Linux distributions)

The following .rpm packages need to be installed:

&nbsp;

```bash
yum install at-spi2-atk cups-libs libdrm libgbm gtk3 alsa-lib libsecret
```

&nbsp;

#### On Ubuntu / Debian (and other Deb packaging based Linux distributions)

The following .deb packages need to be installed

&nbsp;

```bash
apt-get install \
    libgbm1 \
```

&nbsp;

libglib2.0-0 \\\
libgtk-3-0 \\\
libkrb5-3 \\\
libnss3 \\\
libnss-wrapper \\\
libsecret-1-0 \\\
libssl-dev

&nbsp;

#### On servers

If you want to run Hackolade only in cli on a server without a GUI environment installed you'll still require some more tooling:\
yum install Xvfb\
or\
apt-get install xvfb

&nbsp;

### Download and Installation

Download the [latest release](https://s3-eu-west-1.amazonaws.com/hackolade/current/Hackolade-linux-x64.zip). Both the zip file and 256-SHA checksum file must be downloaded int he same folder

&nbsp;

```bash
wget https://s3-eu-west-1.amazonaws.com/hackolade/current/Hackolade-linux-x64.zip
wget https://s3-eu-west-1.amazonaws.com/hackolade/current/Hackolade-linux-x64.SHASUM256.txt.asc
```

&nbsp;

Then unzip:

&nbsp;

```bash
unzip Hackolade-linux-x64.zip
rm Hackolade-linux-x64.zip
cd Hackolade-linux-x64
```

&nbsp;

*Notice*: File “chrome-sandbox” must be owned by root user and have permissions 4755.

&nbsp;

```bash
sudo chown root:root chrome-sandbox
sudo chmod 4755 chrome-sandbox
```

&nbsp;

The application must be executed by a non-root user.

&nbsp;

To verify the the archive integrity, use the command below:

&nbsp;

```bash
$ sha256sum -c Hackolade-linux-x64.SHASUM256.txt.asc
```

&nbsp;

You should get the response:

&nbsp;

```text
Hackolade-linux-x64.zip: OK
```

&nbsp;

### Start application

#### With a Desktop GUI environment

You just have to execute in the terminal. The application can be run from the terminal or from a script by terminal from the extracted folder /path/to/unzipped/folder/Hackolade

&nbsp;

```bash
./Hackolade --help
```

&nbsp;

#### On a server with XVFB

```bash
xvfb-run ./Hackolade --help
```

&nbsp;

## FAQ

### Unable to run on AWS Amazon Linux 2

Hackolade is an Electron application that has components that are incompatible with Amazon Linux 2. We advise you to use EC2 instances running Amazon Linux 3 AMI instead.

&nbsp;

### Unable to run from File Manager

Unfortunately, the issue with running executable file from the file manager still is not resolved: [electron/electron#15406](https://github.com/electron/electron/issues/15406)

&nbsp;

### How to create a Desktop file for easier access

To workaround the previous issue or ease your user life you can create a desktop file to launch the application: [https://stackoverflow.com/questions/55060402/electron-executable-not-recognized-by-nautilus](https://stackoverflow.com/questions/55060402/electron-executable-not-recognized-by-nautilus)\
Create a file called myapp.desktop with the following contents.\\\
\[Desktop Entry\]\
Name=My Application\
Exec=/path/to/binary\
Terminal=false\
Type=Application\
StartupNotify=true\
Encoding=UTF-8\
Then, mark the desktop file executable by issuing chmod +x myapp.desktop. Double clicking the file should launch the application as expected.

&nbsp;

**Run Hackolade over remote connection**\
In case of remote connection, you need VNC server: [https://wiki.centos.org/HowTos/VNC-Server](https://wiki.centos.org/HowTos/VNC-Server)

&nbsp;

## CentOS 7 with no GUI

For CentOS 7 if [GUI was not selected](<https://www.techrepublic.com/article/how-to-install-a-gui-on-top-of-centos-7/> "target=\"_blank\"") during installation, a complex procedure is documented below:

&nbsp;

### Pre-requisites

*sudo yum update*\
*sudo yum install gcc `gcc-c++ `kernel-devel make bzip2 clang dbus-devel gtk3-devel \\*

&nbsp;

```bash
libgnome-keyring-devel xorg-x11-server-utils libcap-devel \
cups-devel libXtst-devel alsa-lib-devel libXrandr-devel \
nss-devel libsecret-devel libnotify-devel wget unzip
```

&nbsp;

Copy and replace [file](<https://drive.google.com/file/d/17aJr9wHbl_xPtCZpyM7xygiObC7lzHTB/view?usp=sharing> "target=\"_blank\"") in the directory ([link](<https://drive.google.com/file/d/17aJr9wHbl_xPtCZpyM7xygiObC7lzHTB/view?usp=sharing> "target=\"_blank\"")):\
*/lib64/libstdc++.so.6*\
[https://drive.google.com/file/d/17aJr9wHbl_xPtCZpyM7xygiObC7lzHTB/view?usp=sharing](<https://drive.google.com/file/d/17aJr9wHbl_xPtCZpyM7xygiObC7lzHTB/view?usp=sharing> "target=\"_blank\"")

&nbsp;

*sudo yum groupinstall “GNOME Desktop”*\
*echo "exec gnome-session" >> ~/.xinitrc*

&nbsp;

Starting GNOME:\
*startx*

&nbsp;

*Notice*: you should start GNOME by a non-root user\
[https://www.techrepublic.com/article/how-to-install-a-gui-on-top-of-centos-7/](<https://www.techrepublic.com/article/how-to-install-a-gui-on-top-of-centos-7/> "target=\"_blank\"")

&nbsp;

### Installation

*wget “*[*https://s3-eu-west-1.amazonaws.com/hackolade/current/Hackolade-linux-x64.zip*](<https://s3-eu-west-1.amazonaws.com/hackolade/current/Hackolade-linux-x64.zip> "target=\"_blank\"")*” -O hackolade.zip*\
*unzip hackolade.zip*\
*rm hackolade.zip*

&nbsp;

*cd Hackolade-linux-x64*\
*chown root:root chrome-sandbox*\
*chmod 4755 chrome-sandbox*

&nbsp;

*Notice*:\
File “chrome-sandbox” must be owned by root user and have permissions 4755.

&nbsp;

The application must be executed by a non-root user.
