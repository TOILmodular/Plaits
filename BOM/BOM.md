# BOM

| Description | Value | Quantity | |
| --- | --- | --- | --- |
| Resistor 1/4W | 100R | 2 | |
| Resistor 1/4W | 1K | 2 | |
| Resistor 1/4W | 2.2K | 3 | |
| Resistor 1/4W | 10K | 11 | |
| Resistor 1/4W | 20K | 4 | |
| Resistor 1/4W | 33K | 6 | |
| Resistor 1/4W | 56K | 1 | |
| Resistor 1/4W | 100K | 9 | |
| Resistor 1/4W | 120K | 4 | |
| Resistor 1/4W | 200K | 3 | |
| Resistor 1/4W | LED | 1 | see footnote *) |
| Capacitor Electrolytic | 22uF | 2 | |
| Capacitor Ceramic | 22uF | 3 | |
| Capacitor Electrolytic | 10uF | 5 | |
| Capacitor Ceramic | 2.2uF | 2 | |
| Capacitor Ceramic | 1uF | 6 | |
| Capacitor Ceramic | 0.1uF | 23 | SMD (1608) |
| Capacitor Ceramic | 1000pF | 16 | |
| Capacitor Ceramic | 100pF | 4 | |
| Capacitor Ceramic | 20pF | 2 | |
| Diode Array | BAT54ST | 1 | SMD (SOT-523). CAUTION: "ST" is important! There are different BAT54 versions |
| Diode | 1N5819 | 2 | |
| LED | 2-color, common anode | 8 | |
| Op Amp | NJM4580 or TL072 | 1 | SMD (8-SOIC) |
| Op Amp | MCP6004 | 2 | SMD (14-SOIC) |
| DAC | PCM5100APW | 1 | SMD (20-TSSOP) |
| Microcontroller | STM32F373CCT6 | 1 | SMD (48-LQFP) |
| LED Driver | TLC59281DBQ | 1 | SMD (24-SSOP) |
| Oscillator Crystal | 8MHz | 1 | leg distance 4.8mm |
| Voltage Regulator | LD2981ABU33 | 1 | SMD (SOT-89-3) |
| Voltage Regulator | R-78E3.3-0.5 | 1 | |
| Voltage Regulator | LM4040B10 | 1 | SMD (SOT-23-3) |
| Inductor | 33uH | 1 | axial THT, if you use my PCB design |
| Ferrite Bead | BLM18R | 3 | SMD (1608) |
| Potentiometer | B10K | 7 | |
| Mono Jack | 3.5mm | 10 | |
| Switch | Tactile | 2 | e.g. Mouser: TL1105SPF160Q1RBLK |
| Header | 2.54mm Male 1x7 | 4 | Connector Main Board |
| Header | 2.54mm Female 1x7 | 4 | Connector Control Board |
| Header | 2.54mm Female 2x5 | 1 | Power Connector |

*) Depending on the LEDs used, they might be too bright. The resistor labeled as "LED" can be used to adjust the brightness by reducing the current from the common anode to each LED. The original design from Mutable Instruments does not include that resistor. So if you use the same LEDs, as in the commercial module, you can just bridge the resistor points with a wire. Otherwise try out different resistor values to adjust the LED brightness.

