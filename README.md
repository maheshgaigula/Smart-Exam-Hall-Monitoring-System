\# Smart Exam Hall Monitoring and Management System



\## 📌 Project Overview



The \*\*Smart Exam Hall Monitoring and Management System\*\* is an embedded system designed to assist in managing and monitoring examination sessions.



The system uses an \*\*ARM7-based LPC2148 microcontroller\*\* and integrates multiple peripherals including an LCD, 4×4 keypad, RTC, ADC, LM35 temperature sensor, multiplexed 7-segment display, LEDs, buzzer, and external interrupts.



The system allows the user to configure examination parameters, monitor examination time, pause/resume the examination, monitor temperature, and provide visual and audio alerts.



\---



\## 🎯 Objectives



\* Provide controlled examination session management.

\* Allow authorized users to configure examination settings.

\* Display real-time clock and date information.

\* Set examination start time and duration.

\* Display remaining examination time.

\* Monitor temperature using an LM35 sensor.

\* Provide pause/resume functionality using an external interrupt.

\* Provide LED warnings as examination time decreases.

\* Activate a buzzer when the examination time expires.

\* Protect configuration settings using a password.



\---



\## ⚙️ Hardware Requirements



\* LPC2148 ARM7 microcontroller

\* 16×2 LCD

\* 4×4 matrix keypad

\* Real-Time Clock (RTC)

\* LM35 temperature sensor

\* ADC

\* Two-digit multiplexed 7-segment display

\* LEDs

\* Buzzer

\* External interrupt switches

\* Connecting wires / breadboard or project hardware setup

\* Suitable power supply



\---



\## 💻 Software Requirements



\* Embedded C

\* ARM7 / LPC2148

\* Keil µVision IDE

\* ARM7 compiler/toolchain

\* GPIO programming

\* ADC programming

\* RTC programming

\* External interrupt programming

\* LCD interfacing

\* Keypad interfacing

\* 7-segment interfacing

\* Register-level programming

\* VIC interrupt controller



\---



\## 🧩 System Architecture



!\[System Architecture](system\_architecture.png)



The LPC2148 acts as the main controller and interfaces with the LCD, keypad, RTC, ADC, LM35 temperature sensor, external interrupt, multiplexed 7-segment display, LEDs, and buzzer.



```text

&#x20;                        ┌─────────────┐

&#x20;                        │   LPC2148       │

&#x20;                        │    ARM7         │

&#x20;                        └──────┬──────┘

&#x20;                                 │

&#x20;         ┌──────────┬───────┼────────┬────────┐

&#x20;         │             │         │          │          │

&#x20;         ▼          ▼           ▼          ▼          ▼

&#x20;       LCD        Keypad        RTC        ADC        EINT

&#x20;                                            │       Pause / Resume

&#x20;                                           LM35

&#x20;                                            │

&#x20;                                            ▼

&#x20;                                     Temperature

&#x20;                                     Monitoring



&#x20;                               ┌─────────────────┐

&#x20;                               │ Exam Management      │

&#x20;                               └────────┬────────┘

&#x20;                                           │

&#x20;                             ┌──────────┼──────────┐

&#x20;                             ▼             ▼            ▼

&#x20;                        7-Segment         LEDs       Buzzer

&#x20;                        Remaining        Warnings    Exam End

&#x20;                           Time

```



\---



\## 📸 Project Demonstration



\### 🔢 Keypad and LCD Display



The 4×4 matrix keypad is used for user input and configuration, while the LCD displays system information, examination status, temperature, and other parameters.



!\[Keypad and LCD Display](images/keypad\_and\_display.jpg)



\### 🔧 Project Hardware



The complete hardware setup of the Smart Exam Hall Monitoring and Management System.



!\[Project Hardware](images/project\_hardware.jpg)



\### 🌡️ Temperature Display



The LM35 temperature sensor is interfaced with the LPC2148 ADC, and the measured temperature is displayed on the LCD.



!\[Temperature Display](images/temperature\_display.jpg)



\---



\## 📁 Project Structure



```text

Smart-Exam-Hall-Monitoring-System/

│

├── Smart\_Exam\_Hall\_Monitoring\_and\_Management\_System1.c

├── project.c

├── project.h

├── project\_declaration.h

├── project\_definations.c

├── declaration.h

├── all\_macro1.h

├── system\_architecture.png

├── project_images/

│   ├── keypad\_and\_display.jpg

│   ├── project\_hardware.jpg

│   └── temperature\_display.jpg

└── README.md

```



\### File Description



| File / Folder                                         | Purpose                                                                |

| ----------------------------------------------------- | ---------------------------------------------------------------------- |

| `Smart\_Exam\_Hall\_Monitoring\_and\_Management\_System1.c` | Main application logic and interrupt handling                          |

| `project.c`                                           | LCD, keypad, ADC, LM35, delay and 7-segment driver implementations     |

| `project.h`                                           | Function declarations for peripheral modules                           |

| `project\_declaration.h`                               | Function declarations for exam-management and RTC functions            |

| `project\_definations.c`                               | Password, RTC, exam configuration and exam-management functions        |

| `declaration.h`                                       | Peripheral function declarations                                       |

| `all\_macro1.h`                                        | Microcontroller definitions, data types, macros and pin configurations |

| `system\_architecture.png`                             | System architecture diagram                                            |

| `project_images/`                                             | Real project hardware and demonstration images                         |

| `README.md`                                           | Project documentation                                                  |



\### Major Modules



\* \*\*LPC2148 ARM7\*\* – Main controller

\* \*\*16×2 LCD\*\* – Displays time, date, temperature and examination information

\* \*\*4×4 Matrix Keypad\*\* – User input and configuration

\* \*\*RTC\*\* – Real-time clock and date management

\* \*\*LM35 + ADC\*\* – Temperature monitoring

\* \*\*External Interrupts\*\* – Configuration and pause/resume control

\* \*\*2-Digit 7-Segment Display\*\* – Displays remaining examination time

\* \*\*LED Warning System\*\* – Provides time-based visual warnings

\* \*\*Buzzer\*\* – Provides examination completion alert

\* \*\*Exam Management Logic\*\* – Handles start time, duration, pause/resume and remaining-time calculation



\---



\## 🔐 Password-Protected Configuration



The system uses a password to protect examination configuration settings.



When the configuration interrupt is triggered:



1\. The user is asked to enter the password.

2\. The entered password is compared with the stored password.

3\. The user gets limited password attempts.

4\. After successful authentication, the user can access the configuration menu.



The configuration menu provides options for:



\* RTC time

\* RTC date

\* Examination start time

\* Examination duration

\* Password modification



\---



\## ⏰ Examination Time Management



The administrator can configure:



\* Examination start hour

\* Examination start minute

\* Examination duration



The system continuously compares the configured examination start time with the RTC.



Once the configured start time is reached, the examination session begins automatically.



\---



\## ⏱️ Remaining Time Display



The remaining examination time is displayed using a \*\*two-digit multiplexed 7-segment display\*\*.



The system calculates the remaining examination time as:



```text

Remaining Time = Exam Duration - Effective Elapsed Time

```



The system also accounts for the paused duration so that the examination countdown does not decrease while the examination is paused.



\---



\## ⏸️ Pause / Resume Function



An external interrupt is used to pause and resume the examination.



When the pause interrupt occurs:



\* The current examination time is recorded.

\* The examination countdown is paused.

\* The pause count is incremented.



When the interrupt occurs again:



\* The examination resumes.

\* The paused duration is excluded from the examination countdown.



The LCD displays the pause count and current pause status.



\---



\## 🌡️ Temperature Monitoring



An LM35 temperature sensor is connected to the LPC2148 ADC.



The temperature measurement process is:



```text

LM35 Temperature Sensor

&#x20;         ↓

&#x20;   Analog Voltage

&#x20;         ↓

&#x20;     LPC2148 ADC

&#x20;         ↓

&#x20;    ADC Conversion

&#x20;         ↓

&#x20;Temperature Calculation

&#x20;         ↓

&#x20;     LCD Display

```



The temperature is calculated and displayed in degrees Celsius.



\---



\## 🚦 LED Warning System



The system provides visual warnings based on the remaining examination time.



| Remaining Time       | Indicator |

| -------------------- | --------- |

| More than 15 minutes | Normal    |

| 15 minutes or less   | LED3      |

| 10 minutes or less   | LED2      |

| 5 minutes or less    | LED1      |

| 0 minutes            | Buzzer    |



The LED warning level changes automatically as the examination approaches completion.



\---



\## 🔔 Examination Completion



When the remaining examination time reaches zero:



```text

Remaining Time = 0

&#x20;       ↓

&#x20;   Exam Ends

&#x20;       ↓

&#x20;     Buzzer

```



The buzzer provides an audio indication that the examination session has finished.



\---



\## 🔄 Overall Working Flow



```text

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

```



\---



\## 🛠️ Build and Execution



\### 1. Open the Project



Open the project source files in \*\*Keil µVision\*\* with the appropriate ARM7/LPC2148 project configuration.



\### 2. Configure the Target



Select the target device and configure the project for the \*\*LPC2148 ARM7 microcontroller\*\*.



\### 3. Add Source Files



Make sure all required source and header files are included in the Keil project.



\### 4. Compile the Project



Build the project using the Keil build option and check for compilation errors and warnings.



\### 5. Generate the HEX File



Configure the project to generate the required `.hex` file after a successful build.



\### 6. Program the Microcontroller



Use a compatible LPC2148 programming/flashing tool to transfer the generated HEX file to the microcontroller.



\### 7. Connect the Hardware



Connect the LCD, keypad, RTC, LM35, 7-segment display, LEDs, buzzer, and external interrupt switches according to the project hardware configuration.



\### 8. Run the System



Power on the system and verify initialization, configuration, examination timing, temperature monitoring, pause/resume operation, LED warnings, and examination completion.



\---



\## 🧪 Testing and Verification



Each major module was tested individually before integrating it into the complete system.



| Module             | Test Performed      | Expected Result                                    |

| ------------------ | ------------------- | -------------------------------------------------- |

| LCD                | Display test        | Text and values displayed correctly                |

| Keypad             | Key press test      | Correct key input detected                         |

| RTC                | Time/date test      | Correct time and date displayed                    |

| ADC + LM35         | Temperature test    | Temperature measured and displayed                 |

| 7-Segment          | Countdown test      | Remaining time displayed correctly                 |

| External Interrupt | Pause/resume test   | Examination pauses and resumes correctly           |

| LEDs               | Warning test        | Correct LED activated according to remaining time  |

| Buzzer             | Completion test     | Buzzer activates when examination ends             |

| Password           | Authentication test | Configuration accessible only after valid password |



\### Integrated Testing



After individual module verification, the modules were integrated and tested as a complete system.



The following complete flow was verified:



```text

Power ON

&#x20;  ↓

Peripheral Initialization

&#x20;  ↓

Password Authentication

&#x20;  ↓

Exam Configuration

&#x20;  ↓

Exam Start

&#x20;  ↓

Countdown

&#x20;  ↓

Temperature Monitoring

&#x20;  ↓

Pause / Resume

&#x20;  ↓

LED Warnings

&#x20;  ↓

Exam Completion

&#x20;  ↓

Buzzer Alert

```



\---



\## 📸 Output and Demonstration



The repository contains real project demonstration images showing the implemented hardware and system output.



\### Keypad and LCD Output



!\[Keypad and LCD Display](images/keypad\_and\_display.jpg)



\### Complete Hardware Setup



!\[Project Hardware](images/project\_hardware.jpg)



\### Temperature Monitoring Output



!\[Temperature Display](images/temperature\_display.jpg)



These images provide visual evidence of the implemented hardware and system operation.



\---



\## ⚠️ Challenges Faced and Solutions



\### 1. Multiplexed 7-Segment Display



\*\*Challenge:\*\*

Displaying the remaining examination time using a two-digit multiplexed 7-segment display requires continuous refreshing of both digits.



\*\*Solution:\*\*

Implemented multiplexing logic with appropriate timing and digit selection to provide a stable display.



\### 2. Pause / Resume Timing



\*\*Challenge:\*\*

The examination countdown should not decrease while the examination is paused.



\*\*Solution:\*\*

The pause time is recorded and excluded from the effective elapsed examination time.



\### 3. Temperature Measurement



\*\*Challenge:\*\*

The LM35 provides an analog voltage that must be converted into a meaningful temperature value.



\*\*Solution:\*\*

The ADC is used to convert the analog signal into a digital value, which is then processed to calculate the temperature.



\### 4. External Interrupt Handling



\*\*Challenge:\*\*

Configuration and pause/resume operations must respond to external events without affecting normal system operation.



\*\*Solution:\*\*

External interrupts and the VIC interrupt controller are used to handle event-driven operations.



\### 5. Multiple Peripheral Integration



\*\*Challenge:\*\*

Several peripherals must operate together while maintaining correct timing and system behavior.



\*\*Solution:\*\*

Each module was developed and tested individually before integrating the modules into the final application.



\---



\## 📚 Embedded Concepts Demonstrated



This project demonstrates practical implementation of:



\* ARM7 microcontroller programming

\* Embedded C

\* GPIO programming

\* Register-level programming

\* LCD interfacing

\* Matrix keypad interfacing

\* ADC interfacing

\* LM35 temperature sensing

\* RTC programming

\* External interrupts

\* VIC interrupt configuration

\* Multiplexed 7-segment display

\* Bit manipulation

\* Embedded timing and delays

\* Password-based access control

\* Real-time event handling

\* Modular peripheral integration



\---



\## 🚀 Future Improvements



Possible future improvements include:



\* Multiple examination hall support

\* Centralized monitoring through CAN or UART

\* Data logging

\* EEPROM-based password and configuration storage

\* Automatic attendance integration

\* PC/mobile monitoring interface

\* Real-time examination reports



\---



\## 👨‍💻 Author



\*\*Mahesh Gaigula\*\*



Electronics and Communication Engineering

Embedded Systems



\---



\## 📌 Project Type



\*\*Embedded Systems Project — ARM7 / LPC2148\*\*



The project was developed as a practical embedded-system application integrating multiple hardware peripherals and real-time event management.



