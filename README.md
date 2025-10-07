Optimized Marlin Firmware for the Tronxy Crux 1
<p align="center">
A pre-configured and optimized firmware project for the Tronxy Crux 1 3D printer, ensuring maximum hardware compatibility and access to the latest Marlin features.
</p>

<p align="center">
<a href="https://www.google.com/search?q=https://github.com/MarlinFirmware/M Marlin/blob/bugfix-2.1.x/LICENSE"><img alt="License" src="https://img.shields.io/github/license/marlinfirmware/marlin.svg"></a>
<img alt="Marlin Version" src="https://www.google.com/search?q=https://img.shields.io/badge/Marlin-bugfix--2.1.x-brightgreen.svg">
<img alt="Status" src="https://www.google.com/search?q=https://img.shields.io/badge/Status-Ready%2520to%2520Compile-blue.svg">
</p>

1. Project Overview
This repository contains a ported and specifically configured version of the Marlin firmware for the Tronxy Crux 1 printer. The project's goal is to offer a clean, updated, and reliable codebase by eliminating guesswork and applying a configuration meticulously extracted from the original manufacturer's firmware.

The main objective is to provide Crux 1 owners with a safe and easy way to upgrade their printer, leveraging the performance improvements, new features, and bug fixes from the Marlin community, with the added bonus of supporting both microcontroller (MCU) variants found on this printer.

2. Key Features
Based on the Latest Version: Built upon the official bugfix-2.1.x branch of Marlin, ensuring you have the most current features and patches.

Dual-MCU Support: The same source code can be compiled for motherboards using either the STM32F446Z chip or the GD32F4xx clone, covering both hardware revisions of the Crux 1.

Evidence-Based Configuration: Every hardware parameter (machine dimensions, motor steps, PID values, etc.) has been carefully migrated from Tronxy's legacy firmware to ensure maximum compatibility. No assumptions were made.

Ready to Compile: The PlatformIO environment is fully configured. Simply choose the correct target for your motherboard and build.

3. Installation
You can compile this firmware using two methods. The commands to build are the same for both, but the setup is different.

Method 1: VS Code + PlatformIO IDE (Recommended)
This is the easiest method as it provides a graphical interface and manages dependencies automatically.

Install Visual Studio Code.

Open VS Code, go to the Extensions view (Ctrl+Shift+X), and install the official PlatformIO IDE extension.

Method 2: PlatformIO Core via Command-Line (Advanced)
If you prefer to work exclusively in the terminal without VS Code, you can install the PlatformIO command-line tools. This works on Windows, macOS, and Linux.

Ensure you have Python (version 3.6+) installed and in your system's PATH.

Open your terminal (Command Prompt, PowerShell, Terminal, etc.) and install PlatformIO Core using pip:

pip install platformio

Verify the installation by checking the version:

pio --version

4. Quick Compilation Guide
The compilation commands are the same for any operating system (Windows/macOS/Linux).

Step 1: Get the Source Code
Open your terminal and clone this repository:

# Replace with your repository's URL
git clone [https://github.com/Felipe-Guerche/Marlin-TronXY-CRUX1.git](https://github.com/Felipe-Guerche/Marlin-TronXY-CRUX1.git)
cd Marlin-TronXY-CRUX1

(If you are using Method 1, you can do this step by using File -> Open Folder... in VS Code and opening the cloned directory.)

Step 2: Identify Your Motherboard's Chip
Before compiling, you must know if your printer uses an STM32 or a GD32 chip. If you are unsure, follow the instructions in the "How to Identify Your MCU" section below.

Step 3: Compile for the Correct Target
From the project's root directory in your terminal, run the command that matches your motherboard's chip.

A) For Motherboards with the STM32F446Z Chip (Standard)
Run the following command:

pio run -e TRONXY_CXY_446_V10

B) For Motherboards with the GD32F4xx Chip (Clone)
Run the following command:

pio run -e TRONXY_CRUX1_GD32

Step 4: Locate and Install the Firmware
After a successful compilation, the firmware.bin file will be located in the directory:

.pio/build/[ENVIRONMENT_NAME]/

Copy the firmware.bin file to the root directory of an SD card, insert it into your powered-off printer, and then turn it on. The firmware update will start automatically.

5. How to Identify Your MCU
As documented by Tronxy, there are two reliable ways to check which chip your printer uses:

Via the Printer's Menu: Navigate to System -> Info (or a similar menu) on your printer's screen. If the displayed information includes "GD32", your chip is from GigaDevice. Otherwise, it is an STM32.

Visually: Open the motherboard housing and look directly at the main microcontroller (the largest square chip). The text printed on the chip's surface will clearly state STM32... or GD32....

6. License
This project is a derivative of Marlin Firmware and is therefore distributed under the GPLv3 License, in accordance with Marlin's original license. Any modifications and distributions of this code must also adhere to the terms of this license.

7. Credits & Acknowledgements
The entire Marlin Firmware team for their incredible open-source project.

Tronxy for providing the original legacy firmware that served as the basis for the hardware configuration.