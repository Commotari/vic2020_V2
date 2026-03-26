
# [Vic-2020 Version 1](README_V1.md)

# Vic-2020 Version 2
A Vic-20 clone created with [almost] all readily available parts

## Acknowledgment
Before talking about the current ongoing development of the Vic-2020 Version 2, it has to be noted that this is based on the repository and work of Dan Werner who was the main developer of the Version 1 of the VIC-2020 project.
That was a very helpful initial work and a huge accomplishment, that Dan Werner did for the whole retro computing community. Thanks a lot !!!
Having a working motherboard and an open source version of the motherboard in KiCad is a perfect start for further developments.
[Here is the link to his VIC 2020 github page](https://github.com/danwerner21/vic2020)

## Introduction
* Version 1

This project is an implementation of a VIC-20 (mostly) compatible computer.
The project is built using a combination of 1980's era components (7400-series logic) and more modern components - such as a modern 6502 variant and 512 KiB SRAM and 512 KiB Flash ROMs.
The only hard to find component is the MOS 6560 VIC video chip (for NTSC and the 6561 for PAL) -- and it is my hope to follow up this project with a project to replace that chip with a FPGA replacement, providing the open source community a full path to re-creating the VIC-20 with all new components.
(Introduction copied from Version 1 from Dan Werner)
* Version 2

As noted in the original Version 1 introduction, the main problem is sourcing the VIC chip (either in PAL or NTSC). That means the following development path should go towards an FPGA.
But there is also on important thing to note here, that the original version was only made for the NTSC chip and not for the PAL system.
This needs to be fixed in a way that also brings in more work force by making this project also attractive for PAL users.
(Remark: Commodore was also very popular in Europe in general and in the German region in particular.)
The idea of this project in Version 2 is:
* creating a video daughter board connector to use modular video daughter boards:
  * board that contains a NTSC video chip
  * board that contains a PAL video chip
  * board that contains an FPGA that is 99.99% compatible with the PAL/NTSC video chip

---

![Vic-2020 board set](Support/images/bare_system.jpg)

## Why?
### Comment from Dan Werner (original contributor of Version 1):
Why would I do a replica of the VIC-20?
Well, like many others the VIC-20 was my first computer.
In 1981 I spent most of my (non-school) waking hours learning everything possible about this machine, and that launched me into a successful career in IT.
In the early 2000s I discovered the retro-computer scene and have spent many hours building and creating new retro computer designs following the work happening in such places as 6502.org and retrobrewcomputers.org.
So much so, that my boss has taken to giving me crap about spending my free time "Building VIC-20s" . . . .
It was earlier in 2020 when he had made one such comment that I realized that while I had constructed many vintage designs, I had never actually built a VIC-20.
I decided that I should correct that oversight as soon as possible -- and thus the VIC-2020 Fichter Edition (named after my boss) was born.

### Comment from Stefan Weilhatner (ongoing development for Version 2):
Growing up in Autria, i also had several Commodore Computers:
* Commodore VC-20 ==> using it for about 2...3 years
* Commodore C64 ==> using it for about 4...5 years
* Commodore Amiga ==> using it for about 3...4 years

As you can see, from the time that I used them, the C64 was the computer that made the most or longer lasting impression on me.
However, the V(I)C-20 was my first computer and has some flaws that I want to be fixed. One of the biggest flaws at that time was the small RAM of 4kByte (+1kByte color ram?).
That resulted in good Games being mostly published on cartridge which adds additional ROM for the program and the RAM is only there for data.
At the end not many good games made it to tape because they usually where restricted to the original amount of memory.
Because it was my first computer, it deserves extra love and it deserves fixing some of the flaws and while being at it, we can do much more.
The RAM issue has already been fixed in Version 1. Now we can take care about other stuff...

---

## Main Design goals for Version 2
* Creating a daughter board connector for a video daughter board
* Creating a video card for NTSC
* Creating a video card for PAL


## Minor design goals for Version 2

### Power Supply for 9V AC with a barrel jack
Form that we get several benefits:
* We can use an adapter to use an old commodore power brick, but only the 9V AC pin which still works fine, even if the 5V 7805 regulator is defect and shorting 12V to the 5V output.
* We can use any generic 9V AC power supply.
* We could re-introduce the cassette port that needs at least 6V power
* We could re-introduce the user port that has the two 9V AC pins on the connector as well
* We could generate a 9V or 12V power DC rail to support an original SID chip, if we later want to add one.

### Cassette port
* Re-introducing the cassette port would be nice for people who still want to use the cassette port.
* There would be even an idea to add an additional microcontroller that could add functionalities for tape and disk and sd-card.
(Microchip has some cheap microcontrollers that come in an old fashioned dual inline packager and run with +5V. Having that on the board could open other doors for communication as well)

### User port
I don't remember using the user port once for myself on the VIC-20. However on the C64 I used it a few times.
I would treat it as a minor low priority goal, but the idea is to have the Version 2 mainboard running in an original VIC-20 case.


## Development forum
I found Version 1 of that project on youtube where someone built this. (Was it Adrian from Adrian's Digital Basement??)
But I did not find a development forum to discuss this with others. 

Please send me an Email for a suggestion about a development forum that is suitable for these discussions.
I don't have any idea what kind of discussion forums are available that would suit that needs. If it is a Website that already focuses on Retro Computing, why not.
We need a place to discuss opinions, ideas, needs, wishes and other nerdy stuff without much censorship (cursing allowed).
==> my email address: look further in "Questions".


## Questions?
The head behind Version 2 of this project is me: Stefan Weilhartner (from Austria)
If there are any questions, I can be reached at funkmaster dot whylee at gmail dot com.
You can find the original version of this file on https://github.com/Commotari/vic2020_V2  

What's up with 'Commotari'?
Commotari is a Portmanteau word (blend word) that should symbolize two of the biggest companies in the 80's home computer scene - Commodore and Atari.
I ( = Stefan Weilhartner ) came up with this as a kind of brand name for my contributions to the retro community and i am using that for now as my github space.

Regarding Version 1 - created by Dan Werner, please look into the old readme file that i still kept in the repository: [Vic-2020 Version 1](README_V1.md)

---

---

---

## Possible Design goals and ideas for Version 3

### FPGA video board
For that I also did a lot of brainstorming. First the idea is to reimplement the functions of the original video chip in PAL and NTSC.
I talked to Gemini AI a lot about the video output. Of course we also at some point want HDMI output.
And the result was a digital YCrCb 4:2:2 output with 6 bit where the first pixel in a line delivers Y (=brightness) in 4 bits (16 different brightness values) and
2 bits for one of the chroma signals and the next pixel uses 4 bits for Y and 2 bits for the other chroma signal.
This way the color resolution in full PAL/NTSC resolution is half but brightness is in full resolution. This reflects also the way NTSC and PAL works because it had a much lower bandwith for the colors.
And this is fine because the human eye also has less resultion for colors.
This way we need less pins to go from the fpga video board to the video output boards.
We can have two video output boards. One analog output board for PAL/NTSC containing the ADV 7170 chip and one digital output board for HDMI containing the ADV 7511/7513 chip to make a HDMI signal.
Both have a digital I2C communication board to read/write registers of these chips for configuration (like telling them the aspect ratio 4:3 or 16:9 etc).

That means we would then have an fpga video board that must have the same connectors as the board for the NTSC and PAL VIC-chips.
But in the case of the FPGA board we need to output port to be digital:
6 bits for digital video data, 1 bit for HSync, 1 bit for VSync, 2 bits for the I2C connection

And two small board - over each other - the lower board with an S-Video output connector - and above it a board with a simial size with the HDMI output connector.
(in this case I would make a hole in the upper part of the original VIC-20 case to access the HDMI port. :-) not sure, if everyone likes that approach )

#### Development stages for the FPGA video board - original functionality
* creating the dot clock and cpu clock from a 27MHz input clock. (there is a reason for exactly that frequency)
* x-y counter for the picture
* creating the sync impulses
* creating a demo video signal (like some grey and color bars) to access at least the analog video output chip
* input pin for PAL/NTSC
* I2C communication for communicating with the different video output chips
* state machine to configure the I2C registers of the video output chips (at first only for PAL and NTSC)
* creating register access for the CPU to read and write to the VIC-20 video chip registers
* building all the VIC-20 graphic functions according to these registers.
  the fist thing would be the background/forground color register and the color mapping from the index to RGB and then from RGB to the digital 4:2:2 output 
* implementing the sound functionality (maybe before doing the graphic stuff)
* implementing an I2S interface to a cheap audio DAC like the PCM5102 from texas instruments
* etc. :-)

#### Development stages for the FPGA video board - extended functionality
I have the Gowin FPGA chip in mind that can also be found on the Tang Nano 20k development board.
But in the LQFP-144 package. This chip has enough pins for everything (more than that) but is - kind of - able to hand solder with enough patience.
That chip is available with a 16-bit 133MHz 8MB SDRAM inside the package.
That would allow to implement a really good video chip.
Higher resolutions and colors, transparency, sprites, multiple layers, and memory for tiles and sprites. Also other features like the Copper from the Amiga or more modern Coprocessor functions
(like copying graphical object wich could be helpful for font rendering or other graphical objects. Also with scaling, filling polygons with different colors on different edges,...)
The onboard 8MB ram really gives a new dimension and the system is not restricted by the size and speed of the ram on the motherboard.

#### From the FPGA video board to an universal RetroBrain board
When having enough 5V compatible IO pins, that board could be used in theory for many other purposes as well.
* Audio board: reimplementing two SID chips, additional sampling, addition speech codecs (like in some TI chips or chips from General Instruments (now Microchip Technology), FM synthesis, stereo reverb. etc.
  when implementing a compatible dual SID chip, music from the C64 and also the tools could be used as well. but with stereo pan registers and stereo reverb functionality that would open up cool things
  Imagine an old space shooter like Asteroids or Space Invaders etc. with additional stereo reverb. It would have the old sound characteristic but simulated open space with reverb.
  
* CPU board: The same board could be used as a cpu module. Instead of your 6502 chip you make a motherboard that has the connectors for that FPGA board.
  You still have module with a 6502 to plug in but you could also use the FPGA board. And then you don't have any limits. 6502 reimplementation is no problem.
  But you can map the program memory to the interal 8MB Ram that runs super fast. You could also add a Z80 core to run old CP/M programs, you could also add a 68000 core, why not.
  And to access the memory of the motherboard you can implement a write cache of a few bytes that the cpu core can go on with the new commands in full speed while the bytes from the write cache are dribbeling "slowly" on the motherboard ram.

* Video card for the C64 ??
  No problemo, Make a new C64 board that has pin headers for a video card, an you can do the same thing like with the VIC-20.
  Of course there need to be enough pins on the connector to fill the needs of the C64. The access to the dram with refresh and color ram etc. is a bit more tricky.
  But there is already the kawari project as a foundation. with the universal RetroBrain board, you can take this to another level.
  Maybe supporting exactly the same extended video functionality like on the VIC-20 for compatibility. Same new register set with more colors, sprites, resolution, 16:9 mode, ....
  
* Video card for the Atari 2600/7800 ??
  Using the same fpga card for video and a 6502 with 16 bit address space that is compatible with the illegal opcodes (same as in the Atari 7800) but new video functions
  would allow a new game market that has the old cartridges but without any limitations because you can put in a cheap microcontroller with a cheap flash chip to create a very cheap cartridge that has enough memory for a more modern game.
  Put that in an original Atari 2600 case and you have a very nice open system in the most beautiful game console case ever built.

* Analog input ports needed???
  In some chips there are analog inputs needed. The SID chip on the C64 has two analog channels (if I am right) to have analog paddle inputs for X and Y.
  Using the I2C port could be used as an IO expander as well and connecting an I2C ADC chip externally would solve this problem.
  The same thing would apply to the TIA chip of the Atari 2600, if I remember correctly. Other simple solutions with a comparator and an up/down ramp would also be possible.
  
---

  
==> too many ideas, not enough time :-)


---