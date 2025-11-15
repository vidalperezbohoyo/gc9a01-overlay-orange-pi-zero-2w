# gc9a01-overlay-orange-pi-zero-2w
This is a repo that contains and show how to use gc9a01-overlay.dts on OrangePi. For using with the kernel module fbtft to show image on a round TFT.

# How to use it

Check ``cat /boot/orangepiEnv.txt`` that contains the line: ``user_overlays=gc9a01-overlay`` (DO NOT ADD IT MANUALLY)  
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

# What i am using
OrangePi Zero 2W (1.5GB) with Ubuntu22 kernel 6.1.31-sun50iw9

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
