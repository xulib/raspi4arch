
# Arch install/tricks on raspi 4 (8G)

## Install modifications for the 8G version of RPi4 

### Usb not recognizing on aarch64 8G ram

Tldr

files: 
```bash
# wget http://os.archlinuxarm.org/os/ArchLinuxARM-rpi-aarch64-latest.tar.gz
# md5sum ArchLinuxARM-rpi-aarch64-latest.tar.gz
10ca5bc029734ede8cee134727d52eea  ArchLinuxARM-rpi-aarch64-latest.tar.gz
```
before you umount the two partitions (in step 7) in the installations manual on [archlinuxarm](https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-4 "archlinuxarm.org").

```bash
# git clone https://github.com/raspberrypi/firmware.git
# cd firmware 
# git checkout dbd3b6fcd9fbb28366118d726585ff833518e263
# cp boot/bcm2711-rpi-4-b.dtb ../boot/.
```

For me there was a problem , that the usb is not recognized if you installed the AArch64 version provieded by [archlinuxarm](https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-4 "archlinuxarm.org").
 
Regard of the [forum](https://archlinuxarm.org/forum/viewtopic.php?f=65&t=14734) there was/is a [github](https://github.com/raspberrypi/linux/issues/3747) issue and  there was a comment: 
> ...The original, downstream support for loading the VL805 firmware was interfering with the newly upstreamed implementation. Reverting it fixed the issue. ..." 

It looks like that for the 8 GB version a new/other firmware is needed if we want that the usb is working. The file bcm2711-rpi-4-b.dtb need to be replaced in the /boot directory.

```bash
# git clone https://github.com/raspberrypi/firmware.git
# cd firmware 
# git checkout dbd3b6fcd9fbb28366118d726585ff833518e263
# cp boot/bcm2711-rpi-4-b.dtb ../boot/.
```
It could be that lately the issue will be fixed in the aarch64 image , so the file was i used was: 

```bash
# wget http://os.archlinuxarm.org/os/ArchLinuxARM-rpi-aarch64-latest.tar.gz
# md5sum ArchLinuxARM-rpi-aarch64-latest.tar.gz
10ca5bc029734ede8cee134727d52eea  ArchLinuxARM-rpi-aarch64-latest.tar.gz
```
