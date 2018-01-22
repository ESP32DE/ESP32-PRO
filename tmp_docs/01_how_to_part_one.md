#### *preliminary work copy*  
**please note:**  
can be here: typos, wrong format, adds, missings, expansion  
this preliminary doc-work copy becomes updates time to time and  
is still in preliminary work. 

if the ESP32-PRO becomes a release by olimex - the doc's   
becomes then a pre release status for testings and after this  
the release.  

if you find mistakes or are you missing steps, need detailed infos,  
please feel free for a contact with questions over github. 

best wishes  


---
# ESP32-PRO
  

There are more possibles to program the ESP32-PRO  
For the begin, we use Arduino IDE and as second  
Eclipse with Arduino Plugin, so we can programm  
the PIC32 and the ESP32 very well with this. 

Btw, PIC32 we can program with MPLAP X too  
and the ESP32 we can program with ESP-IDF in favority IDE also.  
You can take your favority IDE like you need and like.

For the traditionel first "Hello World" Application
let us start simple with Arduino IDE.  
If you have not installed Arduino IDE yet you find on Arduino Website  
download and install readme and many helpful links and Docu.  


For the PIC32 on the ESP32-PRO we use ChipKIT-CORE  
and for the the ESP32 use the Arduino Core from Espressif.

This are ready to go toolchains with compiler and tools.  

## Let's start:
**Preparation:**  
*Arduino IDE - PIC32 Toolchain&Tools - ESP32 Toolchain&Tools*

- Install Arduino IDE  
  Visit the <a href="https://www.arduino.cc/en/Main/Software"> Arduino.cc </a>, download and install the IDE


- Install **PIC32 Core** in Arduino IDE  
  This is the core with Toolchain and Tools for the PIC32  
  Visit <a href="">chipKIT32</a> at github if you want build by self a snapshot  
  or use the Arduino **Boards Manager** to install the latest release.  
  We do here the install by Arduino Boards Manager:  
  Simply place this URL  
    
    https://raw.githubusercontent.com/chipKIT32/chipKIT-core/master/package_chipkit_index.json  
    
    in the Preferences->Additional Boards Manager URLs: text field  
    and then opening up the **Boards Manager** in the Tools->Board menu.  
      
    Visit the <a href="https://github.com/chipKIT32/chipKIT-core"> ChipKIT32 Github </a>, read the Readme, visit <a href="http://chipkit32.github.io/chipKIT-core/index.html"> Developer API </a>,  
    How to for detailed Infos and more and install ChipKIT32 Core in your  
    way if you need special way or want try to manual install.  
      
    You can build byself with the latest snapshot too.  
      
 - Install Arduino core for the ESP32  
  This is the core with Toolchain and Tools for the ESP32  
  Visit esp32-arduino at github and follow the <a href="https://github.com/espressif/arduino-esp32#installation-instructions"> Install Instruction </a>   
    
- Add ESP32PRO Board in Arduino IDE  
  ( to do: insert "How to of Add ESP32-PRO Board" )  
  
  **Note:**  
  *We can upload new Firmware for ESP32 on several ways like*  
    
    - Arduino OTA
    - Over the PIC32 USB Device ( we have USB OTG, HOST and DEVICE )
    - Over the PIC32 UART 
  
  We go here on in this Readme with Over the PIC32 USB Device.  
  For this we have a Bootloader by press a Button for this  
  also we have a Bootloader ready without a Button and is done by  
  a special toggle sequence the DTR/RTS lines over the PIC32 as USB Device  
  You can later change byself to OTA (Over the Air ) or like you want.  
  All Sources are available and are provided that you can customize on your own way.  
  
- Write your first "Hello World" for the PIC32  
 
```
void setup() {
  // put your setup code here, to run once:
  Serial.begin(115200);
}

void loop() {
  // put your main code here, to run repeatedly:
  Serial.println("Hello PIC32");
}
```  

     Note: 
     On PIC32 the Serial is USB Device CDC ACM  
     if you have not installed a driver for this, and you start for the  
     first time on PC, there starts a driver install.  
     you find the driver in the ChipKIT32 core. 
     to do: link to "Driver Install"

- Compile and upload the PIC32 Firmware to the ESP32-PRO  
  If you have done your "Hello World" for the PIC32 you can now  
  compile it and upload it to the ESP32-PRO board.  
  For this, on the ESP32-PRO on PIC32 side, there is a Bootloader by factory  
  on the PIC32. If you start the first time this procedure,  
  there starts a driver install for the bootloader.
  You find the driver in the ChipKIT32 core.  
    
    For more Information on this have a look to the  
  DOCS in the Bootloader Folder here in this Repo  
   *to do:*
    -  *link to the SUB Folder "Bootloader ./. PicKIT3 & CO "*   
    -  *link to the MPLAP X Bootloader Project with Sourcecode*
  
- Write your PIC32 Application Code for upload ESP32 code  
  The PIC32 is connected to the ESP32 several ways.  
  One way is to use the PIC32 UART as Source for the ESP32 UART  
  for transparent upload the ESP32 Firmware.  
  Cause PIC32 can be used as a own USB Device "CDC ACM"  
  we need no FTDI or other for the Firmwareupload to the ESP32.  
  This is done transparently over  
  **PC <-> USB <-> PIC32 USB Device as Serial COM <-> PIC32 UART <-> ESP32 UART**  
  For more Information about this, read the Docu "Transparent UART"  
  in the Doc Folder *to do: link to the "Transparent Uart" doc  
  Also there is then an Example Code available for your reference.  
    
- Write your first "Hello World" for the ESP32  
  you'll be amazed: same code  
 
```
void setup() {
  // put your setup code here, to run once:
  Serial.begin(115200);
}

void loop() {
  // put your main code here, to run repeatedly:
  Serial.println("Hello ESP32");
}
```  

     Note: 
     On ESP32 the Serial is UART and it is connected to a UART from PIC32  
     You can talk over the PIC32 to the ESP32 and vice versa.  
     Also you can write a USB CDC ACM code for the PIC32 with transparent  
     UART connection to the ESP32 and so on.  

- Compile and upload the ESP32 Firmware to the ESP32-PRO  
  If you have done your "Hello World" for the PIC32 you can now  
  compile it and upload it to the ESP32-PRO board.  
  For this, on the ESP32-PRO on PIC32 side, you can use the USB Device  
  for upload as USB Serial COM Port and over the transparent UART mode  
  to the ESP32.  

  Depending on your used PIC32 Firmware you can example use DTR/RTS for a toggle  
  sequence and on match to your code, switch the ESP32 in bootloader mode.  
  There is an example code still in the test pipe and comes with the  
  pre release. Also you can connect by code PIC32 PINS with ESP32 PINS,  
  that switch the ESP32 in download mode. Also you can use OTA for download  
  a firmware to the ESP32.  
  
  ( ToDo: more detailed info and example code )   
    

     
  This is the preliminary work copy for Basic's in this doing.  
  Stay tuned for the release version.