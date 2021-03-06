arduinoMakefile
===============

This project is just a simple Makefile for Arduino. There are some Makefiles in the Web but all of them are complicated and some does not work properly for newer versions of Arduino. This Makefile is simple and just works!

It does:

- Compiles your sketch, including the standard Arduino library required
- Merge all files into a .elf and them translate it to a .hex file
- Upload the .hex to Arduino's flash memory


**WARNING[0]:** it was tested only in Ubuntu GNU/Linux with Arduino Uno. Probably it'll work well in any GNU/Linux distribution or Mac OS with Arduino Duemilanove. Windows users: sorry, please use a better OS.

**WARNING[1]:** by now the feature of compiling external libraries (even standard libraries and third-party libraries) is not implemented. So, if you have some `#include` in your project, probably it won't work -- but don't be afraid, I'm working on this.



Why another Makefile?
---------------------

The question was answered in the section above -- but I'm studying all the Makefiles for Arduino that I found in the Web and trying to implement the simplest way of doing it right. I've created a [**comprehensive list of Makefiles**](https://github.com/turicas/arduinoMakefile/blob/master/resources.markdown) and I'm categorizing them.


Dependencies
------------

You need to have installed:

- Arduino IDE unpacked -- we just use the libraries' source code
- `gcc-avr`, `avr-libc` and `binutils-avr` -- for compilation
- `avrdude` -- for upload
- `make` -- to interpret the Makefile


If you run Ubuntu or Debian, just execute this recipe:


    sudo aptitude install gcc-avr avr-libc binutils-avr avrdude make
    wget http://arduino.googlecode.com/files/arduino-0022.tgz
    tar xfz arduino-0022.tgz



Usage
-----

The head of Makefile is self-explanatory, please read the comments and change these variables:


    # Sketch filename without .pde (should be in the same directory of Makefile)
    SKETCH_NAME=Blink
    # The port Arduino is connected
    #  Uno, in GNU/linux: generally /dev/ttyACM0
    #  Duemilanove, in GNU/linux: generally /dev/ttyUSB0
    PORT=/dev/ttyACM0
    # The path of Arduino IDE
    ARDUINO_DIR=/home/alvaro/arduino-0022
    # Boardy type: use "arduino" for Uno or "skt500v1" for Duemilanove
    BOARD_TYPE=arduino
    # Baud-rate: use "115200" for Uno or "19200" for Duemilanove
    BAUD_RATE=115200


**WARNING:** you need to have the configuration for Arduino Uno at your `avrdude.conf`. For some strange reason, the `avrdude.conf` at the Arduino IDE package does not have Arduino Uno configuration, but it works if do you use the default avrdude configuration file for Ubuntu package (at `/etc/avrdude.conf`).
