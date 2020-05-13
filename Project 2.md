# Control   Systems   for   Reinforcement   Learning   -   Hexapod 
#### Problem Statement: 
To integrate different sensors to the Hexapod (18 DOF) and recreate the exact orientation of the bot in a computer. This is done to detect the state of the system at all instances.    
#### Constraints: 
1) Price    
2) Reliability of the data      
3) Delay in the information of the data    
4) Wiring Ideas     

#### Pipeline:   
We have to ideate a way for IMU integration with the Hexapod. 18+1(centre) IMU's are used. These have to be connected to a single microcontroller to send data for training the model.        
Input Data from 19 IMUs --> Arduino     

##### IMU: (Inertial Measurement Unit)     
Measures the orientation of a body using a combination of accelerometers, gyroscopes and magnetometers.      
An MPU-6050 IMU is used which combines a three-axis accelerometer and three-axis gyroscope, together with an on-board digital motion processor(DMP).      
MPU-6050 is a 6 DOF sensor (six outputs - three from accelerometer and three from gyroscope).     

#### Interfacing 19IMUs to the Arduino:   
Each IMU communicates with the Arduino through I2C protocol. Our task requires interfacing all the 19 IMUs to the Arduino.   
Using MPU-6050 IMUs , we can put them all on the I2C bus and connect each IMU's AD0 pin to a seperate digital pin on the Arduino. When you want to read from a specific IMU, set all AD0's to HIGH except the one you want to read (will be at LOW). So, the IMU set to LOW will have an address of 0X68 and all the others will have an address of 0x69 and hence the IMU from which we want to read the data is distinguished. So, we go through a loop of setting one to LOW and all others to HIGH to read through all the IMUs.     

Here we are using 19 IMUs whereas an Arduino UNO/Nano have only 14 digital pins. There are two ways to solve this:     
##### 1) Using Mega Versions: 
Arduino Mega 2560 Microcontroller has 54 digital I/O pins and hence all 19 IMUs can be comfortably interfaced.    
Advantages : Mega 2560 has higher flash memory (256kB) compared to Uno and can hence support a hefty code. It also has the most SRAM space with 8kb i.e. 4X more than the Uno. It also has 4X more EEPROM than the Uno        
Disadvantages : It is large in size and is also more expensive (around 700 INR) than Arduino UNO (around 250 INR)    

##### 2) Using GPIO Expander: 
I2C GPIO Expanders like MCP23017/PCA9555 have 16 bits of digital I/O pins and are inexpensive, but complicated to use. Also there are the 8575 (TI and NXP) having 16 digital I/O bits.     
PCA9698 has 40 bits of digital I/O and is extremely powerful but is relatively a bit more expensive, but is a good choice.    

##### Using Multiplexers:    
All 19 IMUs can be interfaced to a single Arduino using Multiplexers (TCA9548A).     
One TCA9548A 1-to-8 I2C Multiplexer acts as a gateway between the Arduino and eight I2C buses. One of these 8 buses is connected to the Arduino at a time. Since we are using 19 IMUs, we will need three multiplexers, which provides us 24 channels and hence 19 IMUs can be accomodated.       
###### Note: 
A TCA9548A Multiplexer costs around 300 INR and hence 3 of them together with Arduino cost around 1100-1200 INR. So, we can rather use Arduino Mega 2560 Microcontroller(around 700 INR) to which all 19 IMUs can be interfaced without any multiplexers/expanders.        

Another way is to use a software emulation of the I2C interface so that any of the digital I/O pins may act as an I2C pin. With this we can select arbitrary pairs of pins to act as SDA and SCL for each I2C device and then communicate with each device individually. So, this method will require 2 digital pins for each I2C device and in our case, since we have 19 IMUs will require 38 digital pins. So, if we are to go by this method, we have to choose Arduino Mega 2560 instead of Arduino Uno (or) we have to use I2C GPIO expanders. With this we can setup each slave with it's own I2C address. But, implementing this I2C slave protocol in software is quite difficult and requires some effort and is quite heavy to implement.       

The data obtained from the IMUs which is integrated by the microcontroller, is sent to a computer wirelessly (using bluetooth) (or) through a serial port, and this data is used to create a visual representation of the Hexapod using some modelling softwares.





