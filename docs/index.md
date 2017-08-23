# MAKERBuino game dev tutorial

This is a dev tutorial for the [MAKERBuino](http://makerbuino.com) gaming platform. It is an [Arduino](http://arduino.cc)-based console. It uses the [Gamebuino](http://gamebuino.com/) software library. Therefore this tutorial actually applies to Gamebuino. Therefore I will either use the *Gamebuino* or *MAKERbuino* name in the tutorial.

In this tutorial, I will assume the reader knows the basics of programming. If it is not the case, there are many resources on the web. I recommend the [KhanAcademy](https://www.khanacademy.org/), which is full of courses about many topics, including math, physics, electronics and programming.

I will not get into details about programming on Arduino. It is actually pretty straightforward if you know the basics of programming.

## Dev environment

We will use the Arduino IDE (Integrated development environment). This is far from being the best IDE in the world, but this is standard for Arduino programming, and sufficient for our needs. Just download and install the Arduino IDE from the [Arduino download page](https://www.arduino.cc/en/Main/Software). Then you have to install the Gamebuino library. Just follow the [instructions on the Gamebuino wiki](http://gamebuino.com/wiki/index.php?title=Getting_started#Software_setup).

The [Gamebuino wiki](http://gamebuino.com/wiki/), and the [Gamebuino reference](http://gamebuino.com/wiki/index.php?title=Reference) are valuable resources which you should always have at hand. The Reference is a list of all functions and variables of the library. The names are are self-explanatory. Most of them have a clear documentation. Also, there are many code examples with the library, which you can access from `File > Examples > Gamebuino`.

## Running your game

To run your game, you will need to get the binaries, and copy them on the SD card. I will not rephrase the clear [instructions from the Gamebuino wiki](http://gamebuino.com/wiki/index.php?title=Getting_started#Put_games_on_the_micro_SD_card).

This page explains where to find the binaries, depending on the platform you are working on (Windows, Mac or Linux). This is also useful for the next section.

## Emulator

If you have little experience with programming, you will quickly realize that programming time is mostly spent on debugging. This means making changes, compiling, running, finding bugs, fixing them, and so on. This will be tedious if the *running* step involves copying the binaries on the SD card, inserting the card in the console, loading the game on the console… each time. The solution is to debug the game by running it on an emulator.

Fortunately there are several [emulators](http://gamebuino.com/wiki/index.php?title=Emulators) which work pretty well. Just install one of them. I personally use `gbsim` on Mac. It works fine, except sound, and grey color is flickering slowly.

## Resources

* [Gamebuino wiki](http://gamebuino.com/wiki/)
* [Gamebuino reference](http://gamebuino.com/wiki/index.php?title=Reference)
* [Arduino tutorials](https://www.arduino.cc/en/Tutorial/HomePage)
