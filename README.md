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

(PIR) work by detecting infrared radiation emitted by objects. When an object with thermal radiation enters the detection range of the sensor, it will produce measurable thermal radiation changes to the PIR. The wireconnection between PIR and Arduino UNO:

![PIR](https://github.com/zczqy80/Watch-dog/assets/146266229/d387b905-8302-4bf4-87e3-9e38501d2cdb)


In the code programming of the Arduino IDE, the value of PIR pin could be used to detect the movement, which like following figure:

![image](https://github.com/zczqy80/Watch-dog/assets/146266229/05413fa1-331d-4b2f-8816-937c789920c0)

When an object moves within the detection range, the reading will become 1, otherwise it will be 0. The complete code for the PIR section has been uploaded.













