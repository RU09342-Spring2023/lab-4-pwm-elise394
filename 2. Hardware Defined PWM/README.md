My program starts with variables for the red, green, and blue parts of the RGB LED. I also made a variable to track which state I amin in a later switch statement. I then carry out the steps of stopping the watchdog timer, unlocking the MSP, and making functions for my LEDSetup and TimerB0Setup. I also set some initial values for each of my color variables.

My LED setup was not too bad. I assigned pin 6.0 for red, 6.1 for green, and 6.2 for blue. For each, I set them as outputs and cleared previous configurations. 

For the Timer B0 Setup function, I essentially used the format from lab 4.1 and changed the timing. I then moved on to the color changing magic. I used 5 different states to get the colors to change. I started with the LED completely red, with no green or blue, then gradually decreased the red and increased the green until it was all green. Then, once it was all green, I decreased the green and increased the blue until it was all blue. After that, I decreased the blue until it was all red. Then Ibrought it back to the beginning.  


The specifications for my lab were as follows:

You will need to use pins 6.0, 6.1, and 6.2 to drive an RGB LED. These will need to be configured with a PWM Period of 1ms. You need your RGB LED to cycle between the following colors in order:
- Red, Orange (Red + Green), Green, Cyan (Green + Blue), Blue, Purple (Red + Blue)

You need to cover colors in between them, meaning as you transition from Red to Orange, it shouldn't be just 2 colors. The amount of colors are up to you, but is needs to appear smooth in transition. The timing for cycling is up to you to determine as well.
