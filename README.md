# X301_SKR3_Marlin_2.1.2.1
Configs for X301 with SKR 3


Download VS Code and install
Add PlatformIO to VS code using the extensions button on the left.

Download Marlin 2.1.2.1 and unzip to C drive

Open the marlin 2.1.2.1 folder with Platform IO.

Replace the configuration.h file, configuration_adv.h and PlatformIO file with the file on this github.

Compile with the check mark in the bottom left of VScode

Find the firmware.bin file and put it on an microSD card

Set the jumper on SKR3 to USB insert the micro SD and boot with a USB cable.

SKR3 will flash firware. 

Remove SD card - Filename changes to FIRMWARE.BAK or similar.
Power on from VCC = 24 V

Test all funcionality.


Cura: Start Gcode
M75 ; Start Print Job Timers
M150 B255 R255 U255 ; Set LED's to white
G1 E-3 F300
G28 ; Home
G29 ; Probe the Bed
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; move z up little to prevent scratching of surface
G1 X0.1 Y20 Z0.3 F5000.0 ; move to start-line position
G1 X0.1 Y200.0 Z0.3 F1500.0 E15 ; draw 1st line
G1 X0.4 Y200.0 Z0.3 F5000.0 ; move to side a little
G1 X0.4 Y20 Z0.3 F1500.0 E30 ; draw 2nd line
G92 E0 ; reset extruder
G1 Z2.0 F3000 ; move z up little to prevent scratching of surface
G1 X5 Y20 Z0.3 F5000.0 ; Move over to prevent blob squish

Cura Stop G code:
M104 S0 ; Turn off Extruder Heat
M140 S0 ; Turn off Bed Heat
G91 ; Relative mode
G0 Z10 ; Move bed down to clear print
G90 ; Go back to Absolute positioning
;Retract the filament
G92 E3
G1 E-3 F300
G28 X 
M1 Y280 F3000 ; Move Extruder back for easy access to print
M77; Stop print job timer
M150 U255 ; Turn LED's Green


