pcb-power-connect
=================

In this repository you will find a small pcb useful if you
want to feed power to your Pi using GPIO pins 2 and 4 (e.g.
because the pi is within a housing and there is no space for
a connection to the usb-power plug of the pi).

![](pcb-power-connect-3D.png)

The pcb supports some additional features

  - connect an external high->low signal (e.g. button)
    to GPIO3 (acts as on/off-switch, see below)
  - connect an external low->high signal to GPIO3 via an
    inverter (74HC05)
  - connect a LED
  - connect an IR (or something else)
  - connect an UART
  
 
 Pinout
 ------
 
  -  1: 3V3
  -  2: 5V
  -  3: GPIO2: nc
  -  4: 5V
  -  5: GPIO3: on/off
  -  6: GND
  -  7: GPIO4: IR
  -  8: GPIO14: TX
  -  9: GND
  - 10: GPIO15: RX
  - 11: GPIO17: LED
  - 12: GPIO18: nc
 

Configuration
-------------

Use the following configuration in `/boot/config.txt`:

    # configure GPIO3 as shutdown-button
    dtoverlay=gpio-shutdown
    
    # configure GPIO4 for IR
    dtoverlay=gpio-ir,gpio_pin=4

    # use external heartbeat-LED
    dtparam=act_led_trigger=heartbeat
    dtoverlay=act-led,gpio=17


License
-------

Shield: [![CC BY-SA 4.0][cc-by-sa-shield]][cc-by-sa]

This work is licensed under a
[Creative Commons Attribution-ShareAlike 4.0 International
License][cc-by-sa].

[![CC BY-SA 4.0][cc-by-sa-image]][cc-by-sa]

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-image]: https://licensebuttons.net/l/by-sa/4.0/88x31.png
[cc-by-sa-shield]:
https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg
