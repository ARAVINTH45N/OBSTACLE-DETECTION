# Project Report
# Title:Obstacle Detection System Using Ultrasonic Sensor (HC-SR04) and Arduino UNO

### Name:Aravinth N
### Register No.: 212223060020
### Course: B.E Electronics and Communication Engineering
### Institution: Saveetha Engineering College, Chennai

## 1. Introduction:
Obstacle detection is a crucial part of automation systems, robotics, and assistive devices. This project involves designing an Ultrasonic-based Obstacle Detection System using an HC-SR04 sensor and Arduino UNO. The system is capable of detecting the distance to an obstacle and displaying it via the Serial Monitor.

## 2. Components Used:
Arduino UNO

HC-SR04 Ultrasonic Sensor

Jumper Wires

Breadboard (optional)

USB Cable (for power and programming)

## 3. Working Principle:
The HC-SR04 ultrasonic sensor consists of two modules:

Trigger Pin: Sends out an ultrasonic pulse.

Echo Pin: Receives the reflected pulse.

When the trigger pin emits an ultrasonic wave, it travels through the air and reflects back upon hitting an obstacle. The time between sending and receiving the wave is used to calculate the distance:

Distance (cm)
=
Duration
×
0.034
2
Distance (cm)= 
2
Duration×0.034
​
 
## 4. Circuit Diagram:
The connections are as follows:

![image](https://github.com/user-attachments/assets/c09ee2c8-8b44-4673-b707-f548342797ee)

VCC → 5V on Arduino

GND → GND on Arduino

Trig → Digital Pin 3

Echo → Digital Pin 2

## 5. Arduino Code:
```
cpp
Copy
Edit
#define echoPin 2
#define trigPin 3

long duration;
int distance;

void setup()
{
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  Serial.begin(9600);
}

void loop()
{
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
}
```
![Screenshot 2025-05-23 161304](https://github.com/user-attachments/assets/dacebbef-5f70-4ce8-adad-cf2609f69575)

## 6. Output:
The distance measured is shown on the Serial Monitor.
In the sample output shown below, the measured distance is 0 cm, indicating either no object detected or incorrect sensor positioning.
![Screenshot 2025-05-23 161258](https://github.com/user-attachments/assets/945b1326-c432-40bf-aeaa-37c1f6bd4cbe)


## 7. Applications:
Obstacle detection in robots

Parking assistance systems

Blind stick for visually impaired

Industrial automation

## 8. Conclusion:
This project demonstrates a simple yet effective way of detecting obstacles using ultrasonic sensors. It can be further enhanced using buzzers or LCDs for alert/visual feedback and integrated into autonomous systems.
