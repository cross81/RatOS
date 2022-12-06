---
sidebar_label: Manta M8P
---

# BIGTREETECH Manta M8P

## Wiring

![BTT M8P Pro STM32F446 Wiring Diagram](_media/manta-m8p-wiring.svg)
[Open Full Size Image](_media/manta-m8p-wiring.svg)

:::danger if you use the Ratrig endstop switches and cables, do **not** blindly plug them in to your M8P as doing this will short the board's 5V power rail.
You will probably have to swap the outer two wires (red and white) on the board end of the cable but double check to make sure your cables match the wiring diagram in both ends.
Orders shipped after October 2022 should have the correct cables (the connectors on the new cables are white).
:::

:::info Jumpers
A green square is where you would place a jumper, remove all jumpers on the board that are not marked by this symbol.
:::

### Jumpers

The jumpers above the stepper drivers switches stepper driver input power between V_MOT and VIN (ie, board power terminals and motor power terminals).
In the configuration shown in the image above, the MOTOR power isn't connected because the jumpers are set to use the board power (VIN).
If you wanted to use 48V for example, you would connect your 48V psu to the motor power terminal and switch those jumpers to the other position to use V_MOT instead. Of course you shouldn't do this unless you use high voltage capable 5160 drivers.

## Installing RatOS on eMMC

:::info
The Manta M8P is a Compute Module 4 (CM4) host board. RatOS supports CM4's as long as there's no eMMC (using micro SD card, recommended for ease of use) or at least 16gb eMMC storage.
The BTT CB1 is currently not supported.
::: 

If you're using a CM4 with eMMC storage, you cannot use an SD card. You'll have to connect the Manta to a PC and flash the eMMC storage, please follow the steps in the [BTT Manta M8P User Manual](https://github.com/bigtreetech/Manta-M8P/raw/master/BIGTREETECH%20MANTA%20M8P%20V1.0%20User%20Manual.pdf), for how to mount the eMMC storage to your PC. Then use Balena Etcher to flash RatOS to the CM4, just like it was an SD card.

## Firmware installation

Follow the steps in the RatOS Configurator at [http://RatOS.local/configure?step=1](http://RatOS.local/configure?step=1).

## I updated klipper and now i get an error!

When you update klipper you might see an error that looks like this:

![Firmware version mismatch between host and guest](/img/firmware_version_mismatch.png)

This is because klipper made changes to a part of the MCU firmware that we use, and something went wrong while automatically flashing your board. Klipper is telling us that the version of klipper running on the Pi is newer than the version running on the MCU. To fix this, we have to flash the board with a new version of the firmware, Follow the steps in the RatOS Configurator at [http://RatOS.local/configure?step=1](http://RatOS.local/configure?step=1).