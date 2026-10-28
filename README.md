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
* **Schematic Diagram:** [View or Download Schematic PDF](hardware/Version 1/u29-1504.pdf)
* **Gerber Files:** [Download V.1 PCB Fabrication ZIP](hardware/Version 1/production/u29-1504.zip)
* **Gerber Files:** [Download V.2 PCB Fabrication ZIP](hardware/Version 2/production/u29-1504.zip)
* *Note: The Gerber ZIP file can be uploaded directly to manufacturing services like JLCPCB, PCBWay, or OSH Park.*

### 💾 Firmware & Source Code
* **CPLD Source Code:** [ATF1504 PLD Source Code](firmware/KAYPRO_SRAM_CTRL-6.pld)
* **Compiled JEDEC File:** [Ready-to-Program JED file](firmware/KAYPRO_SRAM_CTRL-6.jed)
* **Compiled svf File:** [Ready-to-Program svf file](firmware/KAYPRO_SRAM_CTRL-6.svf)
* *Note: Use the `.jed` file directly with your USB Blaster and the ATF15xx ISP software to program the chip.*
* *Note: Use the `.svf` file directly with your modified USB Blaster Clone and UrJTAG (https://urjtag.sourceforge.io/) or OpenOCD (https://openocd.org/) software to program the chip.*
