# MicroMouse   Maze  -  TechSoc   Challenge 
#### Problem Statement: 
To build an autonomous, self-contained robot (Micromouse) which can get to the centre of a maze in the shortest possible time. 

##### Constraints: 
1) The micromouse can't be larger than 16cm x 16cm x 10 cm. So it has to be made with components that are small in size and those that can be compactly packed.       
2) The micromouse must be self-contained - So, we have to use a portable power source like Power Bank/Batteries       

#### Given Solution:
##### Dimension: 10cm x 9cm x 9cm    
The bot uses an ESP32 Microcontroller and a 5V Power Bank as Power Source.     
Other components used:     
VL53L0X Laser ToF Flight Time Ranging Sensor Module - Operational Voltage Range - 2.8V to 5V    
US-100 Ultrasonic Sensor - Operational Voltage - 2.4V - 5V  (Can be replaced with the much cheaper HC-SR04 Ultrasonic Sensor)     
N20 6V 100RPM Micro Metal Gear Motor with Encoder - Operational Voltage Range - 3V to 6V     

#### Alternatives:   
##### Microcontroller: 
ESP32 can be replaced with STM32 Microcontroller due to the following reasons :       
Price - ESP32 costs around 900-1000 INR whereas STM32 costs around 300-400 INR     
STM32 also has an amazing speed and can handle projects quite rapidly. It also comes with two I2C buses and with two more analog channels than ESP32. Additionally, it also has 32 GPIO pins compared to 24 in other microcontrollers.    
STM32 can be easily interfaced with different kinds of electronic components like sensors, displays, cameras, motors, etc.  IDE's like Keil MDK ARM(uVision5 IDE)/CoIDE could be used with STM32.    
STM32 has an operational voltage oof 2.0V to 3.6V and hence can be used with a 5V Power Source.    

##### IDE:    
ESP32 can be programmed using Arduino IDE or PlatformIO.       
PlatformIO is an open-source Integrated Development Environment is not complicated, reliable and is easy to understand. It is also easier to setup and can be used to program myriad of microcontroller boards easily. 
