# Linux

## Standard installation ##

The application is shipped as a .zip file.&nbsp; To install, you simply unzip the file in the folder of your choice, then start the executable.&nbsp; You must be aware that the installation of the software is a tacit acceptance of our [Terms and Conditions and End-User License Agreement](<https://hackolade.com/eulas.html> "target=\"\_blank\"").&nbsp;

&nbsp;

Unfortunately, the issue with running executable file from the file manager still is not resolved:\
[https://github.com/electron/electron/issues/15406](<https://github.com/electron/electron/issues/15406> "target=\"\_blank\"")\
The Linux version can be run from the terminal or from a script by terminal:\
/path/to/unzipped/folder/Hackolade\
\
Also, there is a way to create a desktop file to launch the application:\
[https://stackoverflow.com/questions/55060402/electron-executable-not-recognized-by-nautilus](<https://stackoverflow.com/questions/55060402/electron-executable-not-recognized-by-nautilus> "target=\"\_blank\"")\
\
Create a file called myapp.desktop with the following contents.\
\
\[Desktop Entry\]\
Name=My Application\
Exec=/path/to/binary\
Terminal=false\
Type=Application\
StartupNotify=true\
Encoding=UTF-8\
\
Then, mark the desktop file executable by issuing chmod +x myapp.desktop. Double clicking the file should launch the application as expected.

&nbsp;

&nbsp;

For CentOS 7 if [GUI was not selected](<https://www.techrepublic.com/article/how-to-install-a-gui-on-top-of-centos-7/> "target=\"\_blank\"") during installation, a complex procedure is documented below:

### Pre-requisites ###

*sudo yum update*

*sudo yum install gcc gcc-c++ kernel-devel make bzip2 clang dbus-devel gtk3-devel \\ *

                   *libgnome-keyring-devel xorg-x11-server-utils libcap-devel \\*

                   *cups-devel libXtst-devel alsa-lib-devel libXrandr-devel \\*

                   *nss-devel libsecret-devel libnotify-devel wget unzip*

&nbsp;

Copy and replace [file](<https://drive.google.com/file/d/17aJr9wHbl\_xPtCZpyM7xygiObC7lzHTB/view?usp=sharing> "target=\"\_blank\"") in the directory ([link](<https://drive.google.com/file/d/17aJr9wHbl\_xPtCZpyM7xygiObC7lzHTB/view?usp=sharing> "target=\"\_blank\"")):

*/lib64/libstdc++.so.6*

[https://drive.google.com/file/d/17aJr9wHbl\_xPtCZpyM7xygiObC7lzHTB/view?usp=sharing](<https://drive.google.com/file/d/17aJr9wHbl\_xPtCZpyM7xygiObC7lzHTB/view?usp=sharing> "target=\"\_blank\"")

&nbsp;

*sudo yum groupinstall “GNOME Desktop”*

*echo "exec gnome-session" \>\> ~/.xinitrc*

&nbsp;

Starting GNOME:

*startx*

&nbsp;

*Notice*: you should start GNOME by a non-root user

[https://www.techrepublic.com/article/how-to-install-a-gui-on-top-of-centos-7/](<https://www.techrepublic.com/article/how-to-install-a-gui-on-top-of-centos-7/> "target=\"\_blank\"")

### Installation ###

*wget “[https://s3-eu-west-1.amazonaws.com/hackolade/current/Hackolade-linux-x64.zip*](<https://s3-eu-west-1.amazonaws.com/hackolade/current/Hackolade-linux-x64.zip> "target=\"\_blank\"")*” -O hackolade.zip*

*unzip hackolade.zip*

*rm hackolade.zip*

&nbsp;

*cd Hackolade-linux-x64 *

*chown root:root chrome-sandbox*

*chmod 4755 chrome-sandbox*

&nbsp;

*Notice*:

File “chrome-sandbox” must be owned by root user and have permissions 4755.

&nbsp;

The application must be executed by a non-root user.

### Start application ###

Execute in the terminal:

*./Hackolade*

&nbsp;

### Remote connection ###

In case of remote connection, you need VNC server:

[https://wiki.centos.org/HowTos/VNC-Server](<https://wiki.centos.org/HowTos/VNC-Server> "target=\"\_blank\"")

### Compiling GCC ###

If copying */lib64/libstdc++.so.6* didn’t help and you faced troubles with GLIBCXX you have to compile a newer version of GCC (it takes a while):

&nbsp;

*wget ftp://ftp.lip6.fr/pub/gcc/releases/gcc-7.5.0/gcc-7.5.0.tar.gz*

&nbsp;

*tar xzf gcc-7.5.0.tar.gz*

*cd gcc-7.5.0*

*./contrib/download\_prerequisites*

*cd ..*

*mkdir objdir*

*cd objdir*

*$PWD/../gcc-7.5.0/configure --prefix=$HOME/GCC-7.5.0 --enable-languages=c,c++,fortran,go --disable-multilib*

*make*

*make install*

&nbsp;

After compiling create a symlink to the file libstdc++.so.6.0.24:

&nbsp;

*sudo ln -s $HOME/GCC-7.5.0/lib64/libstdc++.so.6.0.24 /lib64/libstdc++.so.6 *

&nbsp;

[https://gcc.gnu.org/wiki/InstallingGCC](<https://gcc.gnu.org/wiki/InstallingGCC> "target=\"\_blank\"")

&nbsp;


***
_Created with the Personal Edition of HelpNDoc: [Full-featured EPub generator](<https://www.helpndoc.com/create-epub-ebooks>)_
