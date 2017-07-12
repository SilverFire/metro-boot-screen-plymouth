# Boot screen for Kyiv Metro

## Installation

### Installation for Ubuntu <16.04

Using root, execute the following commands:

```bash
curl -sL https://github.com/SilverFire/metro-boot-screen-plymouth/archive/master.zip > /tmp/boot-screen.zip
unzip /tmp/boot-screen.zip -d /tmp
mkdir /lib/plymouth/themes/metro-boot-screen
cp /tmp/metro-boot-screen-plymouth-master/src/* /lib/plymouth/themes/metro-boot-screen
mv /lib/plymouth/themes/default.plymouth /lib/plymouth/themes/disabled_default.plymouth
ln -s /lib/plymouth/themes/metro-boot-screen/metro-screen.plymouth /lib/plymouth/themes/default.plymouth
rm -rf /tmp/metro-boot-screen-plymouth-master /tmp/boot-screen.zip
sudo update-initramfs -u
```

### Installation for Ubuntu >=16.04

Pretty much the same. Directory `/lib/plymouth/themes/` was moved to `/usr/share/plymouth/themes`, so make sure to:

1. Change paths in the installation script above
2. Update `metro-screen.plymouth` to reflect correct path


## Testing

1. Install plymouth-x11: `sudo apt-get install plymouth-x11`
2. Run the following command to preview boot screen for 10 seconds:

```bash
sudo plymouthd --debug --debug-file=/tmp/plymouth-debug-out ; sudo plymouth --show-splash ; for ((I=0;I<10;I++)); do sleep 1 ; sudo plymouth --update=event$I ; done ; sudo plymouth --quit
```
