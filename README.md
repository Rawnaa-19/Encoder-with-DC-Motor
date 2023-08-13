# Encoder with DC-Motor
## Table of Contents : 
1. [Introduction](#Introduction)
1. [The Encoder](#The-Encoder)
    - [Circuit Components](#Encoder-Circuit-Components)
    - [Circuit Wiring](#Encoder-Circuit-Wiring)
    - [Arduino Code](#Encoder-Arduino-Code)
    - [Code simulation](#Encoder-Code-simulation)
## Introduction
The Fourth task for the Electronics and Power Department is designing a rotary Encoder circuit with an Arduino UNO. A rotary encoder is a type of sensor that collects data and provide feedback based on a rotating device, which in this task is the DC motor.(Dejan, 2022) The encoder in general has four wires (Vcc , ground , A , and B). A and B are contact pins that generates signals. Output signals A and B depends on the direction in which the knob is turned. If the Knob was turned clockwise the output A is triggered first, and if the knob was turned counterclockwise then output B is triggered first.(Engineers, 2023) Encoders are used to count the number of times a motor has rotated<br><br>
<kbd> **Figure 1** <br><br>*Encoder Output Signals*<br><br> <kbd>![image](https://github.com/Rawnaa-19/Encoder-with-DC-Motor/assets/106926557/84696462-c6aa-4fd5-862d-67e4461f6cf0) (circuitrocks, 2020)</kbd></kbd>

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
<kbd> **Figure 2** <br><br>*Encoder Circuit Wiring*<br><br> <kbd>![image](https://github.com/Rawnaa-19/Encoder-with-DC-Motor/assets/106926557/84696462-c6aa-4fd5-862d-67e4461f6cf0) </kbd></kbd>


## References
[^1]: 
[^2]:
