# NVIDIA Jetson AGX Xavier Utilities

### Increasing USBFS Memory Size

Linux seems to limit usb packet sizes to somewhere between 2 and 16MB. If you're using a high resolution cameras over USB3.0 at fast framerates, this is a problem and you need to increase this allocation limit to ensure no packet loss or packet corruption. On the TX2 this is easier and is a matter of just updating */etc/default/grub* but on the Xavier it's a little more work:

Navigate to the JetPack installer location (of recent this has been placed in $HOME/nvidia. You can then find the **flash.sh** file in the Linux_for_Tegra folder.

Make sure your Xavier is in recovery mode and is connected to your laptop/desktop via USB. 

```
sudo ./flash.sh -k kernel -C "usbcore.usbfs_memory_mb=2048" -k kernel-dtb jetson-xavier mmcblk0p1
```

Flashing should take less than a minute and then your Xavier will reboot.

On reboot, you can check if your changes have persisted across boots.

```
cat /sys/module/usbcore/parameters/usbfs_memory_mb
```


