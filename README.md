# Encoder with DC-Motor
## Table of Contents : 
1. [Introduction](#Introduction)
1. [The Encoder](#The-Encoder)
    - [Circuit Components](#Encoder-Circuit-Components)
    - [Circuit Wiring](#Encoder-Circuit-Wiring)
    - [Arduino Code](#Encoder-Arduino-Code)
    - [Code simulation](#Encoder-Code-simulation)
1. [References](#References)
## Introduction
The Fourth task for the Electronics and Power Department is designing a rotary Encoder circuit with an Arduino UNO. A rotary encoder is a type of sensor that collects data and provide feedback based on a rotating device, which in this task is the DC motor.[^2] The encoder in general has four wires (Vcc , ground , A , and B). A and B are contact pins that generates signals. Output signals A and B depends on the direction in which the knob is turned. If the Knob was turned clockwise the output A is triggered first, and if the knob was turned counterclockwise then output B is triggered first.[^3] Encoders are used to count the number of times a motor has rotated.<br><br>
<kbd> **Figure 1** <br><br>*Encoder Output Signals*<br><br> <kbd>![image](https://github.com/Rawnaa-19/Encoder-with-DC-Motor/assets/106926557/84696462-c6aa-4fd5-862d-67e4461f6cf0)<br><br> (circuitrocks, 2020)[^1]</kbd></kbd>

## The Encoder
In this task, I used the component "DC Motor with Encoder" in tinkercad. 
### Encoder Circuit Components
1. DC Motor with Encoder
2. L293D Motor driver "since we are dealing with dc motor"
3. Arduino UNO
4. Breadboard
5. Wires
   
### Encoder Circuit Wiring
The "DC Motor with Encoder" has 6 wires 2 for the motor and 4 for the encoder. The two connection for the motor are (motorPositive and motorNegative) its connected to the motor driver output pins similar to what I did in task 2. The 4 connections for the encoder are (Vcc , ground , channel A , and channel B) channel A and channel B are connected to the Arduino interrupt pins 2 and 3 respectively.<br><br>
<kbd> **Figure 2** <br><br>*Encoder Circuit Wiring*<br><br> <kbd> ![image](https://github.com/Rawnaa-19/Encoder-with-DC-Motor/assets/106926557/c346d05e-5711-4370-b099-cb7d4e232013)
</kbd></kbd>
### Encoder Arduino Code
```
#define motorA 5
#define motorB 6
int encoderPin1 = 2;
int encoderPin2 = 3;
volatile int lastEncoded = 0;
volatile long encoderValue = 0;
volatile long correctEncoderValue =0;
 
long lastencoderValue = 0;
 
int lastMSB = 0;
int lastLSB = 0;

void setup() {
   Serial.begin (9600);
   pinMode(encoderPin1, INPUT);
   pinMode(encoderPin2, INPUT);
   digitalWrite(encoderPin1, HIGH); //turn pullup resistor on
   digitalWrite(encoderPin2, HIGH); //turn pullup resistor on
   attachInterrupt(0, updateEncoder, CHANGE);
   attachInterrupt(1, updateEncoder, CHANGE);
  
   pinMode(motorA,OUTPUT);
   pinMode(motorB,OUTPUT);
}

void loop() {
   correctEncoderValue = encoderValue/4;
  
   Serial.println(correctEncoderValue);
  
   analogWrite(motorA,127);
   digitalWrite(motorB,LOW);

   delay(100);

}

void updateEncoder(){
  int MSB = digitalRead(encoderPin1); //MSB = most significant bit
  int LSB = digitalRead(encoderPin2); //LSB = least significant bit
 
  int encoded = (MSB << 1) |LSB; //converting the 2 pin value to single number
  int sum  = (lastEncoded << 2) | encoded; //adding it to the previous encoded value
 
  if(sum == 0b1101 || sum == 0b0100 || sum == 0b0010 || sum == 0b1011) encoderValue ++;
  if(sum == 0b1110 || sum == 0b0111 || sum == 0b0001 || sum == 0b1000) encoderValue --;
 
  lastEncoded = encoded; //store this value for next time
}
```
### Encoder Code simulation


https://github.com/Rawnaa-19/Encoder-with-DC-Motor/assets/106926557/d8d91bcc-ebb1-40fc-94bf-c4914cc3d628


## References
[^1]: circuitrocks. (2020, March 26). Incremental Photoelectric Rotary Encoder 400P/R. Circuitrocks. https://circuit.rocks/incremental-photoelectric-rotary-encoder-400p-r.html
[^2]: Dejan. (2022). How Rotary Encoder Works and How To Use It with Arduino. How to Mechatronics. https://howtomechatronics.com/tutorials/arduino/rotary-encoder-works-use-arduino/
[^3]: Engineers, L. M. (2023, February 1). How Rotary Encoder Works and Interface It with Arduino. Last Minute Engineers. https://lastminuteengineers.com/rotary-encoder-arduino-tutorial/
