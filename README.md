# TM1637_avr_asm
AVR compatible assembler code for controlling displays based on TM1637 microchip

## Short description found in the source .as file.

    ;
    ;
    ; In this example used a cheap China 4-digit display 
    ; managed by TM1637 microchip, available at Aliexpress a lot.
    ;
    ; How to code displaying information
    ;
    ; In order to display some information call TM1637_display and fill registers
    ; TM1637_d1 .. TM1637_d4 with letters, that are coded next way:
    ;         0
    ;       +---+
    ;     5 | 6 | 1
    ;       +---+
    ;     4 |   | 2
    ;       +---+
    ;         3
    ; 
    ; Here the ordering numers is the bits layout in letters that to be passed to the called function.
    ; Number one coded as 0b00000110
    ; Number two coded as 0b01011011
    ; So this way, use bit=1 for diods to be burnt and bit=0 for bits that to be off.
    ;
    ;
    ; Output hex file size is only 196 bytes. Not bad. I made it for ATtiny13.
    ;

## Compiling 
to compile it just run
  
    bash$ avra tm1637_demo.as (I am using Linux)

## Flashing an AVR chip
I use an arduino board atmega2560 (but could be take any that supports ISP) for flashing AVR chips:

    avrdude -p t13 -P /dev/ttyUSB0 -c avrisp -b 9600 -U flash:w:tm1637_demo.as.hex
