# CS207_Maker_Project_Touchscreen_Jukebox

The project being designed for CS207 is a touchscreen jukebox.

This jukebox runs a free and open source software called Volumio. The jukebox is being run by a combination of a Raspberry Pi and Arduino to do the music and software proccessing and LED lightshow control. The Raspberry Pi will run Volumio and the touchscreen to interface with the music sources. The output will go to an amplifier and the Arduino Uno which will use the incoming oltage signal from the Raspberry Pi to control some NeoPixel digitally controlable LEDs.


# Repository Contents:
- ino: This is where you will find the code for the Arduino
- images: This is where you will find images for thee project at various stages
- source: This is where you can find the sources for the original bits of code used to make this project

# Bill of Materials:
- 1 x Raspberry Pi B
- 1 x Arduino Uno
- 1 x Amplifier()
- 2 x speakers - make sure that the impedence and wattage of the speakers match what the amplifier can output per channel
- 1 x Adafruit NeoPixel 1 meter strip
- 1 x 12 volt switching power supply
- 1 x 19 volt laptop power supply
- 1 x Justboom Stereo DAC
- 1 x Raspberry Pi Official Touchscreen
- 1 x Old Computer Power Supply
- 1 x 3.5mm male AUX cable to (any other end will work like headphones or 3.5mm AUX)
- 2 x RCA splitter
- 1 x RCA audio cable male to male
- 1 x Volumio Software Installed on Micro SD Card and Volumio Account
- 1 x PTFE clear 1/2 outer diameter tubing
- 1 x 4ft by 2ft sheet of 3/4 inch thick plywood
- 1 x 4ft by 2ft sheet of 1/4 inch thick plywood
- 1 x box of 1 inch screws
- 1 x box of 3/4 inch screws
- 1 x box of 1 1/4 inch screws
- 1 x 12 ft of wiring for the LEDs
- 1 x 1000uF Capacitor
- 1 x 12v to 5v stepdown module
- 1 x 12v to 5v USB stepdown module with USB outputs
- 1 x 560 Ohm resistor
- 1 x 6ft of speaker wire
- 1 x USB drive for storing music
- 1 x 1ft by 96 inch role of walnut veneer (optional)
- 1 x 3ft by 1.5ft panel of solid walnut (optional)
- a woodworking shop and fine woodworking tools (optional)


# The Build Instructions:

A huge portion of this poject is woodworking. I understand that the techniques used in this project are more advanced than a lot of people would like to take on but it doesnt have to be complicated. You can simply make a plywood box and paint it or find an already built box and modify it to meet the needs of this project.

The woodworking challenge:
Woodworking is not for everyone so if this part of the build is a particular challenge, just note that an alredy assembled box may be used. I will not go into a lot of detail on the woodworking portion as it is too complicated to cover. Those of you who enjoy and have experience woodworking will be able to see how to make the jukebox. We will coverthe design of a simple painted plywood box. Lets start with the speaker boxes. These are small dedicated boxes that house each seaker. They provide a better and more punchy sound. These are not a requirement as the speakers will work without these but they do make a difference in sound. To find the size requirement of the boxes, check with the speaker manufacutre. This is a common spec for speakers. These box dimntions are only a guide. Try to get as close as possible to the dimentions but don't sweat over not being perfect. The Jukebox itself can be made out of 3/4 inch plywood. Make a box and screw it together. Cut out holes for the various components to mount through. You can paint the box any colour you want or leave it natural. I used a walnut veneer for the sides and top for this project and a solid piece of walnut for the front panel. The trim along the bottom is made out of bloodwood. Bloodwood is difficult to work with so I don't recomend working wth it unless you are experienced. The back of the jukebox is made out of 1/4 inch thick plywood that was painted black. This was screwed onto the body using 3/4 inch screws. The actual plugin and switches are meant to clamp onto a thin peice of metal. I used aluminum but hot gluing these compnents to the 1/4 inch plywood will work as well. 

Lets start with the software:
Go to www.volumio.com and download the software package from the download tab of the website. Select the Raspberry Pi code choise as this is what we will be using for this project. Once downloaded, using a flashing software, fsh the volumio software onto a 8gb micro SD card. Once complete, the SD card can be plugged into the Raspberry Pi (RPi). Before you power on the RPi, make a volumio account. A bonus feature you get from a volumio account is the ability to cloud save your volumio device settings for poweroutages. Don't power the RPi on at this point.

Next lets look at installing the RPi Official Touchscreen:
There is an excelent video on youtube demonstrating how to do this. The link is here: https://www.youtube.com/watch?v=tK-w-wDvRTg
Please note that for this project, we will use the dual micro USB cable method of powering the devices. Don't apply power yet.

First bootup:
before you boot up the RPi, download the volumio app from the App Store or the Play Store or have an internet browser open. Plug an ethernet cable into the RPi for internet and apply power to the RPi. Volumio is not set up to stream to the touchscreen so you will only get lines of code. Use the app to automatically find the RPi or find the IP address on the touchscreen and enter that into your browser. You will now be able to control the RPi volumio system. Go to plugins and download the Raspberry Pi Official Touchscreen plugin (it may take quite a while so let it instll fully) and then enable it. Using the app or browser, restart the RPi in settings tab and when the RPi restarts, volumio should now be on the touchscreen! If it doesnt, go back to re-flashing the micro SD card and start over.

Lets talk about the Arduino and NeoPixel circuitry now: (Image of circuit in images folder)
The Arduino Uno can't supply enough power to power all of the LEDs so we will need to power the LEDs seperately. To do this, we will use a 12 volt switching power supply. The circuitry diagram can be seen below but here is a discription of what is going on. The positive and negative (ground) wire from the power supply will  be wired to a 12v to 5v stepdown module and then soldered onto a proto board. They will first go through a 1000uF capacitor to smooth out the voltage to protect the LEDs. From the capacitor, the positive end will be connected to the 5V input on the LED strip and the ground will be connected to the ground on the LED strip. The ground wil also go to one of the ground pins on the Arduino as the LED strip must be grounded to the Arduino as well (Do not connect the positive to the Arduino). The digital control lead from the LED strip will be connected to pin 6 on the Arduino with a 560 Ohm resistor in line to make sure that the signal stays smooth. Now that the LEDs and Arduino are connected, let move on!

Connecting the Arduino to the Raspberry Pi:
This is fairly simple. If using the headphone jack from the RPi for your music output, simply cut an old heaphone cable at one end to expose the left, right and ground wires. Plug a AUX splitter into the RPi and plug the cut headphone calbe into the splitter. Now plug either the left or right channel into the Arduino's A0 pin and th ground into the Arduino's ground pin. Plug the Arduino into the RPi using the USB cable.

Speakers are no good without an Amplifier:
This next section will cover the connectin between the RPi, amplifier, power supply and speakers. To connect the RPi to the amplifier, use a3.5mm AUx to RCA cable. Plug the AUX end into the other end of the RPi splitter and the RCS ends into the amplifier. Using the speaker wire, wire up the left and right speakers to the amplifier. Finally, plug the 19v power supply to the amplifier.

But the Rspberry Pi has no power:
To power the RPi, we will use the 12v switching power supply and connect the positive and negative ends of the 12v to 5v USB stepdown module. Now, plug the RPi into the USB module.

Mains power is very dangerous:
This section is where things can get dangerous so be careful. I used the power switch and plugin from an old computer power supply. Simply tear out these components out of the power supply. The power supply I used had resistors ad a 250v capacitor soldered onto the plugin. I removed these components as the 12v switching ower supply already has these built in. Now, wire the ground from the plugin to the ground on the switching power supply, the positive from the switch to the positive input and the negative from the switch to the negative input from the switching power supply. This is safer than directly wiring the power chord to the power supply as if the chrd is pulled, it will simply unplug from the plugin rather than havng live wires floating around.

Uploading the LED animation code:
The last step witht the electronics is to upload the LED code to the Arduino. The code file can be found in this repository. This code was not totally written by me. The foundation of this code came from the Robert Robert YouTube channel (https://www.youtube.com/watch?v=pQwgZwrXfhc&t=83s) and some of the animations came from Tweaking4All (https://www.tweaking4all.com/hardware/arduino/adruino-led-strip-effects/).

Both of these codes were heavily modified be me to match the requirememnts of this project.

You are now ready to try it out. Plug it in and enjoy!

# Team:

- Brandon Watson - head designer
- Carter Watson - code contribution
- Scott Watson - second pair of hands for woodworking
- Janet Watson - design tips

# Credit:

- software: www.volumio.com (Fantastic free open source software!!! Well done Volumio Team!)
- original idea: ETA PRIME YouTube Channel (https://www.youtube.com/watch?v=_0CufyjhK_4)
- code framework:Robert Robert YouTube Channel (https://www.youtube.com/watch?v=pQwgZwrXfhc&t=83s)
- cool animations:Tweaking4All (https://www.tweaking4all.com/hardware/arduino/adruino-led-strip-effects/)



# Updates for CS 207 Project to come.

October 28th: All electronic components needed for this build have been ordered from various websites. The Sure Electronics AA-AB32174 2x50W TDA7492 Class-D Amplifier Board was chosen for the amplifier as it is a good quality unit that comes at a good price. Two 3.5 inch Dayton Audio Midrange woofers were used for the sound output for the jukebox as they have great bass response for the price and punch way about their weight class. The JustBoom stero DAC was used  to improve the sound quality being output from the Raspberry Pi. The official Raspberry Pi touchscreen was used as it has a wel established functionality with the Raspberry Pi and Volumio which is very important as Volumio is meant to be a cloud based service rather than a 'same machine' screen service. This device will have a more finished look than the general 'maker' theme as it will be used by many people and will hopefully end up being a showpiece. It will be made out of walnut and bloodwood.

October 29th: The basic framing for the LED light show coding has been taken from the Youtuber Robert Robert who made an excelent Neopixel based LED lightshow tht is music responsive. A basic explanation as to how the code works. The arduino pulls in 50ms of music sample from an auto gain adjustment microphone and through a combination of eqations, assigns the incoming voltage samples to a number from 0 to 11. A seriese of 'if' statements is then used to 'ick' and run a LED lightshow function. For exmple, if the number is 0, a rainbow effect is run. If the nuber is 4, an old style movie theatre lightshow is displayed. This code repeats on a loop and when no music is playing, the rainbow fucntion is run.

November 1st - Coding challenges:
Seeing as the code framework used for this build was designed around an auto gain adjustment microphone, a new equation had to be used to balance out the voltage readings coming in from the audio source (a headphone cable connected directly to the Arduino's ground and A0 pin). A microphone was not used for this projct as it was decided that the jukebox LEDs should only respond to the music from the jukebox and not outside noices and voices. The problem then arizes that the voltage can heavily range with volume. The detected ranges for voltage were 0 to 500. Therefore, a modulus divide equation was used to make sure that the LEDs function properly for any volume level.
