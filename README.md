# exp3pushbuttonled
Don' write comment lines
```
#include <LPC214x.h>   // define LPC2148 Header file
#define led (1<<2)     // led macro for pin p0.2 of port0 (if they ask for dif port change 1<<2)
#define sw (1<<10)     // sw macro for pin p0.10 of port0 (same as above)
int main(void)
{
	unsigned int x;
	IO0DIR|=(~sw);   // configure P1.24 - P1.31 as input
	IO0DIR|=led;     // configure P1.16 - P1.23 as output
	while(1)
	{
		x = IOPIN0 & sw;   //save status of sw in variable x
		if(x==sw)          // if switch open
		{
			IOSET0|=led; // LED on
		}
		else               // if switch close
		{
			IOCLR0 = led;  // LED off  (interchange if else to turn on light while not pushing button
		}
	}
}
```
