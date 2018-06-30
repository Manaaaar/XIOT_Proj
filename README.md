# XIOT_Proj
Write c or arduino function to control one input and output (IO Pins) the input pin is a switch as interrupt once it pressed it should lighting the led connected to output pin. if the switch pressed must send “pressed” to the serial monitor only one time also send the LED states ”ON” or “OFF”

assumbtions
using Atmega16
switch is connected to pin 0  in PORTB using Pull Down configuration
Led is connected to pin 0 in PORTC using Positive Logic configuration


//code



#include <avr/io.h>
#include <stdio.h>

int main(void)
{
	DDRB = DDRB & (~(1<<PB0)); // configure pin 0 of PORTB to be input pin
	DDRC = DDRC | (1<<PC0);    // configure pin 0 of PORTC to be output pin
	//initialize led
	PORTC = PORTC & (~(1<<PC0));  // led1 is off at the beginning
	
    
		//check if the  switch is pressed to print only once
    	 if(PINB & (1<<PB0))
		{ 
			printf("pressed");
			printf("ON");
			 
		}		
		
		
		else
		{
			printf("pressed");
			printf("OFF");
			
		}  
	
while(1)
    {
    
		//check if the  switch is pressed
    	 if(PINB & (1<<PB0))
		{ 
			PORTC = PORTC | (1<<PC0); // turn on led
			printf("pressed");
			printf("ON");
			 
		}		
		
		
		else
		{
			PORTC = PORTC & (~(1<<PC0));   // turn off led
			printf("pressed");
			printf("OFF");
			
		}  
	} 
  
}


