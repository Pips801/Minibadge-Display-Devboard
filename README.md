# Minibadge Display Devboard
A small PCB that allows you to create your own Minibadge displays!

This board provides everything your custom Minibadge display will need, including LiPo battery charging/use and USB-C power. It can be attached board-to-board with your own PCB designs, or it can be wired up using push-in WAGO wire terminals to your existing displays.

<img height="300" alt="image" src="https://github.com/user-attachments/assets/1c8e9991-1674-4dec-916b-945449384d05" /> <img height="300" alt="image" src="https://github.com/user-attachments/assets/d3120153-20b2-4f65-b784-882e05701e09" />

## Datasheets
* Voltage regulators - TPS2121 - https://www.ti.com/lit/ds/symlink/tps2121.pdf
* Battery Management System - BQ21040 - https://www.ti.com/lit/ds/symlink/bq21040.pdf
* Clock Generator - AP7361C-33E - https://www.diodes.com/assets/Datasheets/AP7361C.pdf
* Clock Driver - 74HC4060 - https://assets.nexperia.com/documents/data-sheet/74HC_HCT4060.pdf
* Powepath MUX - DRV8837C - 
* Power PFET

# Specifications
* Provides your Minibadges battery or USB-C power, 3x 3.3v@1A, CLK, GND, and VBATT.
* Supports LiPo batteries, optionally with NTC temp sensors.
  * 2x LiPo batteries of matching composition, mAh, and charge state can be wired in parallel.
  * 800mA battery charging.
* Features castellated edge-mount pads for direct board to board connections.
* Features WAGO PCB terminal blocks for custom wiring.
* Power switch disconnects minibadges while still powering the battery charging circuit.
* Solderable jumper for disabling temp sensor and selecting CLK speed.

# Limitations
* Max power draw (USB-C): 5V@3A
* Max battery charging current: 800mA
* Max amperage per 3.3v regulator: 1A
* Max minibadges per 3.3v regulator (estimated): 10
* Max total minibadges (estimated): 30-40
* CLK is powered by VREG1.
 * If you plan on having a lot of CLK current, do not connect minibadges 3.3v rail to 3.3v-1. Only connect them to 3.3v-2 and 3.3v-3.

R2 Update list
* Better thermal management for voltage regulators under load.
* Updated PMIC ORing power path chip, replacing dual ORing diodes.
* Updated PFET for power on/off switching and system load capacity.
* Better thermal management for PFET under load.
* Improved current flow and reduced waste heat for CLK driver.
* Thicker power traces for 3.3v regulators and Battery.
* Updated silkscreen component markers.
* Updated solder paste for stronger on/off switch mounting.

# Designing a Minibadge display
### Setup
* Import Minibadge footprints and symbols into KiCad.
* Import DevBoard footprint and symbol into KiCad.

### Schematic
* Create schematic with as many minibadges as you want.
* Import the Devboard symbol and wire up CLK, GND, and SYS (VBATT/5V).
* Wire up the minibadges 3.3v lines to evenly distribute the 3.3v load across the regulators.

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
