# gc9a01-overlay-orange-pi-zero-2w
This is a repo that contains and show how to use gc9a01-overlay.dts on OrangePi. For using with the kernel module fbtft to show image on a round TFT.

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
