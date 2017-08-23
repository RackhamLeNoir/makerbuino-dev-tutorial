# Program skeleton

Before getting into game development, let's talk about the basic structure of a program. The library requires a bit more elements than a generic Arduino program.

## An Arduino program

The basic structure of an Arduino program looks like this:

    void setup()
    {
    }

    void loop()
    {
    }

The `setup` function is called once at startup (or reset). The `loop` function is repeated until the device is turned off or reset. The names are self-explanatory.

## A Gamebuino program

The basic structure of a Gamebuino program has a few things more:

    #include <SPI.h>
    #include <Gamebuino.h>
    Gamebuino gb;

    void setup()
    {
      gb.begin();
      gb.titleScreen(F("My game"));
    }

    void loop()
    {
      if (gb.update()){
      }
    }

The three first lines include the required libraries. SPI is a communication bus, which is used for the screen in the case of Gamebuino. the `gb` object is a handle to the console parts. You can see on the [reference page](http://gamebuino.com/wiki/index.php?title=Reference) that all the function and variable names start with `gb.`. This is because you access them through the `gb` object. You can rename it of course, but I don't recommend it. You will probably make copy/paste errors when using the reference.

In the setup function, we start with a call to `begin`, which initializes the handle. Call it before any call to any other function from the library. Then the call to `titleScreen` creates the… title screen. The parameter is the name of the program, which is displayed. To show you how useful is the reference, please read [this page](http://gamebuino.com/wiki/index.php?title=Gb.titleScreen) from the reference. It answers most of the questions you may have about the title screen. As I will discuss later: it is important to always have a button (usually `C`) mapped to a call to `titleScreen`. Otherwise your program would be *trapped* without the possibility to return to the Gamebuino main menu.

In the `loop` function we use this condition `if (gb.update())` because the logic of the game runs at 20 frames per second, which you can modify with [`setFrameRate`](http://gamebuino.com/wiki/index.php?title=Gb.setFrameRate). The `loop` function is called more often, because the microcontroler (ATmega 328) runs at 16MHz. This means it runs roughly 16 millions of instructions per second. The actual frequency of the `loop` function depends on the number of instructions executed in one call, which is unlikely to be the same at each call. Anyway, the thing to remember is to write your code inside this `if`, unless you know what you are doing.

You can already compile this program, and run it with an emulator, or the console. However beware with the console, there is no return to the menu yet.

# A game

Let's continue with the basic structure of a game. A game does three basic things:

* Manage inputs, in our case map buttons to actions
* Update the game data. This can be a ball moving for example. It does not depend on inputs, but changes every frame.
* Draw the content of the screen. I advise you to draw the full screen at each frame, which is the default behavior. If you would like to keep the previous display and update it, you will have to set [`display.persistence`](http://gamebuino.com/wiki/index.php?title=Gb.display.persistence) to `true`.

We perform these three tasks in dedicated functions for clarity purpose.

    #include <SPI.h>
    #include <Gamebuino.h>
    Gamebuino gb;

    void setup()
    {
      gb.begin();
      gb.titleScreen(F("My game"));
    }

    void input()
    {
      if(gb.buttons.pressed(BTN_C))
        gb.titleScreen(F("My game"));
    }

    void update()
    {
    }

    void draw()
    {
    }

    void loop()
    {
      if (gb.update()){
        input();
        update();
        draw();
      }
    }

There is currently nothing in `update` and `draw` since our game does nothing for now, thus it has nothing to show. However as I mentioned earlier there must always be a way to come back to the menu. The best is to map it to the `C` button. This is what we included in the `input` function.

