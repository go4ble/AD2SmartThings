

## AD2SmartThings v4
### ===================
### Integrate your Honeywell or Ademco alarm panel into your SmartThings physical graph
ADT / Honeywell / Ademco / Vista / Alarm / SmartThings / Alarm Panel / Home Alarm

Do want to integrate your home alarm panel with SmartThings?  Do you hate the hassle arming your panle and having to rush to disarm?  Do you want to install another keypad and don't want to deal with your alarm company?  Do you have an alarm panel and never use it?

This is a relatively simple integration project that effectively integrates your Honeywell or Ademco alarm panel with SmartThings.  These panels are typically installed by ADT or other alarm companies.  You can choose to continue or not with your ADT  monitoring service.  This project works either way.  

After installing this project, control of your alarm panel becomes intuitive and automagic!
* Automatically arm your panel after everyone has left the house, and have it disarm when you arrive.
* Use automation to turn on your alarm when you go to bed and turn off when you wake up 
* Control your alarm panel via your smartphone or a MiniMote or activate from other sensors or devices
* Use your smartphone or Minimote to send a panic alarm when there is danger.



***Release Note:***
*-*This release allows for independent zone processing and reduces the logging from the Aruidno in SmartThings recent history log. Also included is a SmartApp that will automatically create virtual contact and motion sensors which allows you to subscribe to these from other SmartApps. This release also standardizes the hardware assembly of the AD2SmartThings device, which addresses the top two support issues. In addition, we provide more detailed instructions on how to power your project using the alarm console.   The release includes new version 4 code bases for both the Arduino sketch, the device handler and a new README with updated project instructions.

Note: This release is not backwards compatable with the Version 3.X or earlier.  Be sure to install both the sketch and new device handler to upgrade.   The libraries from SmartThings and the ArduinoMega library which can be found on github are not compatable with v4 and later sketches. You must use the ST_Anything SmartThings library. A big thanks to Daniel Ogorchock and his son, Daniel Ogorchock, for creating a superior version of the SmartThings library with many enhancements and  full support for the Arduino Mega. 

## High Level Project Steps

1. Order the hardware
2. Add SmartThings hub to your home network, download app to your iPhone
3. Obtain a Maker/Developer account for SmartThings (graph.api.smartthings.com)
4. Assemble the Arduino Mega, ThingShield and AD2Pi.  Power up.
5. Download the Arduino developer environment and import the AD2SmartThings sketch as well as the ST_Anything library.  Edit the sketch to reflect the number of zones for your system.  Transfer the sketch to the ArduinoMega over USB.
6. Add ArduinoMega/ThingShield to your SmartThings hub using your iPhone app
7. Go to graph.api.smartthings.com
  1. On My Device Types, create a new device type and paste in the device type code.  Save & Publish
8.  Go to My Devices, select the newly added Arduino and edit the Device Type and select the HomeAlarm device type (step 7.i.)
9.  Configure preferences on your mobile device.
10.  Connect your project to your alarm panel.
11.  Thoroughly test out system!  No Warranty (see license terms).

## The Hardware List

The AD2Pi was obtained from Alarm Decoder.  www.alarmdecoder.com
The SmartThings ThingShield was purchased directly from SmartThings
All other items from this project were easily obtained from Amazon via Amazon Prime

* AD2Pi
* Arduino MEGA
* SmartThings ThingShield for Arduino
* Jumper wires


### An ArduinoMega, SmartThing ThingShield and AD2Pi

<img src="https://cloud.githubusercontent.com/assets/5625006/4343989/ec207020-406e-11e4-99fc-15962e7c93e3.jpg" width="200px"  />

<img src="https://cloud.githubusercontent.com/assets/5625006/4343995/50e33b5a-406f-11e4-9dd5-1b73ab5f8e7f.jpg" width="200px"  />

<img src="https://cloud.githubusercontent.com/assets/5625006/4344057/36bc5f3c-4073-11e4-8ef3-446b950dc4ab.jpg" width="200px"  />


### Jumpers

For the wiring, I used individual male to male jumper cables to wire the project (see below).  I found these at Amazon such as **Male to Male Solderless Flexible Breadboard Jumper Cable Wires 65Pcs for Arduino by Sunkee**.

<img src="https://cloud.githubusercontent.com/assets/5625006/4343969/333ffca2-406d-11e4-95ef-287c4dfa869b.jpg" width="200px"  />


### Power 
During programming, the Arduino will be powered by the USB connection to your computer.  Once installed, the Arduino + AD2Pi will be powered by the alarm panel.  This has the added advantage of using the alarm panel battery backup as backup power to the Arduino + AD2Pi.  If power goes out, connectivity will be preserved as long as your internet+SmartThings hub is on a back up power supply and as long as the Alarm Panel battery lasts.  



### Project Housing
I simply strapped the Arduino onto a foam board and inserted it into my alarm panel box

## Constructing Your Project

Here is a high level overview of the entire project.  This README will take you through each step by step.

<img src="https://cloud.githubusercontent.com/assets/5625006/17085596/fde87456-51a1-11e6-95eb-135111ad8170.jpg" width="200px"  />   

### Wiring The Arduino Controller and Configuring The ThingShield

An **Arduino Mega* was used as the controller and was stacked with the SmartThings ThingShield.  

*Set the DIP switch on the ThingShield to D2/D3.*
The shield has a DIP switch that allows it to either read serial commands via pins 0/1 or pins 2/3. For this project, the ThingShield is reading the Serial commands from the ArduinoMega through the ThingShield pins 2/3. Check that the DIP switch is set to D2/D3.  Note, this is typically the default position when ThingShields are shipped. 

<img src="https://cloud.githubusercontent.com/assets/5625006/7670559/50d02238-fc6f-11e4-8208-3dadb582eb67.jpg" width="200px"  />   

Stack the ThingShield on top of the Arduino Mega, matching the pins as you push the two boards together.  All pins should be securely contacted.     

Use jumpers to provide a connection between Serial3 and Pins 2/3.  Here are the connections:

| Jumper     | Pin     | Pin     |
|:--------:|:------:|:-----:|
| TX         | 14      | 2       |
| RX         | 15      | 3       |

<img src="https://cloud.githubusercontent.com/assets/5625006/7666138/53eafdde-fb9e-11e4-92a1-c0b40a0e9001.jpg" width="400px"  />   

<img src="https://cloud.githubusercontent.com/assets/5625006/7666139/553dc478-fb9e-11e4-9235-14c4c6b5496f.jpg" width="400px"  />

<img src="https://cloud.githubusercontent.com/assets/5625006/7851848/2d6b0458-04bb-11e5-9353-a7615897922b.jpg" width="400px"  />


Note, the ThingShield pins are not labeled.  So you can identify the pins using labels on the ArduinoMega picture (above) or by study the photos of my project (above).

### Wiring the AD2Pi to the Arduino/ThingShield

Here are the pin connections to make between the Arduino/Thingshield and the AD2Pi along with a couple pics to get you oriented.  You can make these connections using an 8" male to male jumper wire.

Pin Configuration for AD2Pi to Arduino Mega

|Jumper  | AD2PI  | Mega   |
|:--------:|:--------:|:--------:|
| 5V     | 1      | 5V     |
| GND    | 6      | GND    |
| TX     | 8	    | 18     |
| RX     | 10     | 19     |


<img src="https://cloud.githubusercontent.com/assets/5625006/9980972/24c288d6-5f73-11e5-9a14-00a81754f499.jpg" width="400px"  /> 
<img src="https://cloud.githubusercontent.com/assets/5625006/9980971/22754c30-5f73-11e5-9f02-8901d09c08fc.jpg" width="400px"  />   



## The Software

The code for this project can be found posted on github:

https://github.com/d8adrvn/ad2smartthings.git

### Arduino Sketch 

To load the sketch onto the Arduino, you will need the Arduino developer environment:

http://arduino.cc/en/main/software

Once the software is installed, the first thing to do is obtain the required libraries.  

* A copy of the SmartThings library contained in this repository/release.  This is the ST_Anything version of the SmartThings library.  The libraries from SmartThings and the SmartThingsMega libraries do not work.
* SoftwareSerial library was default library provided with Arduino IDE
 
Once you have the zip files downloaded you can import them within the Arduino IDE. Go to the Sketch:Import Library;Add Library drop down menu. Once you have added the libraries, they will show up under Sketch:Add Library:Contributed as "SmartThings".  

Optionally, you can edit the sketch to match the highest zone number in your system.  Note, this is the highest zone number not the total number of zones.  If you have only a few zones and the highest zone is a low number, by editing the sketch, the software will be more efficient at processing alarm panel messages.  To make the edit, go to the code where it says numZones = 36 and change the number to the highest zone.  If the highest zone is greater than 36, you can make the number higher as well (you may have to edit the device handler if the highest zone is greater than 39).

You can connect the Arduino Mega to your computer via an USB cable, create a new sketch, paste the code from github into the Arduino IDE and then transfer to the ArduinoMEGA.  Be sure to go to the tools menu, select <Board> and then select the ArduinoMega 2560 so that the code will compile correctly and not time out during transfer.  

Pairing instructions for the Arduino to the SmartThings hub can be found at SmartThings.com and are copied here:

“To join the shield to your SmartThings hub, go to “Add SmartThings” mode in the
SmartThings app by hitting the “+” icon in the desired location, and then press the Switch button on the shield. You should see the shield appear in the app.

To unpair the shield, press and hold the Switch button for 6 seconds and release. The shield will now be unpaired from your SmartThings Hub.”

Once you have finished transfering the code to the Arduino, you can remove the USB and power the Arduino using a 9V transformer.

Its more than a good idea to put a piece of electrical tape over the USB port to prevent accidental grounding of the port!

### Device Type Code 

The device type code allows you to control the ArduinoMega via the SmartThings physical graph.  The  controller device type code has the following features:

The Main Tile gives the status of the system and allows you to disarm the system (by pressing the tile).

Inside the device type:

<img src="https://cloud.githubusercontent.com/assets/5625006/12284667/551b7bba-b977-11e5-99a5-13909d246b18.jpg" width="200px"  />

* StatusTile -  Same as the main tile that shows whether the system is armed or disarmed.  
* Disarm - disarms the system.  In case you accidently press the Panic key once or twice, and do not wish to activate a panic alarm, Disarm will reset the panic sequence.
* Chime - toggles chime mode
* Stay - Activates the system in Stay node
* Away - Activates the system in Away mode
* PANIC - a tile to activate the PANIC alarm.  To prevent false alrams, you must press this tile 3X. After pressing once, the tile will remind you to press twice more.  After pressing twice, the tile will remind you to press once more.  After pressing a thrid time, the PANIC alarm will sound.  Note, for this to work, you must set the Preferences to indicate which Panic code has been configured for your alarm.  If in doubt, try "B".  And test the system!
* Message Tile - displays all the messages sent from the AD2Pi

As you scroll down the Device Type UI, you will find:
* Zones - there are status tiles for up to 36 zones.   Zones appear orange when activity is detected (open door, motion detected, smoke, glass breaking, etc...). (If you need fewer zones, you can simply trim the number of zones displayed by modifying the Detials command in the code.) 

<img src="https://cloud.githubusercontent.com/assets/5625006/12284669/552cd9c8-b977-11e5-9f27-7db5f633896a.jpg" width="200px"  />

* AD2Pi Config- this tile sends configuration commands to AD2Pi.  Enter the command in the Preferences section and then send the command to the AD2Pi by pressing this tile.  The main purpose is to set the AD2Pi with a valid address.  

<img src="https://cloud.githubusercontent.com/assets/5625006/12284671/55300fe4-b977-11e5-8715-0261849ab9aa.jpg" width="200px"  />


In addition to the above tiles, notice the 3 VERTICAL DOTS in the top right corner of the Device Type screen.  Pressing these dots takes you to the Prefernces sections.  Here you can:
* Give your system a name
* Give your Device and image
* Update the icon
* Enter a valid keypad address which will be sent to the AD2Pi upon pressing the AD2Pi Config tile 
* VERY IMPORTANT:  You must enter your 4 digit homeowners alarm access code.  
* For the PANIC tile to work, you must select one of the three choices for your Panic code. This code must be valid for your system.  If in doubt, try "B" and then test your system

<img src="https://cloud.githubusercontent.com/assets/5625006/12284672/5531866c-b977-11e5-80f2-0a06517c7fe2.jpg" width="200px"  />

<img src="https://cloud.githubusercontent.com/assets/5625006/12284673/553310c2-b977-11e5-8632-86b96dc9e7dd.jpg" width="200px"  />

To install the device type code: 

1.  Go to graph.api.smartthings.com   
2.  Select My Device Types tab
3.  Select the +NewSmartDevice button
4.  Choose "From Code" tab
5.  Paste the device type code from this repository
6.  Go to the line of code with the "details" arguments
7.  Edit the number of zones in the details argument list to match the number of zones in your system.
8.  Save and Publish (for me) the device type.  You have to Publish!
9.  Go to My Devices tab 
10.  Select your Arduino and using the drop down, select your newly created AD2SmartThings device type (v2 or later).
11.  Go to your mobile device and the Arduino tile should now display as a Home Alarm tile.  Hint: on the iPhone, sometimes you have to kill the SmartThings app two times before a new device type update will display on the SmartThings iPhone app.


To install the SmartApp code: 
 1.  Go to graph.api.smartthings.com   
 2.  Select My Device Types tab
 3.  Click the +NewSmartDevice button
 4.  Choose "From Code" tab
 5.  Paste the Simulated_Contact_Sensor_Device_Handler device type code from this repository
 6.  Save and Publish (for me) the device type.  You have to Publish!
 7.  Repeat steps 3-6 for the Simulated_Motion_Sensor_Device_Handler device type code from this repository.
 9.  Go to My SmartApps tab
 10. Click + New AmartApp button
 11. Choose "From Code" tab
 12. Paste the Alarm_Handler_SmartApp code from this repository
 13. Save and Publish (for me) the device type.  You have to Publish!
 14. Go to your mobile device and to the SmartThings Market in the bottom right corner of the app.  Select the SmartApps tab and scroll to the bottom of the list.  Select My Apps and choose Alarm handler and configure it based on your alarm zone settings (do this last after you get the system fully connected and running)
 
## Connect Your Project To Your Alarm Panel

### Wiring The AD2Pi to your Honeywell or Ademco alarm panel

There is excellent documentation on the Alarm Decoder web site, including an instructional video.  Look for instructions on how to wire the AD2USB which are the same instructions for the AD2Pi used in this project.  Here is the URL:

http://www.alarmdecoder.com/wiki/index.php/Panel_Configuration

Make the following connections from both the AD2Pi and Arduino to the Alarm Panel

| Jumper   | Arduino Pin     | Alarm Panel Terminal                  |
|:--------:|:---------------:|:-------------------------------------:|
| Ground   |  GND            | Black Console Ground Return (-)       |
| Power    |  VIN            | Red Console PWR (+)                   |


| Jumper   | AD2Pi Pin       | Alarm Panel Terminal                  |
|:--------:|:---------------:|:-------------------------------------:|
| Ground   |  GND Black      | Black Console Ground Return (-)       |
| Power    |  12V Red        | Red Console PWR (+)                   |
| Data Out |  DO yellow      | Yellow Data Out To Console            |
| Data In  |  DI green       | Green Data In From                    |


Here is a close up of the terminals that connect AD2Pi to the alarm console

<img src="https://cloud.githubusercontent.com/assets/5625006/17085581/b5c00ee6-51a1-11e6-87e3-f7ff1e1c0eda.jpg" width="200px"  />


After making all the connections, reconnect alarm console to 120v and then reconnect the alarm console to its battery backup.  The Arduino should be powered on and the AD2Pi LED should be be slowly and steadily blinking.


### Configuring Your System To Work With Vista10SE or other SE-series
The VistaSE series requires the AD2Pi to be configured with an ADDRESS=31.   To do this, go to the Preferences tile on your mobile device and in the Configuration box, enter "ADDRESS=31".  All caps, no spaces and no quotes.  After entering this in the Preferences, you must then press the Config AD2Pi tile to send down the configuration command to the AD2Pi.  You will see the Message tile indicate !Sending and then you should see a confirmation message of "ADDRESS=31".  You can double check your work by going back to the Preferences, erasing the command (recommended) and then pressing the ConfigAD2Pi tile once again.  The Message tile will report back the current address of the AD2Pi.  

### Configuring Your System To Work With Vista 20P or other P-series
The Vista20P will only commuicate to the AD2Pi if it has been properly configured with a unique address.  This requires two steps.  First, you need to activate an unused keypad address in your Vista20P and second, you need to configure the AD2Pi with that address.

To configure your Vista20P, follow the instructions in the manual to activate an unused keypad address.  There is a helpful video at alarmdecoder.com  http://www.alarmdecoder.com/wiki/index.php/Panel_Configuration   You can also find a manual at  http://site.aesecurity.com/Manuals/v15pand20pprogrammingguide.pdf

You will also may need to configure the AD2Pi.  The AD2Pi is pre-configured with ADDRESS=18.  If you were lucky enough to only have two keypads and activated the third keypad for the AD2Pi (*191 in the Honeywell programming mode), then you should be fine.  If you activated a different keypad, lets say keypad #4 (*192), then you need to configure the AD2Pi with the correct address.  For Keypad #4, you should configure with ADDRESS=19.  To do this, go to the Preferences tile on your mobile device and in the Configuration box, enter "ADDRESS=19".  All caps, no spaces and no quotes.  After entering this in the Preferences, you must then press the Config AD2Pi tile to send down the configuration command to the AD2Pi.  You will see the Message tile indicate !Sending and then you should see a confirmation message of "ADDRESS=19".  You can double check your work by going back to the Preferences, erasing the command (recommended) and then pressing the ConfigAD2Pi tile once again.  The Message tile will report back the current address of the AD2Pi.  

## Integration of Home Alarm Into Automated Actions:

The device type also establishes a switch and lock capability.  You can integrate your alarm panel into SmartApps and into Actions using these capabilities.

To automate turning on/off the Alarm in "Stay" mode, select the Home Alarm from the list of "switches" in your SmartThings device list

To To automate turning on/off the Alarm in "Away" mode, select the Home Alarm from the list of "locks" in your SmartThings device list.  "Locking" the alarm turns it on in Away Mode while "Un-Locking" turns it off

For example, here are some of my automations that control my Alarm Panel

<img src="https://cloud.githubusercontent.com/assets/5625006/12284668/552c908a-b977-11e5-87bb-ba96fb3392ab.jpg" width="200px"  />


Have fun integrating!

## FAQs

* After installing the Device Type, be sure to both Save AND Publish (for me).  If you do not publish, they will not be able to communicate with the hub.  If you make changes to either code, Publish early and often to avoid IDE issues.

* The Arduino 9V power supply (transformer) can be purchased at Amazon by searching for "Arduino Power Supply".  CAUTION: There are 9V power supplies availble on Amazon that do not work for the Arduino (they are made for musical instrament controllers) and some that perform very poorly on Arduino.  Be sure to read the reviews!  

## TROUBLESHOOTING
* If you have hooked up everything "perfectly", and you still do not see any communication from the AD2Pi, recheck the following:
  *   Have you set the ThingShield DIP to D2/D3?
  *  Did you configure the AD2Pi with a valid address?  For a Vista SE series, set AD2Pi to ADRESS=31.  For Vista P series, set the address corresponding to the keypad address that you activated on your alarm keypad.  Use the mobile phone device Preferences to enter the address that matches the keypad address you activated on your alarm panel.  Be sure to send the valid address down to the AD2Pi by pressing the AD2Pi Config tile.   (note its best practice to delete the keypad address entry from the Preferences field once the address of the AD2Pi has been properly set.  Just leave this field blank when not in use).
  *   If you have a Vista P series, did you activate an extra keypad address for the AD2Pi to use
  *   The AD2Pi LED is steadily flashing at about two flashes per sec.  If not, recheck the AD2Pi wiring diagram from alarmdecoder.com
  *   You pressed PUBLISH (for me) after creating your device-type on graph.api.smartthings.com
  *   You entered your homeowners code into the Preferences page of the Device Type UI
* While compiling or transferring the code, you get the following error: 'Serial1' was not declared in this scope or  'Serial2' was not declared in this scope, then you likely do not have the correct board selected in the Arduino Development Environment.  You can also have the same issue if you see that during transfer, the transfer process times out without transfering the code.  Go to the <Tools> menu and select <Board> then select the Mega 2560.  This will allow the code to compile correctly.  
* A few thoughts regarding newer Vista panels that support partitions.
  * From the Honeywell Vista20p Programming Manual
    * The system sensing devices have been assigned to various “zones,” which are specific areas of protection (e.g., front door, kitchen window, etc.).
    * Zone numbers are displayed at the keypad when an alarm or trouble condition occurs on a sensor.
    * Partitions (VISTA-20P Series) provide two independent areas of protection, with each partition containing a group of zones that can be armed and disarmed without affecting other zones or users.
    * Partitioned systems (VISTA-20P Series) can include a common zone area, which is an area shared by users of both partitions (such as a lobby in a building).
  * If you are actively using multiple partitions for your alarm system, this is a complex situation and was not considered when building this project. 
  * Fortunately, most home installations are single partition using partition #1.  See the tips above for configuring a Vista 20p and intitialy try setting to Partition #1.  For example, you would activate Address 18 to partition #1 by typing in *191 1 0 on you alarm keypad when in installer's mode.. Check your work by #191 to confirm (returns 1 0).
  * In some cases, your installer will set a dummy partition to Alarm.  This will result in two sets of messages being relayed by the AD2Pi to the Device Handler.  This may cause the tiles on your device handler to alternate or "flash" from one state to another.  The best way to fix this is to set a "MASK" on the AD2Pi. You may want to contact NuTech/AlarmDecoder for support.  The default MASK is FFFFFFFF.  If you have a mask code, you can go to the "Edit Device" menu (the 4 vertical dots) and in the "AD2PI Configuration Command" field, type the following:  
    * MASK=FFFFFFFF    
    * Replacing FFFFFFFF with the code that Nutech/AlarmDecoder provides.    As an example, here is a MASK that will filter out messages from dummy partitions when addresses 16-19 are enabled: 
    * MASK=00000F00.   
  * Remember, Its good practice to delete your config command once your are done and leave the config field null.

* Your system will not respond to ArmStay/ArmAway/DisArm yet you are receiving messages from the system.  For example, you are seeing your Zone tiles activate when you open/close a door.  Messages from the system indicate your Arduino, AD2Pi and Device Handler are installed and communicating, however, the AD2Pi is not communicating with the Alarm Panel.  You should see a steady LED heartbeat on the AD2Pi along with this message.  Check the following:
    * You have set a valid address for the AD2Pi to communicate with the panel and the address you sent to AD2Pi matches the address you activated on your Vista20P.  Note for Vista10 systems, you always use ADDRESS=31.
    * You have entered the correct four digit numeric passcode in the Device Handler Preferences (4 vertical dots)
    * The keypad address that you selected for the AD2Pi is in conflict with an exisiting physical keypad.   The AD2Pi needs to be set at a unique address.  Exception is Vista10 units where all keypads use the same address (31).
    * Replace the jumper wires for the D0 and D1 ports on the AD2Pi to be sure there is not a short

### Trouble shooting using Live Logging
You can go to api.graph.smartthings.com and open the Live Logging Tab.  This can give you some useful diagnostics, in case your system is not working as expected.  You can also set isDebugEnabled to 'true' in both the device handler and the arduino sketch to get additional log information in Live Logging tab and the Arduino Console window, respectively

##Credits

* Timer library from Simon Monk
* Thanks to authors: Vassilis Varveropoulos, Brice Dobry for the ArduinoMega ThingShield library and intial ideas
* Lots of good ideas from SmartThings @craig 
* Thanks to Sean Matthews from AlarmDecoder for jumping in to help out with configuring device address, setting up Panic codes, and other help.
* A big thanks to Daniel Ogorchock and his son, Daniel Ogorchock, for many enhancements to the SmartThings library, including full support for the Arduino Mega. 
