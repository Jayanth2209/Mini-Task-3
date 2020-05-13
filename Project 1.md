# Green Lantern Ring 
#### Problem Statement: 
To make a ring that automatically glows when you wear it.    
#### Constraints:  
1) All the components should be small in size so as to comprise a ring.   
2) The circuit must be powered by button cells as they are the smallest source of power.
3) Should consume less power as it needs to run for a long time.     

#### Solution: 
The actual solution involves a push button which when worn is pressed and the circuit lights up. The problem with this is that it continuously presses your skin and hence might cause some pain/depression. To avoid this, we need to use some electronic component that activates when touched - So, we can use Capacitive Touch Sensor IC for this purpose.   
##### IQS223 Sensor: 
A 3 Channel capacitive proximity and touch controller which works within the supply voltage range of 1.8V to 3.3V and is small in size (3mm x 3mm x 0.75mm). Therefore, we can use two button cells (3.0V - 1.5V each) to power the circuit. This device has 4 pins for the connection of the sense electrodes which consist of 3 receivers and 1 transmitter. The transmitter output pin is also shared with a proximity output detection status. The device is also equipped with Automatic Tuning Implementation (ATI) to adjust the device for optimal sensitivity and compensate for the environmental changes.     
The device will be activated when it is brought close to the hand/finger and the proximity output pin becomes active HIGH. This device comes with the Tap & Hold feature i.e. it will be activated as long as the finger is tapped and stays in contact with it and hence will serve our purpose.    
IQS223 IC has configurable low power modes to reduce current consumption during idle/sleep stages of battery applications. It will wake up from this Low Power mode upon a valid proximity detection and immediately zoom to Normal Power mode.     
##### Microcontroller: 
Microcontroller too has to be small in size and has to operate within 3V.    
ATTINY45 is a high performance, low-power microcontroller, and is tiny as the name suggests and works within 1.8V to 5.5V range. It also has the required sleep mode feature. The sensor can be interfaced to the microcontroller and it can be programmed using AtmelStudio.   

These components are suitably wired and the microcontroller is suitably programmed so as to power up the LED when the ring is worn. To reduce the size even more an LED strip can be used instead of an LED.
