# Tronxy CRUX1 Marlin Firmware Configuration

This repository contains a customized Marlin firmware configuration for the Tronxy CRUX1 3D printer.

## Overview

The Tronxy CRUX1 is a dual-extruder 3D printer that comes with a 3.5" touch screen display. This configuration addresses several issues with the original firmware and provides improved functionality.

## Key Features

- **480x320 Display Resolution**: Properly configured TFT display with full screen utilization
- **Touch Screen Support**: Fully functional touch interface
- **SD Card Support**: Working SD card functionality for file management
- **Dual Extruder Support**: Configured for dual hotend setup
- **Mesh Bed Leveling**: Manual mesh bed leveling support
- **Power Loss Recovery**: Automatic print recovery after power interruption

## Current Limitations

⚠️ **Important**: This firmware version currently only supports SD card storage. USB flash drive support has been disabled due to compatibility issues with the USB-Host-Shield-20 library on STM32F407 architecture.

## Hardware Compatibility

- **Board**: Tronxy CXY-446-V10 (STM32F407VET6)
- **Display**: 3.5" TFT with FSMC interface (480x320 resolution)
- **Touch**: XPT2046 resistive touch controller
- **Storage**: SD card (onboard SDIO interface)

## Configuration Changes Made

### Display and Touch
- Enabled `TFT_TRONXY_X5SA` for proper 480x320 resolution
- Enabled `TOUCH_SCREEN` for touch functionality
- Configured touch calibration for Tronxy X5SA display

### Hardware Settings
- Changed motherboard from `BOARD_TRONXY_CXY_466_V1` to `BOARD_TRONXY_CXY_446_V10`
- Adjusted endstop hit states for proper homing
- Enabled S-curve acceleration for smoother motion
- Inverted Z-axis direction for proper movement

### Features Enabled
- Mesh bed leveling (`MESH_BED_LEVELING`)
- LCD bed leveling interface
- EEPROM settings storage
- SD card support
- TFT color UI
- Power loss recovery
- Input shaping for X and Y axes

### USB Host Support Disabled
- Commented out `HAS_OTG_USB_HOST_SUPPORT` in pin definitions
- Disabled USB flash drive support to prevent compilation errors
- This resolves conflicts with USB-Host-Shield-20 library

## Compilation

### Prerequisites
- PlatformIO IDE or PlatformIO CLI
- Python 3.x
- Git

### Build Instructions

1. Clone this repository:
```bash
git clone <repository-url>
cd Marlin-TronXY-CRUX1
```

2. Install PlatformIO dependencies:
```bash
python -m pip install platformio
```

3. Compile the firmware:
```bash
python -m platformio run -e TRONXY_CXY_446_V10
```

4. The compiled firmware will be available at:
   - `.pio/build/TRONXY_CXY_446_V10/firmware.bin`
   - `.pio/build/TRONXY_CXY_446_V10/update/fmw_tronxy.bin`

### Memory Usage
- **RAM**: ~38.6% (50,596 bytes of 131,072 bytes)
- **Flash**: ~53.9% (247,348 bytes of 458,752 bytes)

## Installation

1. Copy the `firmware.bin` file to the root of a FAT32 formatted SD card
2. Insert the SD card into the printer
3. Power on the printer
4. The firmware will automatically flash and reboot

## Troubleshooting

### Display Issues
- If the display shows incorrect resolution, ensure `TFT_TRONXY_X5SA` is enabled
- For touch calibration issues, use the built-in touch calibration menu

### Compilation Errors
- If you encounter USB-Host-Shield-20 errors, ensure `HAS_OTG_USB_HOST_SUPPORT` is commented out
- Clean the build cache: `python -m platformio run -e TRONXY_CXY_446_V10 --target clean`

### Boot Issues
- If the printer doesn't boot, try a different SD card
- Ensure the SD card is formatted as FAT32
- Check that the firmware file is named exactly `firmware.bin`

## Future Improvements

- [ ] Investigate USB flash drive support with alternative libraries
- [ ] Add support for additional serial ports
- [ ] Optimize memory usage
- [ ] Add more advanced bed leveling options

## Contributing

When making changes to this configuration:

1. Test thoroughly on the actual hardware
2. Document any new features or limitations
3. Update this README with relevant information
4. Follow Marlin's coding standards

## License

This configuration is based on Marlin firmware, which is licensed under the GPL v3.0. See the original Marlin repository for full license details.

## Acknowledgments

- Marlin Firmware team for the excellent 3D printer firmware
- Tronxy for the CRUX1 hardware platform
- Community contributors for testing and feedback
