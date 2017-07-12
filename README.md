# Boot screen for Kyiv Metro

## Installation

### Installation for Ubuntu <16.04

Using root, execute the following commands:

```bash
git clone https://github.com/silverfire/metro-boot-screen-plymouth.git /tmp/metro-boot-screen
mkdir /lib/plymouth/themes/metro-boot-screen
cp /tmp/metro-boot-screen/src/* /lib/plymouth/themes/metro-boot-screen
mv /lib/plymouth/themes/default.plymouth /lib/plymouth/themes/disabled_default.plymouth
ln -s /lib/plymouth/themes/metro-boot-screen/metro-screen.plymouth /lib/plymouth/themes/default.plymouth
rm -rf /tmp/metro-boot-screen
```


### Installation for Ubuntu >=16.04

Directory `/lib/plymouth/themes/` was moved to `/usr/share/plymouth/themes`, so make sure to:

1. Change the paths in the installation script above
2. Update `metro-screen.plymouth` to reflect correct path to the theme


## Testing

Run the following command to preview boot screen for 10 seconds:

```bash
sudo apt-get install plymouth-x11
sudo plymouthd --debug --debug-file=/tmp/plymouth-debug-out ; sudo plymouth --show-splash ; for ((I=0;I<10;I++)); do sleep 1 ; sudo plymouth --update=event$I ; done ; sudo plymouth --quit
```
