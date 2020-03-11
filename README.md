qmenu
=====

Collection of tools that utilize
[dmenu](https://tools.suckless.org/dmenu/) to provide the user with a
drop down menu for [QubesOS](https://qubes-os.org/) R4.0+,
from which they can quickly administer their qube
preferences, firewall rules, applications, per-qube keyboard layouts, devices,
etc. with only the keyboard.

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
     --block
     --mic
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

Dependencies
------------

All qmenu tools are written in POSIX-compliant shell script and only
depend on the POSIX-compliant variants of the (nonqubes)utilities they use.


<details>
 <summary>qmenu-am</summary>

* cut
* grep
* _tr_ (For '--focused' option)
* _xdotool_ (For '--focused' option)
* _xprop_ (For '--focused' option)
* <details>
   <summary>Qubes tools</summary>

  * _qvm-prefs_ (For '--focused' option)
  * qvm-run
  </details>

</details>

<details>
 <summary>qmenu-dm</summary>

* awk
* cut
* grep
* sed
* sort
* tr
* wc
* <details>
   <summary>Qubes tools</summary>

  * qvm-device
  * qvm-ls
  * qvm-prefs
  </details>

</details>

<details>
 <summary>qmenu-vm</summary>

- dom0
   * awk
   * cut
   * grep
   * ls
   * _notify-send_
   * sed
   * sort
   * tr
   * wc
   * _xdotool_ (For '--focused' option)
   * _xprop_ (For '--focused' option)
   * <details>
      <summary>Qubes tools</summary>

     * qubes-vm-boot-from-device
     * qubes-prefs
     * qvm-appmenus
     * qvm-block
     * qvm-check
     * qvm-clone
     * qvm-create
     * qvm-devices
     * qvm-firewall
     * qvm-kill
     * qvm-ls
     * qvm-pause
     * qvm-pci
     * qvm-pool
     * qvm-prefs
     * qvm-remove
     * qvm-run
     * qvm-service
     * qvm-shutdown
     * qvm-start
     * qvm-tags
     * qvm-unpause
     * qvm-volume
     </details>

- domU
   * _setxkbmap_ (For switching keyboard layouts)
</details>

Installation
------------

    [user@dispXXXX ~]$ git clone https://github.com/sine3o14nnae/qmenu/

    [user@dom0 ~]$ qvm-run --pass-io dispXXXX 'cat /home/user/qmenu/qmenu-XX' > /tmp/qmenu-XX

    [user@dom0 ~]# cp /tmp/qmenu-XX /usr/local/bin/

    [user@dom0 ~]# chmod 755 /usr/local/bin/qmenu-XX

For `qmenu-vm`, additionally:

    [user@dom0 ~]$ mkdir /tmp/qmenu_vm

    [user@dom0 ~]$ for file in fq_keyboard fq_logs fq_pm fqubes_prefs fqvm_appmenus fqvm_clone fqvm_create fqvm_device fqvm_firewall fqvm_pci fqvm_prefs fqvm_remove fqvm_run fqvm_service fqvm_tags fqvm_volume; do qvm-run --pass-io dispXXXX "cat /home/user/qmenu/lib/qmenu_vm/$file" > /tmp/qmenu_vm/$file; done

    [user@dom0 ~]# cp -r /tmp/qmenu_vm/ /lib/

See [here](https://github.com/Qubes-Community/Contents/blob/master/docs/configuration/qmenu.md)
for detailed instructions.
