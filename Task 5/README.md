## Task 5

**Interfacing VSDSquadron Mini (CH32V003F4U6) and Raspberry Pi Pico (RP2040)**  

---

### Overview
This project demonstrates controlling Raspberry Pi Pico with our VSDSqradron Mini using comunication protocol Universal Synchronous Asynchronous Receiver-Transmitter (USART) at a common baud rate (e.g., 9600 bps). VSDSquadron Mini is powered by CH32V003F4U6 chip with 32-bit RISC-V core based on RV32EC instruction set and on the other hand, Raspberry Pi Pico is based on ARM Cortex-M0+ based microcontroller. In our project, We are controlling the ARM based Raspberry Pi Pico with our RISC V based VSDSqradron Mini board. It can also be done vice versa.  

---

### Components Required 
1. VSDSquadron Mini (CH32V003F4U6)    
2. Raspberry Pi Pico (RP2040)  
3. Connecting Wires
4. Bread Board
5. Power Supply   

---

### Software Required  
1. Arduino IDE
2. Thonny
   
---

### Raspberry Pi Pico Pin diagram

![image](https://github.com/user-attachments/assets/c1be58d4-2512-489e-8f2a-b35ba4e41d51)

---

### CH32V003F4U6 RISC-V SoC IO Bank Assignment for Communication Interfaces 

![image](https://github.com/user-attachments/assets/beeaf265-9806-405d-95bb-bf4f95c18ca5)

---

### Pin Connections

| **VSDSquadron Mini** | **Raspberry Pi Pico** |
|-----------------------------|-----------------------------|
|          PD6 (RX)           |           GP4 (TX)          |
|          PD5 (TX)           |           GP5 (RX)          |
|          GND                |           GND               |

---

### Circuit diagram

![image](https://github.com/user-attachments/assets/42a39651-b385-4c73-aa5d-02b249423733)

---

### Circuit Connection 

The transmitter is the VSDSquadron Mini development board featuring the CH32V003F4U6 RISC-V microcontroller, while the receiver is a Raspberry Pi Pico based on the ARM Cortex-M0+ based microcontroller. The VSDSquadron Mini’s TX pin (PD5) is connected to the RP2040’s RX pin (GPIO 5), with a common ground connection between both boards. The VSDSquadron Mini is programmed using the onboard single-wire programmer via USB-C, with development done in C using an Arduino IDE. The Raspberry Pi Pico is programmed in MicroPython using the Thonny IDE, leveraging the machine library for UART communication and GPIO control. The VSDSquadron Mini transmits a constant HIGH signal on its TX pin, and the Raspberry Pi Pico monitors the RX pin, toggling an LED on GPIO 25 ON or OFF based on the signal state. 

---

### TRANSMITTER CODE - VSDSquadron Mini (Arduino IDE)

```c
#define TX PD5
#define TX PD6
void setup() {
  // Configure PD5 (Digital Pin 5) as an output pin
  pinMode(TX, OUTPUT);

  pinMode(RX INPUT);

  Serial.begin(9600);

 // Set PD5 to HIGH
  digitalWrite(TX, HIGH);
}

void loop() {
  // To keep PD5 HIGH forever
  while (1) {
    // Infinite loop 
  }
}
```

---

### RECEIVER CODE - Raspberry Pi Pico (Thonny)

```python
from machine import Pin, UART
import time

# Initialize the UART interface 
uart = UART(1, baudrate=9600, tx=Pin(4), rx=Pin(5))

# Initialize the LED on GPIO 25 
led = Pin(25, Pin.OUT)


tx_pin = Pin(4, Pin.IN)
rx_pin = Pin(5, Pin.IN)


while True:
    if rx_pin.value() == 1:  # Check if TX pin is high
       #print("tx_pin.value")
       led.value(1)  # Turn on LED
    else:
        #print("rx_pin.value")
        led.value(0)  # Turn off LED
       
    time.sleep(0.1)  
```

---
