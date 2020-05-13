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
Input Data from 19 IMU's --> Arduino     

##### IMU: (Inertial Measurement Unit)     
Measures the orientation of a body using a combination of accelerometers, gyroscopes and magnetometers.      
An MPU-6050 IMU is used which combines a three-axis accelerometer and three-axis gyroscope, together with an on-board digital motion processor(DMP).      
MPU-6050 is a 6 DOF sensor (six outputs - three from accelerometer and three from gyroscope).     

##### Interfacing 19IMU's to the Arduino:   
Each IMU communicates with the Arduino through I2C protocol. Our task requires interfacing all the 19 IMU's to the Arduino.   
Using MPU-6050 IMU's , we can put them all on the I2C bus and connect each IMU's AD0 pin to a seperate digital pin on the Arduino. Here we are using 19 IMU's whereas an Arduino UNO/Nano have only 14 digital pins. There are two ways to solve this:     
1) Using Mega Versions: Arduino Mega 2560 Microcontroller has 54 digital I/O pins and hence all 19 IMU's can be comfortably interfaced.    
Advantages : Mega 2560 has higher flash memory (256kB) compared to Uno and can hence support a hefty code. It also has the most SRAM space with 8kb i.e. 4X more than the Uno. It also has 4X more EEPROM than the Uno        
Disadvantages : It is large in size and is also more expensive (around 700 INR) than Arduino UNO (around 250 INR)

