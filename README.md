qmenu
=====

Collection of tools that utilize
[dmenu](https://tools.suckless.org/dmenu/) to provide the user with a
drop down menu for [QubesOS](https://qubes-os.org/) R4.0+,
from which they can quickly administer their qube
preferences, firewall rules, applications, per-qube keyboard layouts, devices,
etc. with only the keyboard.

All qmenu tools are written in POSIX-compliant shell script and only
depend on the POSIX-compliant variants of the (nonqubes)utilities they use.

The colors that correspond to a qube label can be adjusted by appending
` --{LABEL}=#{HEX TRIPLET}` for any label.

Try the following example for visually appealing colors:

~~~
 --purple=#a020f0 --blue=#4363d8 --gray=#bebebe --green=#3cb44b --yellow=#ffe119 --orange=#f58231 --red=#e6194b --black=#414141
~~~

### qmenu-am ###

Launch domU and dom0 applications.

    Usage: qmenu-am [OPTION] (--light-theme) (--{LABEL}=#{HEX TRIPLET})...

     --all
     --focused

### qmenu-dm ###

List and manage your connected devices.

    Usage: qmenu-dm [OPTION] (--light-theme) (--{LABEL}=#{HEX TRIPLET})...

     --all
     --audio-input
     --block
     --usb

### qmenu-vm ###

List, manage and configure your qubes.

    Usage: qmenu-vm [OPTION] (--light-theme) (--{LABEL}=#{HEX TRIPLET})...

     --all
     --focused
     --halted
     --paused
     --running
     --qube=[QUBE]
     --tags=[TAG]

Installation
------------

    [user@dispXXXX ~]$ git clone https://github.com/sine3o14nnae/qmenu/

    [user@dom0 ~]$ qvm-run --pass-io dispXXXX 'cat /home/user/qmenu/qmenu-XX' > /tmp/qmenu-XX

    [user@dom0 ~]# cp /tmp/qmenu-XX /usr/local/bin/

    [user@dom0 ~]# chmod 755 /usr/local/bin/qmenu-XX

See [here](https://github.com/Qubes-Community/Contents/blob/master/docs/configuration/qmenu.md)
for detailed instructions.
