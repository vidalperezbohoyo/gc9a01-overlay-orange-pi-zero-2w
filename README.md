# gc9a01-overlay-orange-pi-zero-2w
This is a repo that contains and show how to use **gc9a01-overlay.dts** on **OrangePi**. For using with the kernel module **fbtft** to show image on a round TFT.

# What i am using
## System
OrangePi Zero 2W (1.5GB) with Ubuntu22 kernel 6.1.31-sun50iw9
## Wiring

# How to use it
- Copy the provided **gc9a01-overlay.dts** to /tmp
- Run ``sudo orangepi-add-overlay gc9a01-overlay.dts`` (This will compile and setup everything)
- Reboot to apply changes
## Check that everything it is ok
- Check that ``ls /dev/fb*`` shows ``/dev/fb0  /dev/fb1``. Previously to this repo only existed ``dev/fb0``.
- Check that ``/boot/overlay-user/gc9a01-overlay.dtbo`` exists.
- Check ``cat /boot/orangepiEnv.txt`` that contains the line: ``user_overlays=gc9a01-overlay`` (DO NOT ADD IT MANUALLY)
```
verbosity=1  
bootlogo=false  
console=both  
disp_mode=1920x1080p60  
overlay_prefix=sun50i-h616  
rootdev=UUID=eaa7fbfc-c2d4-469e-b037-a160948a9c70  
rootfstype=ext4  
user_overlays=gc9a01-overlay  
```
- Run a demo:
```
cd
git clone https://github.com/grz0zrg/fbg
cd fbg/examples
```
Replace (to use our device), in **earth.c** file, the line:
```
struct _fbg *fbg = fbg_fbdevInit();
```
By:
```
const char *fbdev = "/dev/fb1";
struct _fbg *fbg = fbg_fbdevSetup((char*)fbdev, 0);
```
Compile and run:
```
make
./quickstart
```
# Useful information for modification

## Allwinner pin numeration
You can see that pins are called by Letter and Number: Example: P**H5** or P**I7**...  
To convert to .dts format: ```<&pio 8 6 0>```
Use this table to relationate, letter and ID.
| Port  | PortID |
|-------|--------|
| A     | 0      |
| B     | 1      |
| C     | 2      |
| D     | 3      |
| E     | 4      |
| F     | 5      |
| G     | 6      |
| H     | 7      |
| I     | **8**  |  

For the given example:  ```<&pio 8 6 0>```   
It is: P**I6**  
Format is: ```<&pio PortID Pin 0>```
