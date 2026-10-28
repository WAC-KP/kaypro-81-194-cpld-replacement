# kaypro-81-194-cpld-replacement
Replacement for the 1984 Kaypro Universal Board 81-194 LSI using an ATF1504 CPLD, AS6C1008 SRA and 16 mHz oscillator.

## License

This project is licensed under the **GNU General Public License v3.0 (GPLv3)**. 

### What this means for the community:
- **You are free** to download, build, modify, and use these schematics, Gerbers, and CPLD code for your own Kaypro computers.
- **You can manufacture** these replacement boards for yourself or sell them to other hobbyists.
- **CRITICAL CONDITION:** If you modify the CPLD code or the PCB layout and choose to distribute or sell your new version, **you are legally required to make your modified source code and hardware design files publicly available** under this exact same GPLv3 license. 

For the full legal text, see the accompanying `LICENSE` file.

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


