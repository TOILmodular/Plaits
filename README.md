# Plaits - Macro Oscillator for Eurorack
A DIY clone of the Mutable Instruments Plaits module.

<img height="500" src="https://user-images.githubusercontent.com/97026614/227704645-73dd12a4-f4f5-40ce-8f53-5245141ef417.jpg"> <img height="500" src="https://user-images.githubusercontent.com/97026614/227704723-5b2b9fb4-2128-4a68-8ade-91d2d9bf699a.jpg">

<img height="500" src="https://user-images.githubusercontent.com/97026614/229717438-1c22990d-5d25-4906-96e2-fcb83a1bf992.jpg"> <img height="500" src="https://user-images.githubusercontent.com/97026614/229717290-28661ffa-5f09-4712-8173-6bd269c22ebf.jpg">

## Module Build and PCBs
If you want to build the module yourself, I uploaded firmware, schematic, BOM and Gerber files for the PCB.

NOTE:
The build requires soldering of several SMD components, including the STM32F373CCT6 microcontroller. I did not use any specific SMD tools, like hot-air gun or solder stencil, just a normal soldering iron, thin solder wire (0.65mm) and plenty of flux (most important). 

There are two different versions for the control board, an "original" and a "Thonk" version.
Reason is that for my own module, I am using specific potentiometers - 16K4 series from Supertech Electronics - and 3.5mm jack sockets - MJ-355 from Marushin - available at my local electronics shop.

<img width="300" alt="Plaits_CtrlBoard_original" src="https://user-images.githubusercontent.com/97026614/227705266-db77d62c-a098-4379-aa64-d45a7b9647fa.png">


However, since most DIY projects for Eurorack modules out there are using potentiometers from ALPHA and so-called THONKICONN jacks, as they are provided by Thonk in the UK, I also created a version with footprints for those components.
Choose the one you need.

<img width="300" alt="Plaits_CtrlBoard_Thonk" src="https://user-images.githubusercontent.com/97026614/229720069-4d4d9e9d-3c3e-4184-b632-b5b17823732d.png">

The layout of the main PCB is sligthly different for each version. I needed to move some of the board connector pin locations, due to the different shape of the jack sockets. Please make sure to use the right control and main board PCBs.

<img width="300" alt="Plaits_MainBoard" src="https://user-images.githubusercontent.com/97026614/227705396-f5779b2e-037b-4e6f-934d-4c6465861d1e.png">

I created the Gerber files with the online tool EasyEDA and ordered it at JLCPCB.
I cannot guarantee, if this set of zipped Gerber files works also for other providers, like e.g. PCBWay. I have not tried that. But I saw online, that others did it.

### !!!CAUTION!!!
I have been made aware, that there were erroneus labels for two components on the silk screen of the control board for the "Thonk" version.
Next to the TLC59281DBQ IC, there are a BLM18R ferrite bead and a 0.1uf capacitor. Both have the same SMD package size. But the labels were swapped in my first version.
I already corrected the Gerber file. But if you have a version with the capacitor on top of the ferrite bead, then that is the incorrect first version!

The following picture shows the CORRECT labeling of both components.

<img width="500" alt="Silk Screen Correction" src="https://github.com/TOILmodular/Plaits/assets/97026614/991094e7-6224-459f-9d6e-b486d881b4b6">

## Panel Layout
I added the information about hole coordinates for the front panel in the folder PanelLayout, referring to the component layout in the Gerber files.

## Additional Information about specific Components
There is a number of SMD components in this build:
- STM32F 373 CCT6 (microcontroller, LQFP48 package)
- PCM5100APW (DAC, 20-TSSOP package)
- TLC59281DBQ (LED driver, 24-SSOP package)
- LD2981ABU33 (voltage regulator, SOT-89-3 package)
- LM4040B10 (voltage regulator, SOT-23-3 package)
- MCP6004 (quad op amp, 14-SOIC package)
- NJM4580 (dual op amp, 8-SOIC package, any SMD version of a TL072 is also fine)
- BAT54ST (diode array, SOT-523 package)
- BLM18R (ferrite bead, 1608 package)
- 0.1uF capacitors (1608 package)

Concerning the resistor size, I am usually using small-size resistors, about half the length of the usual size, so they need less space on the PCB. If you want to use my Gerber files, you have to consider that fact. You might still use normal size resistors and put them in a standing position on the boards. Should also work fine.

On the control board, you will find an electrolytic capacitor with a rectangle next to it. Since this capacitors is too tall for standing upright on the board with the main board on top of it, the capacitor needs to be mounted in a rectangular position. The rectangle shows the position for the bent-over capacitor.

<img width="350" alt="Cap bent over" src="https://user-images.githubusercontent.com/97026614/229722617-4b4332b7-431d-4968-b0d0-a5d966044eab.jpg">

## Firmware
I shared the .hex files for the STM32F373 chip (bootloader and main) in the folder Firmware.
The version of those files is V1.1, as available in the Mutable Instruments GitHub repository.

However, the latest version V1.2 with all the new synthesis models can also be loaded to this DIY module version via the available .wav file, as described in the official Plaits manual.

## Programming
The main PCB contains connection points for both connector types for programming STM32 chips, JTAG and UART. Those can be used for standard pins with 2.54mm distance. Depending on the available connector, you only need one of those two connection point groups. However, I only tested the UART connection. The JTAG connection points have been added to the PCB by following the Mutable Instruments original design.

Besides that, there are two connection points for putting the chip into boot mode, which is needed for loading the bootloader file. Just solder a 1x2 pin with standard 2.54mm distance to connection points labeled "BOOT". For activating the boot mode, place a jumper onto the pins. As soon as the bootloder is uploaded, remove the jumper to put the chip into operation mode, so the main code can be uploaded.

If you want to see more about the chip programming process, you can check out my [YouTube video](https://youtu.be/9D4ZEAn3BBg).

<img width="321" alt="ProgrammingConnectors" src="https://user-images.githubusercontent.com/97026614/227706871-7a7d2b94-ab19-4e98-b119-1c4047258e0a.png">

## Calibration
The calibration procedure is the same, as the one for the original module from Mutable Instruments.

1. Disconnect all CV inputs.
2. Connect the note CV output of a well-calibrated keyboard interface or MIDI-CV converter to the V/OCT input. Leave all the other CV inputs unpatched.
3. Press both buttons. The first LED slowly blinks. The color depends on the diodes used. The original one is blinking green.
4. Send a voltage of 1.000V to the V/OCT input.
5. Press any button. The first LED now blinks in the combined color of the 2-color LED.
6. Send a voltage of 3.000V to the V/OCT input.
7. Press any button.
