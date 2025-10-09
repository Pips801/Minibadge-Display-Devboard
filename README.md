# Minibadge Devboard
A small PCB that allows you to create your own Minibadge displays!

<img height="500" alt="image" src="https://github.com/user-attachments/assets/ab08be7f-1882-463b-b7bd-d60ec6992621" /> <img height="500" alt="image" src="https://github.com/user-attachments/assets/c4474a9e-028e-46b3-9f72-89c954e33307" />

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

# Cost breakdown

### BOM
| Vendor          | Item                   | Item total | Item quantity | Per item cost | Per unit cost | Per unit required |
| --------------- | ---------------------- | ---------- | ------------- | ------------- | ------------- | ----------------- |
| JLC PCB         | Board                  | $11.00     | 50            | $0.22         | $0.22         | 1                 |
| JLC PCB         | Engineering fee        | $8.00      | 50            | $0.16         | $0.16         | 1                 |
| JLC PCB         | Film                   | $1.30      | 50            | $0.03         | $0.03         | 1                 |
| JLC PCB         | Castellated holes      | $49.90     | 50            | $1.00         | $1.00         | 1                 |
| JLC PCB         | Confirm                | $1.00      | 50            | $0.02         | $0.02         | 1                 |
| JLC PCB         | Packaging              | $0.71      | 50            | $0.01         | $0.01         | 1                 |
| JLC Assembly    | Setup fee              | $25.00     | 50            | $0.50         | $0.50         | 1                 |
| JLC Assembly    | Components (passive)   | $9.78      | 50            | $0.20         | $0.20         | 1                 |
| JLC Assembly    | Extended component fee | $30.00     | 50            | $0.60         | $0.60         | 1                 |
| JLC Assembly    | Assembly               | $10.12     | 50            | $0.20         | $0.20         | 1                 |
| JLC Assembly    | Pckaging fee           | $0.47      | 50            | $0.01         | $0.01         | 1                 |
| JLC Parts       | Primary components     | $81.65     | 50            | $1.63         | $1.63         | 1                 |
| Shipping        | Shipping               | $48.49     | 50            | $0.97         | $0.97         | 1                 |
| Tariffs & taxes | Customs                | $133.58    | 50            | $2.67         | $2.67         | 1                 |
| Tariffs & taxes | State sales tax        | $20.00     | 50            | $0.40         | $0.40         | 1                 |

### Final costs
| Project total cost | Per unit total cost | Quantity | Adjusted total | Adjusted per unit cost |
| ------------------ | ------------------- | -------- | -------------- | ---------------------- |
| $431.00            | $8.62               | 50       | $431.00        | $8.62                  |

### Cost by vendor
<img width="727" height="449" alt="chart (5)" src="https://github.com/user-attachments/assets/339ea21a-02ee-440d-baa3-8cc222f8c7ec" />

### Cost by item
<img width="727" height="449" alt="chart (6)" src="https://github.com/user-attachments/assets/5d48941a-c570-49a0-b5ee-af6a720563e7" />
