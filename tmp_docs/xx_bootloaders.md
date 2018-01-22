# Bootloader on PIC32

The used Bootloader is used in <a href="https://github.com/chipKIT32/chipKIT-core"> chipKIT-core </a> and use the <a href="https://github.com/chipKIT32/PIC32-avrdude-bootloader"> PIC32-avrdude-bootloader </a> bei default.  

For detailed Informations <a href="https://github.com/chipKIT32/chipKIT-core"> read the Bootloader Readme </a>  

Caused the SRC is online, you can make your customize Version like you need or want.  


*Note:*  

Bootloader default Variation 00:  
The default used Factory Version is with Bootloader Button and one Bootloader Status LED, that toggle.  
The Bootloader Push Button is on PB3 (pulled up) and active if it is grounded,  
the Bootloader Status LED is on PB2 (LED ON by HIGH, LED OFF by LOW), the CPU_CLK is setted to 40000000 ( 40 MHz )  







