# Distance-Measurement-using-ultrasonic-sensor-with-Arduino-Uno-and-Tinkercad-

This project uses an HC-SR04 ultrasonic sensor and Arduino UNO to measure the distance of objects in both centimeters and inches. The measured data is displayed on an I2C LCD. The project was simulated using Tinkercad, an online electronics simulator.

Table of Contents

Project Overview

Hardware Used

Software and Tools

Circuit Components

Code Explanation

Working Principle

Output

Getting Started

License



Project Overview

The objective of this project is to detect the distance of an object using the HC-SR04 ultrasonic sensor and display the result on a 16x2 I2C LCD screen. It is a simple example of sensor integration with Arduino and display systems, aimed at beginners and enthusiasts.

Hardware Used

Arduino UNO R3

HC-SR04 Ultrasonic Sensor

I2C 16x2 LCD Display

Breadboard and jumper wires

Software and Tools

Tinkercad Circuits – For circuit simulation

Arduino IDE – For writing and uploading the code

LiquidCrystal_I2C library

Circuit Components

Trig Pin (A0): Sends ultrasonic pulses

Echo Pin (A1): Receives reflected pulses

LCD (I2C): Displays distance in cm and inches

Power: 5V and GND from Arduino to sensor and LCD


Code Explanation

#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

#define trigPin A0 
#define echoPin A1 

long distanceInch;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  lcd.init();
  lcd.backlight();
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Simple  Circuits");
  delay(2000);
  lcd.clear();
  lcd.setCursor(0,0);  
  lcd.print("Distance:");
  lcd.setCursor(0,1);
  lcd.print("Distance:");
}

void loop() {
  long duration, distance;
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  distance = (duration / 2) / 29.1;  // in cm
  distanceInch = duration * 0.0133 / 2;  // in inches

  lcd.setCursor(9,0);  
  lcd.print("                "); 
  lcd.setCursor(9,0);   
  lcd.print(distance); 
  lcd.print(" cm");  

  lcd.setCursor(9,1);  
  lcd.print("                "); 
  lcd.setCursor(9,1);  
  lcd.print(distanceInch);
  lcd.print(" inch");  

  delay(200); 
}

Working Principle

1. The Trig pin sends a short ultrasonic pulse.
2. The Echo pin listens for the reflected signal.
3. The time taken for the echo to return is used to calculate distance.
4. The result is displayed in both centimeters and inches.

Formula:

Distance (cm) = (Duration / 2) / 29.1  
Distance (inches) = (Duration * 0.0133) / 2


Output

Displays real-time distance measurement on a 16x2 LCD:

Distance: 45 cm  
Distance: 17.7 inch


Getting Started

1. Simulate the circuit on Tinkercad Circuits
2. Upload the code using Arduino IDE
3. Observe distance changes in real-time on the LCD


License

This project is open-source and licensed under the MIT License.


