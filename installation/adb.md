## Setting up the ADB feature

You need a local installed Server (like a raspi) or you could use your existing instance from MAD. Install the adb package and activate it.

Installation for raspi:

```
sudo apt-get update
```

```
sudo apt-get install -y android-tools-adb android-tools-fastboot
```

## Phone Prepere
### Config your Phone for ADB over Wifi

-Enable Usbdebuging in Developer option on phone
-connet to pc with usb cable
-Allow the connect on Phone
-type in terminal
```adb tcpip 5555```
-unplug the usb

-now we are connecting to phone again over wifi
-```adb connect <device IP>:5555```
-after we connected

optional:

after you connected you can make your connection to last until reboot
todo this you need to type
adb shell
su
setprop service.adb.tcp.port 5555
start adbd
exit
now connection stays until reboot

or you can change it back with
adb shell
su
setprop service.adb.tcp.port -1
start adbd


This will make it persistent:
adb shell
su
setprop persist.adb.tcp.port 5555
reboot

ADB over USB might not be available after reboot. To undo this setting, do:

setprop persist.adb.tcp.port ""
reboot
