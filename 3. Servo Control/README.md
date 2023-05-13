I started by creating functions to set up the servo, buttons, and timer B. In the main function, I stopped the watchdog timer, unlocked the MSP, and called upon the other functions. 

In my servo setup function, I decided to use pin 6.0 to control the servo. I set it as an output, and cleared previous configurations for it.

In my button setup function, I set up button 2.3 as an input, enabled interrupts, set it as pulled up, and made it look for a low to high edge. I repeated the process with button 4.1. 

In my timer B setup function, I used SM clock, put the timer in up mode, enabled interrupts, and cleared it. I enabled the capture compare interrupt, set my period to 2kHz, and duty cycle so that it would be 75% of the period for the radius of the servo. 
 
For the interrupt for button 2.3, I started by clearing the flag. I then set it so that if timer B was less than the period, to increase the duty cycle by 10%. 
 
 For button 4.1's interrupt, I also started by clearing the flag. Then, I made it so that if timer B was running less than the period, I would increase the duty cycle by 10%. 
