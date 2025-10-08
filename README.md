# Minibadge Devboard
A small PCB that allows you to create your own Minibadge displays!
<img height="400" alt="image" src="https://github.com/user-attachments/assets/c6deb0ff-0d1e-41c5-94de-63858753c2ca" /> <img height="400" alt="image" src="https://github.com/user-attachments/assets/c4474a9e-028e-46b3-9f72-89c954e33307" />

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

# Designing a Minibadge display
### Setup
* Import Minibadge footprints and symbols into KiCad.
* Import DevBoard footprint and symbol into KiCad.

### Schematic
* Create schematic with as many minibadges as you want.
* Import the Devboard symbol and wire up CLK, GND, and SYS (VBATT/5V).
* Wire up the minibadges 3.3v lines to evenly distribute the 3.3v load across the regulators.

### PCB
* Arrange all of your minibadges.
* Finalize your board shape.
* Place the Devboard on the back of the PCB with the USB port against the edge of your board.
* Wire up your CLK, GND, 3x 3.3v, and SYS (VBATT/5V)

# Assembly
1. Solder the `SPEED` jumper to select the Clock frequency. F for Fast, S for Slow.
2. Solder or attach (through the WAGO) your battery positive and negative leads.
3. If your battery has an NTC temperature wire (third wire, usually white or yellow) connect it to the NTC pad or terminal. Solder the `NTC` jumper to `Y` (Yes NTC)
4. If your battery does not have an NTC temperature wire, solder the `NTC` jumper to the `N` (No NTC) position.
5. Solder or wire up your 3 different 3.3v lines from your display board.
6. Solder or wire up GND, SYS (VBATT/5V), and CLK to the appropriate connections on your display.


