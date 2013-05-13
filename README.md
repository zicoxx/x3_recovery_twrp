This is TWRP for LG Optimus 4X HD.
Changes to the sourcecode were made to ensure and improve the functionality of TWRP on the 4X HD.
To make the recovery run successfully, add to the devices BoardConfig.mk following lines:

==================================================================================================================
#LCD resolution of the device
DEVICE_RESOLUTION := 720x1280

#We have internal storage at /data/media
RECOVERY_SDCARD_ON_DATA := true 

#Define internal storage
TW_INTERNAL_STORAGE_PATH := "/data/media"
TW_INTERNAL_STORAGE_MOUNT_POINT := "data"

#Define and add support for external storage
TW_EXTERNAL_STORAGE_PATH := "/external_sd"
TW_EXTERNAL_STORAGE_MOUNT_POINT := "external_sd"

#Specify the LCD-Backlight brightness path to control the LCD brightness
TW_BRIGHTNESS_PATH := /sys/devices/platform/tegra-i2c.1/i2c-1/1-0036/leds/lcd-backlight/brightness
TW_MAX_BRIGHTESS := 100 

#Set CORRECT pixel format. Other pixel formats may work, but causes graphics bugs (eg. half screen bug while running Aroma Installer/File manager)
TARGET_RECOVERY_PIXEL_FORMAT := "RGBX_8888"

#Use prebuilt kernel (kernel from x3's cyanogenmod kernel)
TARGET_PREBUILT_RECOVERY_KERNEL := device/lge/p880/kernel

#We have no select button on the 4X HD, so our select button is the power button
BOARD_HAS_NO_SELECT_BUTTON := true

#Specify path to lun file to support usb mass storage
TARGET_USE_CUSTOM_LUN_FILE_PATH := /sys/devices/platform/tegra-udc.0/gadget/lun0/file
==================================================================================================================


==================================================================================================================
Official TWRP Readme:

**Team Win Recovery Project (TWRP)**

The goal of this branch is to rebase TWRP onto AOSP while maintaining as much of the original AOSP code as possible. This goal should allow us to apply updates to the AOSP code going forward with little to no extra work.  With this goal in mind, we will carefully consider any changes needed to the AOSP code before allowing them.  In most cases, instead of changing the AOSP code, we'll create our own functions instead.  The only changes that should be made to AOSP code should be those affecting startup of the recovery and some of the make files.

If there are changes that need to be merged from AOSP, we will pull the change directly from AOSP instead of creating a new patch in order to prevent merge conflicts with AOSP.

This branch is under final testing and will be used shortly for public builds, but has not officially been released.

You can find a compiling guide [here](http://forum.xda-developers.com/showthread.php?t=1943625 "Guide").

[More information about the project.](http://www.teamw.in/project/twrp2 "More Information")

If you have code changes to submit those should be pushed to our gerrit instance.  A guide can be found [here](http://teamw.in/twrp2-gerrit "Gerrit Guide").
