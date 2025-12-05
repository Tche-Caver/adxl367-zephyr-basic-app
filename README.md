# ADXL367 Zephyr Application

This simple Zephyr application reports the X, Y, and Z acceleration values from an ADXL367 (or ADXL366).  This repository contains:
- Application code which reports accelerometer maginitude readings
- Devicetree overlays for the MAX32655FTHR
- Kconfig prj.conf enabling sensors, the accelerometer driver, and floating point printf output

This application requires basic Zephyr knowledge of workspaces, etc.
- For this example, the MAX32655FTHR will be used, but the overlay and build command can be changed to use a different board

# Hardware Setup
Hardware required:
- MAX32655FTHR board
- EVAL-ADXL367Z (or EVAL-ADXL366Z)
- Micro USB cable (with data transfer capabilities)
- Jumper wires
  
Hardware Setup:
- Connect the SPI pins on the MAX32655FTHR to the SPI pins on the EVAL-ADXL367
- Connect 3.3V on the MAX32655FTHR to VS on the EVAL-ADXL367
- Connect 1.8V on the MAX32655FTHR to VDDIO on the EVAL-ADXL367
- Connect GND on the MAX32655FTHR to GND on the EVAL-ADXL367
- The feather board can now be plugged into your computer

# Software Setup:
Initialize a Zephyr workspace with this repo as the manifest repo
```
west init -m https://github.com/Tche-Caver/adxl367-zephyr-basic-app adxl367-wkspc
```

Move into the workspace topdir and update the workspace with modules specified in the manifest file
```
cd adxl367-wkspc
west update
```

Move into the manifest repo and build the application
```
cd adxl367-zephyr-basic-app
west build -p always -b max32655fthr/max32655/m4 app
```
In this case the MAX32655 is being used, so the board specifier is max32655fthr/max32655/m4.  This can be changed for different boards.

Flash the application
```
west flash
```

