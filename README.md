# Watch-dog
An indoor environment monitor with the core function of detecting the flow of people at the door or corridor.

# Project brief
This project used the HCSR-04 module to detect distance and use PIR to detect human movement, thereby combining the two to achieve detection of people flow. The LCD and buzzer were used to output detection results. At the same time, two buttons were used as inputs in this project to change different output modes and adjust the detection distance.

![358e639cf4d6229150cf22367c2bab6](https://github.com/zczqy80/Watch-dog/assets/146266229/1d7f053b-05d1-4460-942f-f3b69beb90b8)

# Functions
1. Detect people flow: Real-time detection and recording of personnel enter and go out amount.
2. Sound remind: Different sounds when people enter or go out, display temperature and humidity in quiet mode.
3. Range adjustment: Through different distance limitation to adapt to different indoor environment.

# Hardware
Arduino UNO: microcontroller.

PIR sensor × 2: detects motion by sensing infrared radiation.

HC-SR04: Measures distance with the  reflection.

Buttons × 2: Push button that changes the level when pressed.

DHT-22: Measures the temperature and humidity.

Buzzer: Generates sound when an electrical signal input.

I2C LCD: Screen that can display text with I2C communication.

# PIR (Passive infrared sensor)

PIR work by detecting infrared radiation emitted by objects. When an object with thermal radiation enters the detection range of the sensor, it will produce measurable thermal radiation changes to the PIR. The wireconnection between PIR and Arduino UNO:

![PIR](https://github.com/zczqy80/Watch-dog/assets/146266229/d387b905-8302-4bf4-87e3-9e38501d2cdb)


In the programming of the Arduino IDE, the value of PIR pin could be used to detect the movement, which like following figure:

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/05413fa1-331d-4b2f-8816-937c789920c0)

When an object moves within the detection range, the reading will become 1, otherwise it will be 0. The complete code for the PIR section has been uploaded.

# HCSR-04

HCSR-04 is a sensor used to measure the distance between itself and the obstacles ahead by ultrasonic waves, which has a non-contact measurement range from 2 cm to 400 cm with a measurement accuracy of 3 mm. The wireconnection between HCSR-04 and Arduino UNO:

![HCSR-04](https://github.com/zczqy80/Watch-dog/assets/146266229/d4deaeb2-0583-410f-a61b-9d2bac45eb66)

In the programming of the Arduino IDE, the code to drive HCSR-04 like following figure:

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/f0187882-d27f-4d73-86a7-a8e9f01356b9)

As shown in the Figure 2-2, when the trigger was set to high, the chirped port would produce a set of 8 ultrasonic waves with a frequency of 40KHz. After a period of time, the echo port could receive the reflected wave. 
The time that the echo port maintains at high was the total time of the ultrasonic wave from transmission to reflection to reception. Therefore, the distance between the module and the target can be calculated. The complete code for the PIR section has been uploaded.

# Buttons

In this project, the user interface used two buttons as inputs. The first button was used as the adjustment button for the distance detection range which changed in units of 40cm between 0 and 240cm, while the second button was used to switch the output mode of the project back and forth between silent and audible modes. The wireconnection between single button and Arduino UNO:

![Button](https://github.com/zczqy80/Watch-dog/assets/146266229/3ff20289-94bf-4440-8faa-439c6cb351fe)

When the button is not pressed, its corresponding digital instrument reading is low, otherwise it is high. Therefore, it is possible to determine whether the button has been pressed by detecting the reading of the corresponding digital pin. After setting the counter, the number of times it has been pressed can be determined. When the number of presses reaches the upper limit, the count returns to 0.

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/08dfbb48-cc5e-417c-8118-c4b5de365890)

The complete code for the Button section has been uploaded.

# DHT-22

DHT-22 is used to detect the temperature and humidity of the environment when the project at quiet mode, After configuring the relevant libraries (<DHT.h>) in the Arduino IDE, the readings of the DHT-22 sensor can be read. The wireconnection between DHT-22 and Arduino UNO: 

![DHT-22](https://github.com/zczqy80/Watch-dog/assets/146266229/fded99af-4a71-4e4f-81a7-88fb7e696987)

In the programming of the Arduino IDE, the code to set up DHT-22 like following figure:

<img width="600" alt="image" src="https://github.com/zczqy80/Watch-dog/assets/146266229/ec28aa49-f7d8-4cde-a96b-f7e2b710081a">

Then, read the data of DHT-22 in the void of loop, the temperature and humidity could be measured. The complete code for the DHT-22 section has been uploaded.

# Buzzer

The buzzer could remind user with different tones when people enter or exit when the project at sound mode, The wireconnection between Buzzer and Arduino UNO: 

![Buzzer](https://github.com/zczqy80/Watch-dog/assets/146266229/2cf1f8f8-a01b-4679-99fe-5e5527fad92b)

The complete code for the Buzzer section has been uploaded, and here is a complete Buzzer project for reference: https://blog.csdn.net/c80486/article/details/52620972

# I2C LCD

LCD can display 16 by 2 characters. The LCD has multiple pins, each PIN has the following functions:

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/a15073b2-b41d-45ac-ad00-37f6d6eaa50a)

The LCD has 4-bit and 8-bit operating modes, and in 4-bit operating mode, only four pins need to be connected as inputs. And set the other two pins to set the read/write status and Register selection bits respectively. The connection between the LCD and Arduino is as follows:

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/3a3f5e5d-9f64-44ab-94b1-a5f099728b0b)

However, the LCD screen used in this project is equipped with an I2C module, which greatly simplifies the connection between it and Arduino, as shown in the following figure:

![LCD](https://github.com/zczqy80/Watch-dog/assets/146266229/030a8b49-3957-4a4d-ac0d-8c29e723a1f2)

The following is the configuration of an LCD equipped with an I2C module, which includes communication address, backlight, display bits, etc:

<img width="600" alt="image" src="https://github.com/zczqy80/Watch-dog/assets/146266229/c5c2ab33-1730-49d3-ae2d-b75083179dac">

After configuration is completed, the cursor can be set in the loop to determine the display position:

<img width="200" alt="image" src="https://github.com/zczqy80/Watch-dog/assets/146266229/3ac34c73-662f-49ad-a82b-c8da52e19dc9">

The complete code for the LCD section has been uploaded. If the program does not report an error and Lcd does not light up, it may be a problem with the communication address configuration of the LCD. You can visit the code in the following link to query the communication address of the LCD: https://blog.csdn.net/jh1513/article/details/90489191

# Combined Project system 

The circuit diagram of project were as follows:

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/0c7caea3-a5f4-4417-b9d6-2876f8001dd9)

The packaging of the project adopted laser wooden boards, and the design diagram of package and the final hardware of project were as follows:

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/464f654b-d5b2-4a76-ab49-732e4efdbcc8)

The file of box has been upload, The assembly process and final result of the box are as follows:

![7514a2eafb72f0626adfc970f1b2781](https://github.com/zczqy80/Watch-dog/assets/146266229/49e0e191-3a55-4057-b011-51c045c82c5e)

![25f38951df78903a7683c5fdb2d2c68](https://github.com/zczqy80/Watch-dog/assets/146266229/dbda3c64-0ca8-40d7-b3fb-fac92cd4bfed)

![09fadce31bab4974c44cce4170604f0](https://github.com/zczqy80/Watch-dog/assets/146266229/be9f6db6-49fe-43e0-bfe4-fe9bb10c19f6)

![3f0b5ae73d4dfa0f4dd1f1123680221](https://github.com/zczqy80/Watch-dog/assets/146266229/93883523-d1b2-43ad-80b3-c56210563ed3)

![61d0a849854ba1bf05872f5e9be7fb8](https://github.com/zczqy80/Watch-dog/assets/146266229/2ad3bc1a-21e3-4ce6-a75f-cfec519e6b07)

After the shell is assembled, the program is written into Arduino, and the flowchart of the program is shown below:

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/05f8a4ea-7f42-49b0-8e1d-2634982d11c8)

The complete code for the project has been uploaded.

# Test and result

A series of tests were conducted on the functionality of the project, and the test results are as follows:

1.	The project could successfully detect the direction of personnel in and out, so as to separately count the amount of personnel in and out, and displayed it on the LCD in real time. The measured distance of the item was also changed with the distance adjustment button.

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/98cb4ade-6d56-4c7b-baa8-7c6572185c44)

2.	When the project was in non-silent mode, it could remind the user through different tones when someone entered or exited. If someone entered the classroom, the buzzer would emit a high syllable, while someone leaved the classroom, the buzzer would emit a low syllable.

3.	When the project was adjusted to silent mode, and the current temperature and humidity could also be displayed on the LCD. 

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/ea0aea5b-2cb7-42bd-abef-01a60410b52e)

4.	When someone passed through the project quickly or simultaneously, the direction or amount of people flow detection might go wrong. This has been improved by adding isolation covers to the two PIRs.

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/0a6455bf-7f1f-4475-9a26-090bc7f807cf)

# Future work

1.	Limit the measurement range of a single PIR. 
2.	Increase the sampling frequency during continuous detection. 
3.	Add a master-slave structure to completely separate the two PIRs. 
4.	Enhance the connectivity between DHT-22 and main function.

# References

During the progress of this project, relevant data or inspiration was obtained from the following webpage:

PIR------The datasheet of PIR: https://www.farnell.com/datasheets/2718281.pdf

HCSR-04------The datasheet of HCSR-04: https://cdn.sparkfun.com/datasheets/Sensors/Proximity/HCSR04.pdf

Button------CASA0016 Workshop2: https://workshops.cetools.org/codelabs/CASA0016-Workshop-2/index.html#3 

DHT-22------CASA0016 Workshop4: https://workshops.cetools.org/codelabs/CASA0016-Workshop-4/index.html#3 









  
      









