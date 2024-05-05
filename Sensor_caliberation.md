# Steps followed:- 
- Write a simple code for the sensor to detect objects in the surrounding.
- Write down the maximum distance for which the sensor can read values.
- Adjust the screw to change the maximum distance according to the application.
- For the line following robot, around 1-2cm max distance is more than enough.
- The screw can rotate maximum of about 270 degrees.
- There are 12 divisions marked around the screw casing. So the interval is about 30 degrees.
- So we plot a graph for degrees of turn v/s max distance that the sensor can detect.
- at 0 degrees, there is no sensor output itself and the LED doesn't blink.
- 30 degrees clockwise turn:- object at maximum distance which can be detected is 2 cm.
- at 60 degrees:- about 4 cm.
- at 90 degrees:- 4.8 cm.
- at 120 degrees:- 5.6 cm.
- at 150 degrees:- about 7 cm.
- at 180 degrees:- 10 cm.
- at 210 degrees:- 55 cm approx (not sure).
- at 240 degrees:- LED is always on. What does this mean?
- at 270 degrees:- LED is always on.
- The code used is as follows:- 
```c
int IRSensor = 9; // connect IR sensor module to Arduino pin D9
int LED = 13; // connect LED to Arduino pin 13

void setup(){
  Serial.begin(600); // Init Serial at 115200 Baud Rate.
  Serial.println("Serial Working"); // Test to check if serial is working or not
  pinMode(IRSensor, INPUT); // IR Sensor pin INPUT
  pinMode(LED, OUTPUT); // LED Pin Output
}

void loop(){
  int sensorStatus = digitalRead(IRSensor); // Set the GPIO as Input
  if (sensorStatus == 1) // Check if the pin high or not
  {
    // if the pin is high turn off the onboard Led
    digitalWrite(LED, LOW); // LED LOW
    Serial.println("Motion Detected!"); // print Motion Detected! on the serial monitor window
  }
  else  {
    //else turn on the onboard LED
    digitalWrite(LED, HIGH); // LED High
    Serial.println("Motion Ended!"); // print Motion Ended! on the serial monitor window
  }
}
```
- baud rate is kept at 600 bps which is enough for our application. For high speed line following robots, even greater baud rates are required. 
