===================================================

The last FreeBSD post-install guide you may ever need!

===================================================

V, 0.1

Jump head-first into FreeBSD! (Please don't do this irl)

*RUN ALL COMMANDS BELOW AS ROOT! 

TO BECOME ROOT, RUN: 'su'

Password: 'your root password you set'

===================================================

VIDEO DRIVERS:

Intel: 'pkg install drm-kmod && sysrc kld_list+=i915kms'

AMD: 'pkg install drm-kmod && sysrc kld_list+=amdgpu'

NVIDIA: 'pkg install nvidia-driver && 'sysrc kld_list+=nvidia-modeset'

After you run the command for your graphics provider, run: 'pw groupmod video -m username'

===================================================

DESKTOP ENVIRONMENTS:

KDE PLASMA: 'pkg install kde5 && sysrc dbus_enable="YES" && pkg install sddm && sysrc dbus_enable="YES"'

KDE PLASMA MINIMAL: 'pkg install plasma5-plasma konsole dolphin && sysrc dbus_enable="YES" && pkg install sddm && sysrc dbus_enable="YES"'

GNOME: 'pkg install gnome && sysrc dbus_enable="YES" && sysrc GDM_ENABLE="YES"'

GNOME MINIMAL: 'pkg install gnome-lite gnome-terminal && sysrc dbus_enable="YES" && sysrc GDM_ENABLE="YES"'

XFCE: 'pkg install xfce && sysrc dbus_enable="YES" && pkg install lightdm lightdm-gtk-greeter && sysrc lightdm_enable="YES"

MATE: 'pkg install mate && sysrc dbus_enable="YES" && pkg install lightdm lightdm-gtk-greeter && sysrc lightdm-enable="YES"

MATE MINIMAL: 'pkg install mate-base mate-terminal && sysrc dbus_enable="YES" && pkg install lightdm lightdm-gtk-greeter && sysrc lightdm-enable="YES"

CINNAMON: 'pkg install cinnamon && sysrc dbus_enable="YES" && pkg install lightdm lightdm-gtk-greeter && sysrc lightdm_enable="YES"'

LXQT: 'pkg install LXQT && sysrc dbus_enable="YES" && pkg install sddm && sysrc sddm_enable="YES"'

===================================================

WEB BROWSERS:

FIREFOX: 'pkg install firefox'

CHROMIUM (Note, I tried this (29/4/24) and pkg was not available, compiling is the only method, compiling takes a while!): 'cd /usr/ports/www/chromium && make install clean'

IDIDIUM BROWSER: 'pkg install iridium-browser'

FALKON: 'pkg install falkon'

KONQUEROR: 'pkg install konqueror'

EPIPHANY (GNOME WEB): 'pkg install epiphany'

QUTEBROWSER: 'pkg install qutebrowser'

DILLO: 'pkg install dillo'

LINKS: 'pkg install links'

W3M: 'pkg install w3m'

===================================================

Have fun with FreeBSD!

===================================================

Source of information: https://docs.freebsd.org/en/books/handbook/

===================================================

By: coolguy71 

===================================================
