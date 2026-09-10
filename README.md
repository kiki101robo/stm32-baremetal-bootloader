# STM32 Baremetal Bootloader

A custom bare-metal bootloader for STM32F411RE, built from scratch in C without any vendor bootloader libraries.

## What This Project Is

This project explores bootloader development on the STM32F411RE, covering the full path from the embedded build process to a working multi-slot firmware system. The goal is to understand how bootloaders work at a low level — memory layout, linking, and firmware selection — by building one from the ground up rather than using an existing framework.

## Hardware

- **MCU:** STM32F411RE (Nucleo-F411RE)

## Features

- Custom linkerscript with user-defined `MEMORY` regions and `SECTIONS`
- Jump-to-application logic for transferring control from bootloader to user firmware
- Multi-slot memory system capable of storing multiple firmware applications on the same microcontroller
- Push-button trigger for entering bootloader mode
- Simple UART communication driver for selecting which firmware application to run
- Shared functions between the bootloader and user application
