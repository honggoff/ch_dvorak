# Patches for Swiss Dvorak Keyboard Layout

This repository contains patches to the xkb configurtion files that define the keyboard layouts available in the X server. They add a variant called 'dvorak' to the swiss german keyboard layout. This is my own adaptation of the german dvorak layout to the peculiarities of the standard swiss german layout.


## Create a Patch for a new Ubuntu Version

```shell
old_version=15.04
new_version=16.04

cd ubuntu
mkdir ${new_version}
cd ${new_version}
cp -r /usr/share/X11/xkb/ orig
cp -r orig new
cd new
patch --no-backup-if-mismatch -p1 < ../../${old_version}/dvorak.patch
# fix things if the old patch did not apply
cd ..
diff -urN --no-dereference orig/ new/ > dvorak.patch
```

## Apply an existing Patch to your Installation

```shell
cd /usr/share/X11/xkb
sudo patch -p1 < ${srcdir}/ubuntu/${new_version}/dvorak.patch
```
