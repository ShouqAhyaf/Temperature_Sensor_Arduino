# LM35: Temperature Sensor using Arduino
Design and Programming of an Electronic Circuit for an Analog Sensor.

## Table of Contents:
- Introduction
- Technologies
- Components Required
- Connections
- Block Diagram & Simulation
- Code

## Introduction
This project demonstrates the design and programming of an electronic circuit using the LM35 analog temperature sensor with Arduino. The circuit reads temperature values from the sensor and displays them on the serial monitor while controlling LEDs based on temperature thresholds.

## Technologies
Arduino IDE: Version 1.8.19

## Components Required
- Arduino UNO
- LM35 Temperature Sensor
- Breadboard
- 3 LEDs (Red, Yellow, Green)
- 3 Resistors (220 ohms)
- Jumper wires

## Connections
LM35 Sensor:

Connect VCC of LM35 to 5V on Arduino.
Connect GND of LM35 to GND on Arduino.
Connect the output pin of LM35 to A7 (analog input) on Arduino.
LEDs:

Connect the long leg (+ve) of each LED to a 220-ohm resistor.
Connect the other leg of each resistor:
Red LED to pin 6.
Yellow LED to pin 5.
Green LED to pin 4.
Connect the shorter leg of each LED to GND.
Power:

Use USB cable to connect Arduino to the computer.


## Block Diagram & Simulation
![image](https://github.com/user-attachments/assets/29a1067d-989d-4f7d-aba9-6b86b7065ba6)
 
The circuit reads the temperature from the LM35 sensor, displays the values in the serial monitor, and lights up the corresponding LED:
- Red LED: Temperature ≥ 30°C
- Yellow LED: Temperature ≤ 20°C
- Green LED: Temperature between 21°C and 29°C.

## Code
int sensorPin = 7;

int greenLED = 4;

int yellowLED = 5;

int redLED = 6;


void setup() {

  pinMode(greenLED, OUTPUT);
  
  pinMode(yellowLED, OUTPUT);
  
  pinMode(redLED, OUTPUT);
  
  Serial.begin(9600);

}


void loop() {

  int sensorValue = analogRead(sensorPin);
  
  float temp = sensorValue * 0.4882;



  Serial.print("Temperature : ");
  
  Serial.println(temp);
  
  delay(1000);



  if (temp >= 30) {
  
    digitalWrite(redLED, HIGH);
    
    digitalWrite(yellowLED, LOW);
    
    digitalWrite(greenLED, LOW);
  
  } else if (temp <= 20) {
  
    digitalWrite(redLED, LOW);
    
    digitalWrite(yellowLED, HIGH);
    
    digitalWrite(greenLED, LOW);
  } 
  else {
  
    digitalWrite(redLED, LOW);
    
    digitalWrite(yellowLED, LOW);
    
    digitalWrite(greenLED, HIGH);
  
  }
}

