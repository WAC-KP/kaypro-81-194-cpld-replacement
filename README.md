# kaypro-81-194-cpld-replacement
Replacement for the 1984 Kaypro Universal Board 81-194 LSI using an ATF1504 CPLD, AS6C1008 SRAM and 16 mHz oscillator.

## License

This project is licensed under the **GNU General Public License v3.0 (GPLv3)**. 

### What this means for the community:
- **You are free** to download, build, modify, and use these schematics, Gerbers, and CPLD code for your own Kaypro computers.
- **You can manufacture** these replacement boards for yourself or sell them to other hobbyists.
- **CRITICAL CONDITION:** If you modify the CPLD code or the PCB layout and choose to distribute or sell your new version, **you are legally required to make your modified source code and hardware design files publicly available** under this exact same GPLv3 license. 

For the full legal text, see the accompanying `LICENSE` file.

## Why this project

A while back I purchased a nonworking Kaypro 2x as a parts computer. It was dirty and many of the screws were rusting. The keyboard jack was broken. The power supply was broken (literally). Otherwise everything else looked good. Comparison to a working 2x revealed a few bad RAM chips and the corrupted 81-194 LSI. Replacing the faulty ram and borrowing a working 81-194 resulted in a fully functional Kaypro 2X. 

A web search revealed no viable solutions to the dead LSI chip. So I asked AI for help. At the suggestion (urging) of AI and to simplify code, the design moved away from RAM to SRAM. The end result was a working, stable Kaypro 2x. 

Was it worth it? Perhaps, perhaps not. You can still find universal board Kaypros, working or not. Prototype PCBs are not too expensive until you add in shipping. Parts are reasonable but all combined you might just get lucky and find another Kaypro for less than the parts and labor.

That said, I believe it was worth it, simply based on the learning process and the side result of a functional Kaypro.


## Downloads & Project Files

Instead of hunting through folders, you can access the core design files for this project directly using the links below:

### 🛠️ Hardware & PCB Fabrication
* **Schematic Diagram:** [View or Download Schematic PDF](hardware/Version%201/u29-1504.pdf)
* **Gerber Files V1:** [Download V1 PCB Fabrication ZIP](hardware/Version%201/production/u29-1504.zip)
* **Gerber Files V2:** [Download V2 PCB Fabrication ZIP](hardware/Version%202/production/u29-1504.zip)
* *Note: The Gerber ZIP file can be uploaded directly to manufacturing services like JLCPCB, PCBWay, or OSH Park. Version 2 is just a repositioning of components.



### 💾 Firmware & Source Code
* **CPLD Source Code:** [ATF1504 PLD Source Code](firmware/KAYPRO_SRAM_CTRL-6.pld)
* **Compiled JEDEC File:** [Ready-to-Program JED file](firmware/KAYPRO_SRAM_CTRL-6.jed)
* **Compiled svf File:** [Ready-to-Program svf file](firmware/KAYPRO_SRAM_CTRL-6.svf)
* *Note: Use the `.jed` file directly with your USB Blaster and the ATF15xx ISP software to program the chip.*
* *Note: Use the `.svf` file directly with your modified USB Blaster Clone and UrJTAG or OpenOCD software to program the chip.*

---

## Building and installing

* The PCB is designed to replace both U29 (81-194) and U55 (74LS373). Separate the PCB into the two daughter boards and mount the components. The two boards are connected by a 16 wire ribbon cable.
* A single RST connection is provided (see the PCB)
* To minimize risk of socket damage only use rounded header pins designed for interfacing with DIP sockets. 
* 0805 surface mount capacitors and resistors are used to help reduce clutter and they can still be hand soldered. 
* External power pins can be used to supply the required 5v for programming the CPLD or the CPLD can be programmed with the board installed. 
* A heartbeat LED is provided as a visual indicator of functioning AFT1504.  


### Compiling pld with WinCUPL II
 &emsp;cupl.exe -m1l -age -b -u PATH_TO\atmel.lib KAYPRO_SRAM_CTRL-6.pld  
 &emsp;fit1504.exe KAYPRO_SRAM_CTRL-6.tt2 -device PLCC44 -preassign keep -jtag on  
 

### Programming ATF1504AS with UrJtag
 &emsp;run JTAG  
  &emsp;&emsp;jtag> cable usbblaster  
  &emsp;&emsp;jtag> detect  
  &emsp;&emsp;jtag> part 0  
  &emsp;&emsp;jtag> instruction length 10  
  &emsp;&emsp;jtag> svf PATH_TO/KAYPRO_SRAM_CTRL-6.svf  
  &emsp;&emsp;&emsp;(programming may take a few minutes)


---  

### Resources
 - [USB Blaster Clone rev, C](https://www.amazon.com/dp/B07F5H5LPZ).
     - [Fixing a knockoff Altera USB Blaster that never worked](https://www.downtowndougbrown.com/2024/06/fixing-a-knockoff-altera-usb-blaster-that-never-worked/)
     - [Firmware binary file](https://github.com/dsm/USB-Blaster_CH552)
     - [WCHISPStudio](https://www.wch-ic.com/download/file?id=196)
 - [Microchip WinCUPL Product Page](https://www.microchip.com/en-us/development-tool/wincupl)
 - [ATMISP 7.3.1 Download (ZIP)](https://ww1.microchip.com/downloads/aemDocuments/documents/MPD/SoftwareLibrary/ATMISP_v7_3_1.zip)
 - [UrJTAG](https://urjtag.sourceforge.io/)
 - [OpenOCD](https://openocd.org/)


## ⚠️ Kaypro Hardware & Installation Disclaimer

**CRITICAL WARNING:** This project involves modifying vintage computing equipment by directly interfacing with IC sockets. Incorrect installation or software faults can permanently destroy period-hard-to-find chips and logic boards. Use this software and hardware at your own risk.

In addition to the terms outlined in the GNU General Public License v3.0 (GPL-3.0):

* **Socket Interfacing Risk:** This software/hardware is designed to interface specifically with DIP sockets **U29** and **U55** on the **Kaypro Universal Board**. You assume all risk for incorrect orientation, bent pins, misaligned rows, or plugging into incorrect IC locations.
* **Electrical & Component Damage:** The authors and contributors shall not be held liable for any direct or indirect damage to your Kaypro mainboard, power supply (including original astec/riffa capacitors), CRT circuitry, or vintage components resulting from data corruption, improper timing signals, or logic states generated by this software.
* **Verification Required:** Ensure your board layout matches the Kaypro Universal Board configuration (e.g., Kaypro 2X, 4/84, 10) and verify all voltages before powering on the machine with this modification installed. 
