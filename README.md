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





