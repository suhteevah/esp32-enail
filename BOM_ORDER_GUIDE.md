# ESP-Nail - Order-Ready Bill of Materials

**Last updated**: 2026-03-20
**Build target**: Model S (single channel) - scale quantities for D (2ch) or Q (4ch)

---

## CORE ELECTRONICS

### 1. ESP32 DevKit V1 (38-pin)
- **Qty**: 1
- **Amazon**: https://www.amazon.com/dp/B08D5ZD528
- **Alt (3-pack, better value)**: https://www.amazon.com/dp/B09GK74F7N
- **Price**: ~$7-10 (single), ~$18 (3-pack)
- **Notes**: Must be 38-pin version. CP2102 or CH340 USB chip both work. Get the 3-pack - you'll want a spare.

### 2. SSD1306 0.96" OLED Display (I2C, 128x64)
- **Qty**: 1
- **Amazon**: https://www.amazon.com/dp/B08CDN5PSJ
- **Alt (2-pack)**: https://www.amazon.com/dp/B09C5K91H7
- **Price**: ~$6-8 (2-pack)
- **Notes**: Get the **I2C** version (4 pins: VCC, GND, SCL, SDA), NOT SPI (7 pins). White or blue, doesn't matter. Address 0x3C.

### 3. KY-040 Rotary Encoder Module
- **Qty**: 1
- **Amazon**: https://www.amazon.com/dp/B06XQTHDRR
- **Alt (5-pack)**: https://www.amazon.com/dp/B07DM2YMT4
- **Price**: ~$6-9 (5-pack)
- **Notes**: Get the module version with the breakout PCB (5 pins). Has built-in 10k pullups. Grab the 5-pack, they're cheap and fragile.

### 4. MAX31855 K-Type Thermocouple Amplifier Breakout
- **Qty**: 1 per channel (1/2/4)
- **Amazon (Adafruit genuine)**: https://www.amazon.com/dp/B00SK8NDAI
- **Amazon (generic, cheaper)**: https://www.amazon.com/dp/B0BW2G32Y1
- **Price**: ~$10-15 (Adafruit), ~$5-8 (generic)
- **Notes**: The Adafruit ones are rock solid. Generic works fine too. Must be MAX31855 (NOT MAX6675 - different SPI protocol). Includes screw terminals for thermocouple wires.

### 5. SSR-25DA Solid State Relay
- **Qty**: 1 per channel (1/2/4)
- **Amazon**: https://www.amazon.com/dp/B08FR13GYR
- **Alt (with heatsink)**: https://www.amazon.com/dp/B0CXKXK6XN
- **Price**: ~$8-12 each, ~$10-15 with heatsink
- **Notes**: 3-32VDC input, 24-380VAC output, 25A rating. **Genuine SSRs matter here** - cheap Fotek counterfeits are a fire hazard. Look for ones with the UL listing. The combo with heatsink is the move.

### 6. SSR Heatsink (if not buying combo above)
- **Qty**: 1 per channel
- **Amazon**: https://www.amazon.com/dp/B07YWLMXPK
- **Price**: ~$4-6 each
- **Notes**: Aluminum fin-type. Must fit standard SSR footprint. Apply thermal paste between SSR and heatsink.

### 7. 5-Pin Mini-XLR Female Panel-Mount (NC5FD-L-1 or equivalent)
- **Qty**: 1 per channel (1/2/4)
- **Amazon (Neutrik genuine)**: https://www.amazon.com/dp/B013SQ5138
- **Amazon (generic 5-pin XLR)**: https://www.amazon.com/dp/B0DL2LCGMP
- **Price**: ~$5-8 (Neutrik), ~$3-5 (generic)
- **Notes**: MUST be 5-pin mini-XLR female panel-mount. This is the industry standard connector for e-nail coils. Neutrik is the gold standard but generics work. Solder-cup contacts. If you search "5 pin mini XLR female panel mount" you'll find them.

---

## POWER COMPONENTS

### 8. IEC C14 Fused Inlet with Rocker Switch
- **Qty**: 1
- **Amazon**: https://www.amazon.com/dp/B07DJ2K9V8
- **Alt (3-pack)**: https://www.amazon.com/dp/B09TVFJ9M5
- **Price**: ~$4-8
- **Notes**: Snap-in mount. Has integrated 10A fuse holder and on/off rocker switch. The JR-101-1FR style. Comes with a fuse usually.

### 9. HLK-PM01 AC-DC 5V Converter Module
- **Qty**: 1
- **Amazon**: https://www.amazon.com/dp/B0BHKCCTYF
- **Alt**: https://www.amazon.com/dp/B09X22MR2D
- **Price**: ~$5-8
- **Notes**: Hi-Link HLK-PM01. Converts 110-240VAC to 5V DC, 600mA. Fully isolated. This powers the ESP32. **Do NOT substitute with a non-isolated buck converter** - you're working with mains voltage.

### 10. 10A 5x20mm Glass Fuses (spare)
- **Qty**: 2 (1 installed in inlet + 1 spare)
- **Amazon**: https://www.amazon.com/dp/B09WDGBQ9S
- **Price**: ~$6 (20-pack assortment)
- **Notes**: 250V rated, fast-blow. The IEC inlet usually comes with one, but grab spares.

---

## DISCRETE COMPONENTS (SSR DRIVER CIRCUIT)

### 11. 2N2222A NPN Transistor (TO-92)
- **Qty**: 1 per channel + spares
- **Amazon**: https://www.amazon.com/dp/B09YH2D3JJ
- **Price**: ~$6 (50-pack)
- **Notes**: TO-92 through-hole package. Used as buffer between ESP32 3.3V GPIO and 5V SSR input. Any generic 2N2222A or PN2222A works. You'll have plenty of spares.

### 12. Resistor Kit (1k, 4.7k, 10k needed)
- **Qty**: Need 1k (per channel), 4.7k (x2), 10k (per channel + 1)
- **Amazon**: https://www.amazon.com/dp/B08FD1XVL6
- **Price**: ~$7-10 (full kit)
- **Notes**: A 1/4W through-hole resistor assortment kit covers all needs:
  - **1k ohm**: SSR driver base resistor (1 per channel)
  - **4.7k ohm**: I2C pullup resistors (2 total, SDA + SCL)
  - **10k ohm**: MAX31855 CS pullups (1 per channel) + encoder SW pullup (1 total)

### 13. Capacitor Kit (100nF ceramic + 100uF electrolytic)
- **Amazon (ceramic 100nF)**: https://www.amazon.com/dp/B007MOGT7E
- **Amazon (electrolytic assortment)**: https://www.amazon.com/dp/B07PBQXQNQ
- **Price**: ~$6-8 each
- **Notes**: Need 100nF ceramics for decoupling (1 per MAX31855 + 2 for rails = 3-6 total) and 100uF electrolytics for bulk filtering (2 total, 5V + 3.3V rail).

---

## WIRE AND CONNECTORS

### 14. 16AWG Silicone Wire (Red + Black)
- **Qty**: 3m for 1ch, 5m for 2ch, 8m for 4ch
- **Amazon**: https://www.amazon.com/dp/B01AAX64EC
- **Price**: ~$11-14 (10ft each red+black)
- **Notes**: **MUST be 16AWG minimum for AC mains wiring**. Silicone insulation handles heat well. Get red and black.

### 15. 22AWG Hookup Wire (assorted colors)
- **Qty**: 2-5m depending on channel count
- **Amazon**: https://www.amazon.com/dp/B07TX6BX47
- **Price**: ~$15 (kit with multiple colors)
- **Notes**: For all signal wiring: SPI to MAX31855, I2C to OLED, encoder connections. Multiple colors help keep things organized.

### 16. Heat Shrink Tubing Kit
- **Qty**: 1 assortment
- **Amazon**: https://www.amazon.com/dp/B084GDLSCK
- **Price**: ~$7-10
- **Notes**: Assorted sizes 1.5mm-10mm. Use on ALL solder joints, especially AC connections. 2:1 shrink ratio.

### 17. Ring Terminals (16AWG, M3)
- **Qty**: 4-10 depending on channel count
- **Amazon**: https://www.amazon.com/dp/B09DYFXTMZ
- **Price**: ~$7-9 (assortment)
- **Notes**: For grounding bus connections. Crimp AND solder for secure PE earth connections.

### 18. M3 Hardware Kit (screws, nuts, standoffs)
- **Qty**: 1 kit
- **Amazon**: https://www.amazon.com/dp/B0B2T5C8JH
- **Alt (nylon standoffs for PCB)**: https://www.amazon.com/dp/B07D78QL64
- **Price**: ~$8-12
- **Notes**: Need M3x8 and M3x12 screws, nuts, and standoffs for mounting the PCB, SSR, display, and encoder. ~20 screws + nuts + 8 standoffs.

---

## OPTIONAL BUT RECOMMENDED

### 19. ACS712-05B Current Sensor Module
- **Qty**: 0-1 per channel (optional)
- **Amazon**: https://www.amazon.com/dp/B01AFBKVPG
- **Price**: ~$3-5 each
- **Notes**: 5A hall-effect current sensor. Monitors coil current draw. Useful for detecting coil failures or shorts. Analog output to GPIO 36.

### 20. BME280 I2C Sensor Module
- **Qty**: 0-1 (optional)
- **Amazon**: https://www.amazon.com/dp/B0BN2JN4RY
- **Price**: ~$5-8
- **Notes**: Temperature/humidity/pressure sensor for ambient monitoring. Shares I2C bus with OLED. Address 0x76 or 0x77.

### 21. USB-C Female Breakout Board
- **Qty**: 1
- **Amazon**: https://www.amazon.com/dp/B09BRJ3KHP
- **Price**: ~$6-8 (pack)
- **Notes**: Panel-mount USB-C breakout so you can reprogram the ESP32 without opening the enclosure. Wire VCC/D+/D-/GND to ESP32's USB port.

---

## EXTERNAL / HEATING COMPONENTS

### 22. E-Nail Heating Coil (with 5-pin XLR plug)
- **Qty**: 1 per channel
- **Amazon**: https://www.amazon.com/s?k=enail+coil+5+pin+xlr
- **Price**: ~$25-65 depending on size/brand
- **Sizes**: 10mm, 16mm, 20mm, 25mm, 30mm barrel
- **Notes**: Must have integrated K-type thermocouple and 5-pin XLR male plug. Compatible with Fancier, Auber, and most standard e-nail controllers. 20mm is the most common size.

### 23. IEC C14 Power Cable
- **Qty**: 1
- **Amazon**: https://www.amazon.com/dp/B072BYGKZZ
- **Price**: ~$6-8
- **Notes**: Standard PC/monitor power cable. 3-prong to IEC C14. You probably have a few lying around already.

---

## ENCLOSURE (pick one)

### Option A: 3D Printed (cheapest)
- **Material**: PETG filament (~$20/kg)
- **Cost**: ~$5-15 in filament
- **Notes**: Print from the included .scad/.stl files. PETG recommended over PLA for heat resistance. 0.2mm layers, 30% infill, 3 perimeters.

### Option B: Project Enclosure Box (no printer needed)
- **Amazon**: https://www.amazon.com/dp/B0BYP58BYT
- **Price**: ~$10-20
- **Notes**: ABS project box, ~200x120x75mm. You'll need to drill/cut holes for the XLR connectors, IEC inlet, OLED, and encoder. Works great with a step drill bit.

---

## TOOLS YOU'LL NEED

If you don't already have these:

| Tool | Amazon | Price |
|------|--------|-------|
| Soldering Iron Kit | https://www.amazon.com/dp/B07S61WT16 | ~$15-25 |
| Wire Strippers | https://www.amazon.com/dp/B000XEUPMQ | ~$8-12 |
| Crimping Tool (for ring terminals) | https://www.amazon.com/dp/B0188DJ6LI | ~$10-15 |
| Multimeter | https://www.amazon.com/dp/B01ISAMUA6 | ~$15-20 |
| Solder (60/40 or 63/37) | https://www.amazon.com/dp/B075WB98FJ | ~$8-10 |
| Thermal Paste (for SSR heatsink) | https://www.amazon.com/dp/B09NRGFLF6 | ~$7 |
| Step Drill Bit (for enclosure holes) | https://www.amazon.com/dp/B08BFCQ33N | ~$10-15 |

---

## ORDER SUMMARY - Model S (Single Channel)

| # | Item | Est. Cost |
|---|------|-----------|
| 1 | ESP32 DevKit (3-pack) | $18 |
| 2 | OLED Display (2-pack) | $7 |
| 3 | Rotary Encoder (5-pack) | $7 |
| 4 | MAX31855 Breakout | $8 |
| 5 | SSR-25DA + Heatsink combo | $12 |
| 6 | 5-Pin Mini-XLR Female | $6 |
| 7 | IEC C14 Fused Inlet | $5 |
| 8 | HLK-PM01 5V Converter | $6 |
| 9 | Fuses (spare pack) | $6 |
| 10 | 2N2222A Transistors (pack) | $6 |
| 11 | Resistor Kit | $8 |
| 12 | Capacitor Kits | $14 |
| 13 | 16AWG Silicone Wire | $12 |
| 14 | 22AWG Hookup Wire | $15 |
| 15 | Heat Shrink Kit | $8 |
| 16 | Ring Terminals | $8 |
| 17 | M3 Hardware Kit | $10 |
| 18 | USB-C Breakout (optional) | $7 |
| 19 | Project Enclosure Box | $15 |
| 20 | E-Nail Coil (20mm) | $35 |
| 21 | IEC Power Cable | $7 |
| | **TOTAL** | **~$220** |

**Note**: Total is higher than pure "per-unit" BOM cost because you're buying packs/kits with spares. Your actual per-unit component cost is ~$65-80 for a single channel build. The extra parts will cover future builds or replacements.

---

## SAFETY REMINDERS

- **This project works with mains voltage (120/240VAC).** Respect it.
- Always use 16AWG minimum for AC wiring
- Double-check SSR orientation before powering on (DC side vs AC side)
- Fuse MUST be on the LINE (hot) side
- All metal parts must be bonded to earth ground (PE)
- Test with a multimeter before first power-on
- Never work on the circuit while it's plugged in
