---
sidebar: auto
---

# Step-by-step Assembly Guide (Draft)

## Notices
::: tip
**Please read all the following notices and instructions before assembling the IMSAI 8080esp replica kit.**
:::

::: warning
This kit contains cut acrylic.
Cut acrylic can have sharp edges that can in turn cut. As a precaution, wear cotton gloves to protect your hands while handling the cut acrylic.
:::

::: danger CAUTION
This kit contains many small parts that may be a choking hazard and is not suitable for children. Keep the contents of this kit away from children to avoid choking.
:::

::: tip NOTE
This kit is for hobby and educational interest only. The simulated replica computer you will build should not be used for any other purpose and cannot be expected to work reliably beyond a demonstration of the simulated computer.
:::

::: tip
Keep the box the IMSAI 8080esp replica kit shipped in. This custom made box was designed to both ship the unassembled kit and also to house the assembled replica. It is the best box you can use if you need to store or transport your finished IMSAI 8080esp.
:::

::: tip
Keep one of the full sheets of cardboard from above or below the components. This will serve as a tool to help with the assembly of the kit, especially for retaining the M4 bolts in the correct position while assembling all the layers of acrylic and the PCB together. It maybe useful to you in future if you ever need to disassemble and reassemble the IMSAI 8080esp.
:::

::: warning Notes on the PCB
- There is no resistor R15, it was removed from the design long ago and the resistors were never renumbered
- There are 2 silk screen errors on the PCB:
    1. the LED LA14 is incorrectly labeled as LS14
    2. the LED LD0 is labeled on the left of the LED and should be labeled above as per LD1-LD7
- There is a 5x2 group of through-holes marked **Spare** that nothing gets soldered into
- There are two groups of 8x1 through-holes that are unmarked (one above LRN1 and one below RN1) that nothing gets soldered into
:::

::: tip Note
This step-by-step assembly guide refers to the **front** and **back** of the PCB as follows:

- the **front** of the PCB has the silkscreen for the LEDs and the toggle switches
- the **back** of the PCB has the silkscreen of the IMSAI 8080 Microcomputer System decal and The High Nibble logo
:::

::: tip
There is a [play list of videos on YouTube](https://www.youtube.com/playlist?list=PLADkYVZqAxdOlpkLc3HC-EbbttXevZ3-B) that demonstrate this step-by-step assembly sequence and includes additional tips for successful assembly.
:::

## Unpacking and checking against the BOM

::: tip
Please unpack the entire kit and perform a stock take of what you have received against the [Bill-of-Materials](../bom/).
:::

::: warning
If you believe you are missing any components when you compare the kit contents with the [Bill-of-Materials](../bom/) please contact me directly by email to [info@thehighnibble.com](mailto:info@thehighnibble.com).

Please respect that this kit is a hobby project made by an individual maker and not a mass produced product from a manufacturer. While every care was taken to pack each kit correctly, mistakes make have occurred.
:::

::: danger DAMAGE
If your kit arrived in a damaged state, or if upon opening the kit you find any of the contents to be damaged, please take photographs of the damage and include them in your email.
:::

::: tip
I will happily work with you directly, via email, to resolve the issues with your incomplete or damaged kit.
This may require mailing replacement parts to you and that will take time, so please have patience.
:::

## PCB & Soldering

### ESP32 Microcontroller, PSRAM & micro SD Card Socket

| Step | Parts | Location | Notes |
| ---: | ----- | -------- | ----- |
| 1. |  Header 20x1 Male | ESP32-PICO-KIT board | Cut 2 sets of 3 pins from the 20x1 Male Header strip. Solder these into the unpopulated through-holes on the ESP32-PICO-KIT board. Upon completion there should be 20 pins along each edge of the underside of the ESP32-PICO-KIT board. |
| 2. | Connector 20x1 Female (x2) | `ESP32` back | Solder these connectors mounted on the **back** of the PCB in the 2 rows of 20 through-holes that form a DIP40 outline marked `ESP32`. |
| 3. | PSRAM (SMD) | `U13` front | *Note: Pin 1 is indicated on the PCB by a white dot and on the component by a dimple in the plastic case*. When done, perform a continuity test with a multimeter from each pin of the SOP-8 package to a connected pad on the PCB (see video, details to follow) |
| 4. | microSD Card Socket (SMD) | `uSD Card` front | Align the two locating pins on the microSD Card Socket with the two holes in the PCB. Solder the 4 large ground pads of the lid first ensuring the 9 smaller leads are well aligned, then solder the 9 smaller leads. |
| 5. | Resistor 10K | `R14` front | |
| 6. | Capacitor 100nF | `C1` front | |
| 7. | Resistor Network 6x10K | `RN1` back | *Note: Pin 1 is indicated on the PCB by the square pad and on the component by a white dot*|
| 8. | ESP32-PICO-KIT, microSD Memory Card | **[TEST STEP]** | Plug the ESP32-PICO-KIT into the female connectors on the **back** of the PCB. *Note: The USB connecter should be towards the near edge of the PCB and the WiFi antenna towards the RS232 connector mounting holes.* Insert the microSD card. Connect the ESP32-PICO-KIT to a PC with a suitable USB cable. Run a terminal emulator at 115200 baud 8N1 connected to the TTY/COM port that the ESP32-PICO-KIT presents and observe the boot logs. Errors with either the PSRAM or the microSD card will indicate soldering mistakes (see video, details to follow) |

::: danger
Before continuing, remove both the microSD Memory Card from the socket and the ESP32-PICO-KIT from the female connectors, **taking care not to bend the Wi-Fi antenna.**
:::

### LEDs and accompanying Resistors

::: tip
The LEDs and accompanying Resistors should be soldered in groups of 8 as indicated below and each group of 8 tested before proceeding to the next group.
:::

::: tip
Use the supplied black acrylic spacer and alignment tools. Tape them in place with the LEDs before you solder to help achieve the  alignment of each group of 8 LEDs.

- My preference is to raise the LEDs 3mm off the PCB, the black acrylic spacer with 8 open vertical slots enables this. You can, however, solder the LEDs sitting flush with the PCB.
- The black acrylic alignment tool with 8 round holes should always be used to help align 8 LEDs at a time to be in alignment

(see video, details to follow)
:::

::: danger
LEDs are polarized and must be soldered in the correct orientation. The cathode (short lead, nearest the flat edge) should be soldered in the **square**, lower, though-hole pad. The anode (long lead) should be soldered in the **round**, upper, though-hole pad. Check the orientation of all LEDs in each group of 8 before soldering into place by visually inspecting the flat edge corresponding with the flat indicated in the silk screen on **front** side of the PCB, and the alignment of the long and short leads on the **back** side of the PCB.
:::

| Step | Parts | Location | Notes |
| ---: | ----- | -------- | ----- |
| 9a. | LED Red 5mm (x8) | `LA8-LA15` front |  *Note: LEDs are polarized and must be soldered in the correct orientation.* Use the acrylic spacer and alignment tools. See notes above. |
| 10a. | Resistor 3K ohm (x8) | `R32-R39` front | Resistors are **not** polarized and can be inserted & soldered either way around. Because of my sense of aesthetic (ok, my OCD) I like to orientate them all the same way according to the coloured bands. |
| 11a. | Test Lead | [TEST STEP] | At this time you should test the group of 8 LEDs you have just soldered into place. Insert the ESP32-PICO-KIT into its socket and connect it to a power source. Using the supplied test lead you can use the +5V provided by the ESP32-PICO-KIT to the PCB to test each LED (see video, details to follow) |

::: danger
Before continuing, remove both the microSD Memory Card from the socket and the ESP32-PICO-KIT from the female connectors, **taking care not to bend the Wi-Fi antenna.** 
:::

#### Steps 9-10 can now be repeated for each remaining group of LEDs in the following suggested order.

| Step | Parts | Location | Notes |
| ---: | ----- | -------- | ----- |
| 9b. | LED Red 5mm (x8) | `LS0-LS7` front | |
| 10b. | Resistor 3K ohm (x8) | `R40-R47` front | |
| 11b. | Test Lead | [TEST STEP] | |
| 9c. | LED Red 5mm (x8) | `LO0-LO7` front | |
| 10c. | Resistor 3K ohm (x8) | `R16-R23` front | |
| 11c. | Test Lead | [TEST STEP] | |
| 9d. | LED Red 5mm (x8) | `LA0-LA7` front | |
| 10d. | Resistor 3K ohm (x8) | `R24-R31` front | |
| 11d. | Test Lead | [TEST STEP] | |
| 9e. | LED Red 5mm (x8) | `LD0-LD7` front | |
| 10e. | Resistor 3K ohm (x8) | `R52-R59` front | |
| 11e. | Test Lead | [TEST STEP] | |
| 9f. | LED Red 5mm (x4) | `LHT1, LWT1, LRN1, LIE1` front | |
| 10f. | Resistor 3K ohm (x4) | `R48-R51` front | |
| 11f. | Test Lead | [TEST STEP] | |

### Other Resistors, Capacitors, IC sockets & Miscellaneous Parts

::: warning Note
The transistor `Q1` and the accompanying Resistor `R13` are **optional**. They are a convenience for flashing new firmware on the ESP32-PICO-KIT over USB without removing it from the IMSAI 8080esp PCB. However, on their own they do not provide the whole solution and two extra jumper wires are required to be directly soldered to component leads on the ESP32-PICO-KIT board (details to follow). The simple alternative is to remove the ESP32-PICO-KIT  from the IMSAI 8080esp PCB before flashing new firmware over USB, or more simply use the drag-and-drop, over-the-air (OTA) firmware update procedure via the Desktop UI (details to follow).
:::

| Step | Parts | Location | Notes |
| ---: | ----- | -------- | ----- |
| 12. | Resistor 10K ohm | `R1-R12` front | Resistors are **not** polarized and can be inserted & soldered either way around. Because of my sense of aesthetic (ok, my OCD) I like to orientate them all the same way according to the coloured bands. |
| 13. | Resistor 10K ohm | `R13` back | *(Optional) See note above.* |
| 14. | Capacitor 100nF (0.1μF, 104) | `C3-C12, C17` front | These capacitors are **not** polarized and can be inserted & soldered either way around. |
| 15. | Capacitor 100nF (0.1μF, 104) | `C2, C13-C16` back | These capacitors are **not** polarized and can be inserted & soldered either way around. |
| 16. | 16 pin DIP Socket (x10) | `U1-U10` front | DIP sockets should be inserted to align the crescent/indent at one end with the corresponding mark in the silk screen for the IC Socket. This makes no difference functionally, but will help with the inserting the ICs with the correct orientation later in the assembly. |
| 17. | 16 pin DIP Socket | `U11` back | DIP sockets should be inserted to align the crescent/indent at one end with the corresponding mark in the silk screen for the IC Socket. This makes no difference functionally, but will help when inserting the ICs with the correct orientation later in the assembly. |
| 18. | S8050 NPN Transistor| `Q1` back | *(Optional) See note above.* |
| 19. | Tactile Switch SPST-NO | `Reset` front | *Note: don't rely only on the 2 soldered connector pins to secure the switch to the PCB, also solder in the 2 mounting pegs to ensure a secure connection to the PCB* |
| 20. | Header 4x2 Male | `Boot` back | |
| 21. | Header 8x2 Male | `Patch` back | |
| 22. | Header 8x2 Male | `Comms` back | |
| 23. | DE9 (DB9) Male Socket (x2) | `RS232-1, RS232-2` back | *Note: don't rely only on the 9 soldered connector pins to secure a socket to the PCB, also solder in the 2 mounting pegs to ensure a secure connection to the PCB* |

### Inserting the ICs

::: danger
If you fail to insert the ICs at this step, before proceeding to insert and solder the rocker/toggle switches, you will find that you cannot later insert some of the ICs without bending the switches. I have done this, to prove that it can be done, but I do not recommend it.
:::

::: danger
**ICs are polarized/directional and must be inserted in the correct orientation.** ICs should be inserted to align the crescent/indent at one end with the corresponding mark in the silk screen. If you have soldered in the **16 pin DIP Sockets** with the indicated orientation, this will make the job easier.
:::

| Step | Parts | Location | Notes |
| ---: | ----- | -------- | ----- |
| 24. | 74HC595 (x6) | `U1-U6` front | `U1-U6` are all oriented the same way, with the crescent/indent to the **right** when looking at the **front** of the PCB. |
| 24. | 74HC74HC165 (x4) | `U7-U10` front | `U7-U10` are all oriented the same way, with the crescent/indent to the **right** when looking at the **front** of the PCB. |
| 25. | MAX3232 | `U11` back | `U11` is oriented with the crescent/indent to the **left** when looking at the **back** of the PCB. |

## Testing

::: tip
At this point you can operate the IMSAI 8080esp without having the rocker/toggle switches mounted.

- Plug the ESP32-PICO-KIT into the female connectors on the **back** of the PCB. 
- *Note: The USB connecter should be towards the near edge of the PCB and the WiFi antenna towards the RS232 connectors.*
- Insert the microSD card.
- Connect the ESP32-PICO-KIT to a USB power source with a suitable USB cable.
- The simulation will not start until you short the centre and top pins of switch `S1`

You can connect to the web based desktop UI by connecting a PC to the Wi-Fi SSID advertised as `IMSAI8080`. Because the Wi-Fi has not been configured, the IMSAI 8080esp should have rebooted into Wi-Fi fallback mode, where it acts as an **Access-Point (AP)** with the default SSID of `IMSAI8080`. Once you are connected to this Wi-Fi network, start a Chrome browser and enter the URL `http://imsai8080.local`.

There are (or will be) separate instructions for configuring the Wi-Fi to connect to you local Wi-Fi network.

You can use the virtual `CPA:` device to toggle the `RUN/STOP` switch.
:::

::: warning
While you can operate the IMSAI 8080esp at this point, it will no do much for you without some further configuration. The default configuration is like an empty machine with no ROM only RAM, and you don't have a full frontpanel to play with. Damn!
Configuration is (or will be covered elsewhere).
:::

## To Be Continued... 

::: tip
Time for a cup of tea if you've gotten this far.
:::