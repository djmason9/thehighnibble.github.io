---
sidebar: auto
---

# Updating Software (Draft)

## Overview

::: warning
While every effort is made to ensure any new release of firmware and image software is ready for use, experience and [Murphy's Law](https://en.wikipedia.org/wiki/Murphy%27s_law) dictate that there will be problems from time to time.

If you don't like risk and don't count yourself as an [early adopter](https://en.wikipedia.org/wiki/Early_adopter) then follow the [forum](http://bit.ly/IMSAI8080esp) and look for a clear sign of positive reports about a new release before proceeding with any update.

The worst that can happen is that you will need to install the **Espressif** [esptool.py](https://github.com/espressif/esptool) on your Windows/Mac/Linux PC to be able to re-flash your ESP32 to bring your IMSAI8080esp back to life.  
:::

**Firmware** and **Image** updates are published via **GitHub**, accessible using the *GitHub* link in the upper-right corner of this page.

::: tip
It is recommended to always use the release marked as the **Latest Release** unless you have a specific reason not to.

The current release is [September 2019 Release - patch-2](https://github.com/thehighnibble/firmware/releases/tag/v1.2.3) (v.1.2.3)
:::

## Updating the Firmware

Updating the **firmware** is a simple *drag & drop* process via the web-based *desktop UI*.

### Download the firmware from GitHub

Download the **FIRMWARE.zip** file from the latest release on GitHub (see above).

The **FIRMWARE** package in the release assets is a *ZIP* file containing 4 files, for example:

```
bootloader.bin        21K
imsai_part_table.bin  3.0K
imsaisim_esp32.bin    898K
ota_data_initial.bin  8.0K
```

To update the *firmware* you need only the `imsaisim_esp32.bin` file. This is the **IMASAI 8080esp** firmware binary to be flashed to the ESP32.

::: danger
The remaining files are only for flashing a new firmware installation to a blank ESP32, and can only be flashed using the **Espressif** [esptool.py](https://github.com/espressif/esptool).
:::

### Upload (flash) the firmware to the ESP32

- Drag-and-drop the `imsaisim_esp32.bin` file onto the `SYS:` device **icon** on the *Desktop UI* to flash it to the ESP32.
- Confirm the first dialog, and wait (typically 10-30 seconds) until you see the second dialog confirming the upload was successful

::: warning
If you don't receive the second dialog confirming the upload was successful, then the firmware will not have been flashed.
This will not effect the ESP32 as it will simply reboot on the last working firmware.

Some early adopters have reported this occurring, and the reason was poor Wi-Fi connectivity causing drop-outs. The solution was simply to move their IMSAI8080esp closer to their Wi-Fi Access Point
:::

### Reboot the ESP32

Reboot the ESP32 using the reset (EN) press button on ESP32, or click the reboot button (Red, circular arrow) on the `SYS:` window.

Your IMSAI 8080esp will now reboot on the new firmware.

### Checking the firmware version

The firmware version number is reported in two places:

1. To the system console (UART0 - USB or RS232-1 at 115200 baud) early in the boot process:

<pre><code><span style="color: #00FF00;">I (326) cpu_start: Application information:
I (331) cpu_start: Project name:     imsaisim_esp32
I (337) cpu_start: App version:      v1.2.2
I (342) cpu_start: Compile time:     Sep  7 2019 15:50:57
I (348) cpu_start: ELF file SHA256:  fcb184bf5b3633a0...
I (354) cpu_start: ESP-IDF:          v4.1-dev-59-gfecfdb909
</span></code></pre>

In this example you can see the `App version:   v1.2.2` indicating that the system is running the `v1.2.2` firmware.

2. The `SYS:` System (host) virtual device on the *desktop UI*
![Thanks John K](./SYS_build_version.png)

In this example (thanks to community member John Kennedy) you can see the `Build version v1.2.2` indicating that the system is also running the `v1.2.2` firmware.

### Background - Over The Air (OTA) updates

This handy, *Over The Air* (OTA) update feature is provided as part of the **Espressif** *esp-idf* development platform.
There are two *partitions* that can each store an *OTA firmware*, **ota_0** and **ota_1**.

Each update is flashed to the next available partition, the original **factory** partition is never overwritten by an *OTA update*.
Details of what partitions are active (Running:), booted (Boot:) and available (Next:) are given in the `SYS:` System (host) virtual device on the *desktop UI* under the heading **Partitions**

For further information you can refer to the **Espressif** *esp-idf* [documentation](https://docs.espressif.com/projects/esp-idf/en/latest/api-reference/system/ota.html) 

Also you can set the startup configuration mode for 'NVS_LOG_LEVEL' to 'INFO' at watch the firmware update/flash process logs on the system console.

## Updating the µSD card Image

Currently the only way to update the **µSD card Image** is to remove the *µSD card* from your **IMSAI8080esp** and connect it to your Windows/Mac/Linux PC.

The filesystem on the *µSD card* is `FAT32`.

With the *µSD card* filesystem mounted on your PC you should be able to:

- backup the whole *image*
- restore a whole *image*
- edit individual configuration files
- directly manage disk *(\*.dsk)* image files in the disk library directory

Before any **µSD card Image Update** is released, a *drag & drop* process similar to the *firmware update* process described above will be made available in a new firmware. This will allow the *image update* to be done without the need to mount the *µSD card* in a PC.