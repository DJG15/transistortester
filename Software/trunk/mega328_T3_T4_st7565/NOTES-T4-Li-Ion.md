# T4 chineese LCR meter notes

This is for LCR meter marked QS2015-T4, but should work for other T4
(and may be T3) variants.

## Changes

* Added Li-Ion battery, charger, step-up, direct USB power via schottky diodes.
  Changed battery voltage thresholds in Makefile and in source.
* Added pullup resistor from LCD RST (ATmega pin PD4) to D2 anode. Enabled
  PULLUP_DISABLE and LCD_SPI_OPEN_COL options in Makefile.
* Used smaller font.

## HOWTO

* Flash command:

    ```
    avrdude -c usbasp -p m328p -U lfuse:w:0xff:m -U hfuse:w:0xd7:m -U efuse:w:0x01:m
    avrdude -c usbasp -p m328p -U flash:w:TransistorTester.hex:a -U eeprom:w:TransistorTester.eep:a
    ```

## TODO

* USB to UART converter, bootloader.
* Integration with [sigrok](http://sigrok.org/)?
* Voltage measurement input.
* Step-up for measuring zener diodes?
* DS18B20? more sensors?

## References

* [Schematic of the T4 LCR meter (PDF)](http://www.mikrocontroller.net/attachment/228473/TT-CN_T4.PDF)
  from
  [post](http://www.mikrocontroller.net/topic/248078?page=6#3784106)
* [ISP pinout](http://www.eevblog.com/forum/testgear/$20-lcr-esr-transistor-checker-project/?action=dlattach;attach=148776;image)
  and
  [programmer adapter](http://www.eevblog.com/forum/testgear/$20-lcr-esr-transistor-checker-project/msg659867/#msg659867)
