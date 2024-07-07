===================================================

# Jump right into FreeBSD!


> *RUN ALL COMMANDS BELOW AS ROOT! 

> TO BECOME ROOT, RUN: 

```
 su
```
> Password:

```
(The root password you set)
```
===================================================

# VIDEO DRIVERS:

## Intel:

```
pkg install drm-kmod && sysrc kld_list+=i915kms
```

## AMD: 

```
(AMD Radeon HD7000 and newer): pkg install drm-kmod && sysrc kld_list+=amdgpu
```

> Newer cards need a newer DRM-kmod! 7xxx and newer:

```
cd /usr/ports/graphics/drm-61-kmod && make install clean && pkg install gpu-firmware-amd-kmod
```
> (a lot, but it is what is required at the moment.)

> Older card? No problem!

```
pkg install drm-kmod && sysrc kld_list+=radeonkms
```

## NVIDIA: 

> Newer cards, GTX 9XX and newer:

```
pkg install nvidia-driver && sysrc kld_list+=nvidia-modeset
```

> Older card? You can install older drivers!:

```
pkg install nvidia-driver-304 && sysrc kld_list+=nvidia 
```
*note this version of the Nvidia Driver (304) requires an older version of XORG

```
pkg install nvidia-driver-340 && sysrc kld_list+=nvidia
```

```
pkg install nvidia-driver-390 && sysrc kld_list+=nvidia-modeset
```

```
pkg install nvidia-driver-470 && sysrc kld_list+=nvidia-modeset
```

> After you run the command for your graphics provider, run: 

```
pw groupmod video -m username
```

===================================================

# DESKTOP ENVIRONMENTS (XORG):

# If you're using an X-based DE, install XORG first!

```
pkg install xorg
```

## KDE PLASMA: 

```
pkg install kde5 sddm && sysrc dbus_enable="YES" && sysrc sddm_enable="YES"
```

## KDE PLASMA MINIMAL: 

```
pkg install plasma5-plasma konsole dolphin sddm && sysrc dbus_enable="YES" && sysrc sddm_enable="YES"
```

## GNOME: 

```
pkg install gnome && sysrc dbus_enable="YES" && sysrc gdm_enable="YES"
```

## GNOME MINIMAL: 

```
pkg install gnome-lite gnome-terminal && sysrc dbus_enable="YES" && sysrc gdm_enable="YES"
```

## XFCE: 

```
pkg install xfce lightdm lightdm-gtk-greeter && sysrc dbus_enable="YES" && sysrc lightdm_enable="YES"
```

## MATE: 

```
pkg install mate lightdm lightdm-gtk-greeter && sysrc dbus_enable="YES" && pkg install && sysrc lightdm-enable="YES"
```

## MATE MINIMAL: 

```
pkg install mate-base mate-terminal lightdm lightdm-gtk-greeter && sysrc dbus_enable="YES" && sysrc lightdm-enable="YES"
```

## CINNAMON: 

```
pkg install cinnamon lightdm lightdm-gtk-greeter && sysrc dbus_enable="YES" && sysrc lightdm_enable="YES"
```

## LXQT: 

```
pkg install lxqt sddm && sysrc dbus_enable="YES" && sysrc sddm_enable="YES"
```

# Compositors (Wayland)

## 14.1 fixed many issues with Wayland, so now this section of the guide is applicable!


> Before anything, install Wayland and SeatD:

```
pkg install wayland seatd && sysrc seatd_enable="YES" && sysrc dbus_enable="YES" && service seatd start
```

## HYPRLAND:

```
pkg install hyprland kitty
```

## Sway:

```
pkg install sway foot
```
**Base sway, have a look at this for things like lock screens: https://docs.freebsd.org/en/books/handbook/wayland/#wayland-sway

## SwayFX:

```
pkg install swayfx foot
```
**Base swayfx, have a look at this for things like lock screens: https://docs.freebsd.org/en/books/handbook/wayland/#wayland-sway

## Hikari:

```
Coming soon!
```

## Login Managers:

```
pkg install lightdm && sysrc lightdm_enable="YES"
```

```
pkg install sddm && sysrc sddm_enable="YES"
```

```
pkg install gdm && sysrc gdm_enable="YES" **Not recommended because it will more than likely install extra GNOME utilities you don't need.
```

===================================================

# WEB BROWSERS: (Ranked heaviest to lightest btw!)

## FIREFOX: 

```
pkg install firefox
```

## CHROMIUM 

```
pkg install chromium
```

## IRIDIUM BROWSER: 

```
pkg install iridium-browser
```

## FALKON: 

```
pkg install falkon
```

## KONQUEROR: 

```
pkg install konqueror

```

## EPIPHANY (GNOME WEB): 

```
pkg install epiphany
```

## QUTEBROWSER: 

```
pkg install qutebrowser
```

## DILLO: 
```
pkg install dillo
```

## LINKS: 
```
pkg install links
```

## W3M:

```
pkg install w3m
```

===================================================

# VIRTUALIZATION:

## VIRTUALBOX: (Note, currently, in 8 June 2024, FreeBSD 14.1 requires compiling the Virtualbox kernel module. to get it working. It takes longer (only takes a couple minutes), but it still works!)

```
cd /usr/ports/emulators/virtualbox-ose-kmod/ && make install clean && pkg install virtualbox-ose && kldload vboxdrv
```

```
pw groupmod vboxusers -m username
```

```
ee /boot/loader.conf, add the line vboxdrv_load="YES" After, to exit ee, press "ESC + Enter" at the same tme, then the "A" key!
```

```
sysrc vboxnet_enable="YES" && pw groupmod vboxusers -m username
```

```
ee /etc/devfs.conf', add below!

own     vboxnetctl root:vboxusers
perm    vboxnetctl 0660
```

> Continue if you want USB support!

```
pw groupmod operator -m username
```

```
ee /etc/devfs.rules' (doesn't exist yet, dont worry if it says it's new!) Add below:

[system=10]
add path 'usb/*' mode 0660 group operator
```

```
sysrc devfs_system_ruleset="system" && service devfs restart
```

## BHYVE:

```
Coming soon!
```

===================================================

# Extra Wireless Options

## Don't want to edit wpa_supplicant all the time just to connect to another Wi-Fi network? Try wifimgr!

```
pkg install wifimgr
```

===================================================

> Have fun with FreeBSD!

===================================================

> Source of information: https://docs.freebsd.org/en/books/handbook/

===================================================

> By: coolguy71 

===================================================
