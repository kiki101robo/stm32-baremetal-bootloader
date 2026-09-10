# STM32 Baremetal Bootloader

Bare-metal bootloader for STM32F4 built from scratch in C — custom linkerscripts, memory regions, jump-to-application logic, and a multi-slot bootloader system supporting multiple firmware images with UART-based selection.

## Overview

This project implements a custom bootloader for STM32F4 microcontrollers without relying on any vendor bootloader libraries. It covers the full embedded build pipeline — from writing a custom linkerscript and defining memory regions, to implementing jump-to-application logic and building a multi-slot firmware storage system that can hold multiple applications on the same chip.

## Features

- Custom linkerscript with user-defined `MEMORY` regions and `SECTIONS`
- Jump-to-application logic for transferring control from bootloader to user firmware
- Multi-slot memory system for storing multiple firmware images
- Push-button trigger for entering bootloader mode
- UART communication driver for selecting which firmware slot to boot
- Shared functions between bootloader and application code

## Hardware / Requirements

- **MCU:** STM32F4 (e.g. STM32F407VG / Discovery board) — *update with your exact board*
- **Toolchain:** `arm-none-eabi-gcc` (version X.X) — *update with your version*
- **Flasher/Debugger:** ST-Link + OpenOCD (or STM32CubeProgrammer)
- **Build system:** Make — *update if you use CMake instead*
- **UART terminal:** Any serial terminal (e.g. PuTTY, minicom, screen) for testing slot selection

## Memory Layout

| Region        | Address Range              | Purpose                    |
|---------------|-----------------------------|-----------------------------|
| Bootloader    | `0x08000000 - 0x0800XXXX`   | Bootloader code             |
| Slot 0        | `0x0800XXXX - 0x0800XXXX`   | Firmware application 0      |
| Slot 1        | `0x0800XXXX - 0x0800XXXX`   | Firmware application 1      |

*Update this table with your actual linkerscript memory regions.*

## Build Instructions

```bash
# Clone the repository
git clone https://github.com/<your-username>/stm32-baremetal-bootloader.git
cd stm32-baremetal-bootloader

# Build the bootloader
make

# Flash the bootloader
make flash
```

*Update these commands to match your actual Makefile/CMake targets.*

## Usage

1. Hold the push-button and reset the board to enter bootloader mode.
2. Connect to the board over UART (baud rate: `XXXXX`).
3. Send a command to select the desired firmware slot.
4. The bootloader jumps to the selected application.

*Update with your actual button pin, baud rate, and UART command format.*

## Project Structure
