My task for this lab was as follows:
You need to generate a 1kHz PWM signal with a duty cycle between 0% and 100%. Upon the processor starting up, you should PWM both of the on-board LEDs at a 50% duty cycle. Upon pressing the on-board buttons, the duty cycle of the LEDs should increase by 10%, based on which button you press. Once you have reached 100%, your duty cycle should go back to 0% on the next button press.
 - Button 2.1 Should control LED 1.0
 - Button 4.3 should control LED 6.6

I utilized the skeleton that Prof. Trafford included in the instructions.

```c
int main(void)
{
	WDTCTL = WDTPW | WDTHOLD;	// stop watchdog timer
	LEDSetup(); // Initialize our LEDS
	ButtonSetup();  // Initialize our button
	TimerA0Setup(); // Initialize Timer0
	TimerA1Setup(); // Initialize Timer1
	__bis_SR_register(LPM0_bits + GIE);       // Enter LPM0 w/ interrupt
}
```

The first thing I did was change timer A to timer B. Then, I structured myself a bigger skeleton with functions. I then made sure to unlock the MSP in the main function in order for it to be programmed. After that, I got to setting up the buttons. 

In my LEDSetup function, I first set the red LED (1.0) as an output and cleared any previous settings for it. I repeated the process with the green LED. 

In my ButtonSetup function, I started by setting button 2.3 as an input. I then enabled the register and interrupt, configured the button as pulled up, and made it search for the low to high edge. I repeated the same process with button 4.1. 

For my TimerB0Setup function, I used SM clock, put it in up mode, and enabled the interrupt for the timer and capture compare register. I set the timer to 1000Hz, or 1kHz, and set the duty cycle to 50%. 

The next few lines of interrupts just kind of happened to make the interrupts do something. And then I set the interrupt of button 2.3 to clear, and if the duty cycle was fully on, then I set the brightness off. If the cycle was not at 100%, I incrementally increased it by 10% until it was at 100%. I repeated the same set of steps for the interrupt of button 4.1. 

Again, interrupts happened. I think I took some inspiration from Texas Instruments' website. I tried my best. 

I may have had to add in a function for timer B1 but honestly I am not sure why I would need another timer for another button. 
