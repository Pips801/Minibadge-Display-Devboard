# Minibadge Display Devboard
A small PCB that allows you to create your own Minibadge displays!

This board provides everything your custom Minibadge display will need, including LiPo battery charging/use and USB-C power. It can be attached board-to-board with your own PCB designs, or it can be wired up using push-in WAGO wire terminals to your existing displays.

<img height="300" alt="image" src="https://github.com/user-attachments/assets/c2eb49ee-c9d9-45e6-97a8-a0418281feec" /> <img height="300" alt="image" src="https://github.com/user-attachments/assets/c30dee54-9d2b-4e41-8131-5ae0eadc6ca4" />


## Datasheets
* Voltage regulator - TLV62585RWT - https://www.ti.com/lit/ds/symlink/tlv62585.pdf
* Battery management system - BQ21040 - https://www.ti.com/lit/ds/symlink/bq21040.pdf
* Clock generator - 74HC4060 - https://assets.nexperia.com/documents/data-sheet/74HC_HCT4060.pdf
* Clock driver - DRV8837C - https://www.ti.com/lit/ds/symlink/drv8837c.pdf
* Powepath MUX - TPS2121 - https://www.ti.com/lit/ds/symlink/tps2121.pdf

# Specifications
* Provides your Minibadges battery or USB-C power, 3.3v@3A, CLK, GND, and VBATT.
* Supports LiPo batteries, optionally with NTC temp sensors.
  * 2x LiPo batteries of matching composition, mAh, and charge state can be wired in parallel.
  * 800mA battery charging.
* Features castellated edge-mount pads for direct board to board connections.
* Features WAGO PCB terminal blocks for custom wiring.
* Power switch disconnects minibadges while still powering the battery charging circuit.
* Solderable jumper for disabling temp sensor and selecting CLK speed.

# Limitations
* Input (USB-C): 5V@3A
* Input (Battery): 4.2V@3A
* Battery charging: 4.2V@800mA
* Output (3.3V): 3.3V@3A
* Output (CLK): 3.3V@3A
* Output (SYS): Input voltage@amperage (whichever is higher)
* Max total minibadges: 30-50

R2 Update list
* Better thermal management for voltage regulators under load.
* Updated PMIC ORing power path chip, replacing dual ORing diodes.
* Updated PFET for power on/off switching and system load capacity.
* Better thermal management for PFET under load.
* Improved current flow and reduced waste heat for CLK driver.
* Thicker power traces for 3.3v regulators and Battery.
* Updated silkscreen component markers.
* Updated solder paste for stronger on/off switch mounting.

R3 Update list
* Larger castellated pads for better connection.
* Addition of a second row of pads for pins.
* Swap from 3x LDO regulators to 1x Buck regulator.
* Decreased waste heat and better thermal management.
* Shhrunk board height by 2.54mm.
* Added technical limitations on silkscreen.

# Designing a Minibadge display
### Setup
* Import Minibadge footprints and symbols into KiCad.
* Import DevBoard footprint and symbol into KiCad.

### Schematic
* Create schematic with as many minibadges as you want.
* Import the Devboard symbol and wire up CLK, GND, and SYS (VBATT/5V).
* Wire up the minibadges 3.3v lines.

<img height="400" alt="image" src="https://github.com/user-attachments/assets/5cee3f1c-dd95-44ab-9998-e44554d591dc" />

### PCB
* Arrange all of your minibadges.
* Finalize your board shape.
* Place the Devboard on the back of the PCB with the USB port against the edge of your board.
* Wire up your CLK, GND, 3x 3.3v, and SYS (VBATT/5V)

<img height="400" alt="image" src="https://github.com/user-attachments/assets/203cdfca-c7ca-4586-b22b-4565289f8a69" /> <img height="400" alt="image" src="https://github.com/user-attachments/assets/22d00681-0fd2-455b-b95d-9b6c29cf2159" />

# Assembly
1. Solder the `SPEED` jumper to select the Clock frequency. F for Fast, S for Slow.
2. Solder or attach (through the WAGO) your battery positive and negative leads.
3. If your battery has an NTC temperature wire (third wire, usually white or yellow) connect it to the NTC pad or terminal. Solder the `NTC` jumper to `Y` (Yes NTC)
4. If your battery does not have an NTC temperature wire, solder the `NTC` jumper to the `N` (No NTC) position.
5. Solder or wire up your 3 different 3.3v lines from your display board.
6. Solder or wire up GND, SYS (VBATT/5V), and CLK to the appropriate connections on your display.
