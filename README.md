qmenu
=====

Collection of tools that utilize
[dmenu](https://tools.suckless.org/dmenu/) to provide the user with a
drop down menu for [QubesOS](https://qubes-os.org/) R4.0+,
from which they can quickly administer their qube
preferences, firewall rules, applications, per-qube keyboard layouts, devices,
etc. with only the keyboard.

The colors that correspond to the qube label can be adjusted by creating a
text file called `qmenu.conf` in `/home/user/.config/` with
the following contents:

~~~
[LABEL 1]=#[HEX TRIPLET]
[LABEL 2]=#[HEX TRIPLET]
...
[LABEL 8]=#[HEX TRIPLET]
~~~

### qmenu-al ###

Launch domU applications.

    Usage: qmenu-al [OPTION] (--light-theme)

     --all
     --focused

### qmenu-dm ###

List and manage your connected devices.

    Usage: qmenu-dm [OPTION] (--light-theme)

     --all
     --audio-input
     --block
     --usb

### qmenu-vm ###

List, manage and configure your qubes.

    Usage: qmenu-vm [OPTION] (--light-theme)

     --all
     --focused
     --halted
     --paused
     --running
     --tags=[TAG]

Installation
------------

    [user@dispXXXX ~]$ git clone https://github.com/sine3o14nnae/qmenu/

    [user@dom0 ~]$ qvm-run --pass-io dispXXXX 'cat /home/user/qmenu/qmenu-XX' > /tmp/qmenu-XX

    [user@dom0 ~]$ sudo cp /tmp/qmenu-XX /usr/bin/

    [user@dom0 ~]$ sudo chmod 755 /usr/bin/qmenu-XX

See [here](https://github.com/Qubes-Community/Contents/blob/master/docs/configuration/qmenu.md)
for detailed instructions.
