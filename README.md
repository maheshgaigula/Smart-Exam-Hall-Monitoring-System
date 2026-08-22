\# Smart Exam Hall Monitoring and Management System



\## 📌 Project Overview



The \*\*Smart Exam Hall Monitoring and Management System\*\* is an embedded system designed to assist in managing and monitoring examination sessions.



The system uses an \*\*ARM7-based LPC2148 microcontroller\*\* and integrates multiple peripherals including an LCD, 4×4 keypad, RTC, ADC, LM35 temperature sensor, multiplexed 7-segment display, LEDs, buzzer, and external interrupts.



The system allows the user to configure examination parameters, monitor examination time, pause/resume the examination, monitor temperature, and provide visual and audio alerts.



\---



\## 🎯 Objectives



\- Provide controlled examination session management.

\- Allow authorized users to configure examination settings.

\- Display real-time clock and date information.

\- Set examination start time and duration.

\- Display remaining examination time.

\- Monitor temperature using an LM35 sensor.

\- Provide pause/resume functionality using an external interrupt.

\- Provide LED warnings as examination time decreases.

\- Activate a buzzer when the examination time expires.

\- Protect configuration settings using a password.



\---



\## ⚙️ Hardware Used



\- LPC2148 ARM7 microcontroller

\- 16×2 LCD

\- 4×4 matrix keypad

\- RTC

\- LM35 temperature sensor

\- ADC

\- Two-digit multiplexed 7-segment display

\- LEDs

\- Buzzer



\---



\## 💻 Software and Technologies



\- Embedded C

\- ARM7 / LPC2148

\- Keil µVision

\- GPIO

\- ADC

\- RTC

\- External Interrupts

\- LCD interfacing

\- Keypad interfacing

\- 7-segment interfacing

\- Register-level programming



\---



\## 🔐 Password-Protected Configuration



The system uses a password to protect examination configuration settings.



When the configuration interrupt is triggered:



1\. The user is asked to enter the password.

2\. The entered password is compared with the stored password.

3\. The user gets limited attempts.

4\. After successful authentication, the user can access the configuration menu.



The configuration menu provides options for:



\- RTC time

\- RTC date

\- Examination start time

\- Examination duration

\- Password modification



\---



\## ⏰ Examination Time Management



The administrator can configure:



\- Examination start hour

\- Examination start minute

\- Examination duration



The system continuously compares the configured examination start time with the RTC.



Once the configured start time is reached, the examination session begins automatically.



\---



\## ⏱️ Remaining Time Display



The remaining examination time is displayed using a \*\*two-digit multiplexed 7-segment display\*\*.



The system calculates:



Remaining Time = Exam Duration - Elapsed Time

Paused time is excluded from the elapsed examination time.



\## ⏸️ Pause / Resume Function



An external interrupt is used to pause and resume the examination.



When the pause interrupt occurs:



The current examination time is recorded.

The examination countdown is paused.

The pause count is incremented.



When the interrupt occurs again:



The system resumes the examination.

The paused duration is excluded from the examination countdown.



The LCD displays the pause count and current pause status.



\##  🌡️ Temperature Monitoring



An LM35 temperature sensor is connected to the LPC2148 ADC.



The signal flow is:



LM35

&#x20; ↓

Analog Voltage

&#x20; ↓

LPC2148 ADC

&#x20; ↓

ADC Conversion

&#x20; ↓

Temperature Calculation

&#x20; ↓

LCD Display



The temperature is displayed in degrees Celsius.



\##  🚦 LED Warning System



The system provides visual warnings based on the remaining examination time.



Remaining Time	Indicator

More than 15 minutes	Normal

15 minutes or less	LED3

10 minutes or less	LED2

5 minutes or less	LED1

0 minutes	Buzzer



\##  🔔 Examination Completion



When the remaining examination time reaches zero:



Remaining Time = 0

&#x20;       ↓

&#x20;   Exam Ends

&#x20;       ↓

&#x20;     Buzzer



The buzzer provides an audio indication that the examination session has finished.



\##  🧩 System Architecture

&#x20;                  

&#x20;                   ┌─────────────┐

&#x20;                   │       LPC2148   │

&#x20;                   │        ARM7     │

&#x20;                   └───────┬─────┘

&#x20;                             │

&#x20;      ┌────────┬─────┼──────┬───────────┐

&#x20;      │          │       │        │              │

&#x20;      ▼          ▼       ▼        ▼              ▼

&#x20;    LCD         Keypad   RTC      ADC            EINT

&#x20;      │           │       │        │              │

&#x20;      │           │       │       LM35       Pause / Resume

&#x20;      │           │       │

&#x20;      └─────────┴─────┴───────────┐

&#x20;                                          │

&#x20;                                          ▼

&#x20;                                       Exam Management

&#x20;                                          │

&#x20;                             ┌─────────┼──────────────────┐

&#x20;                             ▼           ▼                       ▼

&#x20;                        7-Segment        LEDs                    Buzzer

&#x20;                      Remaining Time    Warnings               Exam End





\##  📁 Project Structure

Smart-Exam-Hall-Monitoring-System/

│

├── Smart\_Exam\_Hall\_Monitoring\_and\_Management\_System1.c

├── project.c

├── project.h

├── project\_declaration.h

├── project\_definations.c

├── declaration.h

├── all\_macro1.h

└── README.md

File Description

File	Purpose

Smart\_Exam\_Hall\_Monitoring\_and\_Management\_System1.c	Main application logic and interrupt handling

project.c	LCD, keypad, ADC, LM35, delay and 7-segment driver implementations

project.h	Function declarations for peripheral modules

project\_declaration.h	Function declarations for exam-management and RTC functions

project\_definations.c	Password, RTC, exam configuration and exam-management functions

declaration.h	Peripheral function declarations

all\_macro1.h	Microcontroller definitions, data types, macros and pin configurations

README.md	Project documentation



\##  🔄 Overall Working Flow

Power ON

&#x20;  ↓

Initialize LPC2148 peripherals

&#x20;  ↓

Initialize LCD, keypad, ADC, 7-segment and RTC

&#x20;  ↓

Display Smart Exam Monitor System

&#x20;  ↓

Wait for configuration interrupt

&#x20;  ↓

Password Authentication

&#x20;  ↓

Configure RTC / Exam Time / Duration / Password

&#x20;  ↓

Wait for configured exam start time

&#x20;  ↓

Start Examination

&#x20;  ↓

Display Remaining Time

&#x20;  ↓

Monitor Temperature

&#x20;  ↓

Monitor Pause / Resume Interrupt

&#x20;  ↓

Generate LED Warnings

&#x20;  ↓

Remaining Time = 0

&#x20;  ↓

Activate Buzzer

&#x20;  ↓

Exam Completed





\##   📚 Embedded Concepts Demonstrated



This project demonstrates practical implementation of:



ARM7 microcontroller programming

Embedded C

GPIO programming

Register-level programming

LCD interfacing

Matrix keypad interfacing

ADC interfacing

LM35 temperature sensing

RTC programming

External interrupts

VIC interrupt configuration

Multiplexed 7-segment display

Bit manipulation

Embedded timing and delays

Password-based access control

Real-time event handling





\##  🚀 Future Improvements



Possible future improvements include:



Multiple examination hall support

Centralized monitoring through CAN or UART

Data logging

EEPROM-based password and configuration storage

Automatic attendance integration

PC/mobile monitoring interface

Real-time examination reports



\##  👨‍💻 Author



Mahesh Gaigula



Electronics and Communication Engineering

Embedded Systems



\##  📌 Project Type



Embedded Systems Project — ARM7 / LPC2148



The project was developed as a practical embedded-system application integrating multiple hardware peripherals and real-time event management.

