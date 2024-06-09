===================================================

V, 0.1

## Jump right into FreeBSD!


*RUN ALL COMMANDS BELOW AS ROOT! 

TO BECOME ROOT, RUN: 
> 'su'

Password:
> 'the root password you set'

===================================================

## VIDEO DRIVERS:

Intel:
> 'pkg install drm-kmod && sysrc kld_list+=i915kms'

AMD: 
> 'pkg install drm-kmod && sysrc kld_list+=amdgpu'

NVIDIA: 

`pkg install nvidia-driver && sysrc kld_list+=nvidia-modeset`

After you run the command for your graphics provider, run: 
> 'pw groupmod video -m username'

===================================================

## DESKTOP ENVIRONMENTS:

KDE PLASMA: 
> 'pkg install kde5 && sysrc dbus_enable="YES" && pkg install sddm && sysrc dbus_enable="YES"'

KDE PLASMA MINIMAL: 
> 'pkg install plasma5-plasma konsole dolphin && sysrc dbus_enable="YES" && pkg install sddm && sysrc dbus_enable="YES"'

GNOME: 
> 'pkg install gnome && sysrc dbus_enable="YES" && sysrc GDM_ENABLE="YES"'

GNOME MINIMAL: 
> 'pkg install gnome-lite gnome-terminal && sysrc dbus_enable="YES" && sysrc GDM_ENABLE="YES"'

XFCE: 
> 'pkg install xfce && sysrc dbus_enable="YES" && pkg install lightdm lightdm-gtk-greeter && sysrc lightdm_enable="YES"

MATE: 
> 'pkg install mate && sysrc dbus_enable="YES" && pkg install lightdm lightdm-gtk-greeter && sysrc lightdm-enable="YES"

MATE MINIMAL: 
> 'pkg install mate-base mate-terminal && sysrc dbus_enable="YES" && pkg install lightdm lightdm-gtk-greeter && sysrc lightdm-enable="YES"

CINNAMON: 
> 'pkg install cinnamon && sysrc dbus_enable="YES" && pkg install lightdm lightdm-gtk-greeter && sysrc lightdm_enable="YES"'

LXQT: 
> 'pkg install LXQT && sysrc dbus_enable="YES" && pkg install sddm && sysrc sddm_enable="YES"'

===================================================

## WEB BROWSERS: (Ranked heaviest to lightest btw!)

FIREFOX: 
> 'pkg install firefox'

CHROMIUM 
> 'pkg install chromium'

IDIDIUM BROWSER: 
> 'pkg install iridium-browser'

FALKON: 
> 'pkg install falkon'

KONQUEROR: 
> 'pkg install konqueror'

EPIPHANY (GNOME WEB): 
> 'pkg install epiphany'

QUTEBROWSER: 
> 'pkg install qutebrowser'

DILLO: 
> 'pkg install dillo'

LINKS: 
> 'pkg install links'

W3M: 
> 'pkg install w3m'

===================================================

## VIRTUALIZATION:

VIRTUALBOX: (Note, currently, in 8 June 2024, FreeBSD 14.1 requires compiling Virtualbox to get it working. It takes longer (Maybe around 30 minutes to 1 hour), but it still works!)
> cd /usr/ports/emulators/virtualbox-ose && make install clean && kldload vboxdrv

> 'ee /boot/loader.conf', add the line 'vboxdrv_load="YES"' After, press "ESC + Enter" at the same tme, then the "A" key!

> 'sysrc vboxnet_enable="YES" && 'pw groupmod vboxusers -m username'

> 'ee /etc/devfs.conf', add below!

> 'own     vboxnetctl root:vboxusers'

> 'perm    vboxnetctl 0660'

> Continue if you want USB support!

> 'pw groupmod operator -m username'

> 'ee /etc/devfs.rules' (doesn't exist yet, dont worry if it says it's new!) Add below:

> '[system=10]'

> 'add path 'usb/*' mode 0660 group operator'

> 'sysrc devfs_system_ruleset="system"'

> service devfs restart

BHYVE:
> Coming soon!

===================================================


Have fun with FreeBSD!

===================================================

Source of information: https://docs.freebsd.org/en/books/handbook/

===================================================

By: coolguy71 

===================================================
