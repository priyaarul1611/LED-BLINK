
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
   <img width="940" height="500" alt="image" src="https://github.com/user-attachments/assets/f43c6e49-fc0d-4315-9831-a998591fd00c" />

2. Click **File → New STM32 Project**.
<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/f87f590b-eb19-4d4a-9b52-7e6145d03cdc" />

3. Select the **target microcontroller** or board and click **Next**.
   <img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/8adb905d-1e3c-4b61-89c4-a9b84477d9f4" />



4. Name the project.
  <img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/9268ad6f-f3b9-4db9-8ceb-01849d1e9437" />

5. The corresponding `.ioc` file will be generated automatically.
  <img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/8fc74f28-c78e-4e28-b043-62d0890b76f3" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  <img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/c535435b-3a8c-43b0-9127-d8d8d8cf815d" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/f7fb3446-cabd-44cb-a58c-50cee81c632e" />

8. Edit the generated main program as required.
    <img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/6ee24c9c-a78a-4cb5-91dc-ed50691487ff" />

9. Click **Project → Build All**.
    <img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/d9036a93-d97e-4342-8d3b-44c32c3afb5a" />

10. Link the **HEX file** using the post-build process.
    <img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/2dc3f89a-e279-4c74-bb99-c34612a02b5b" />

11. Click **Debug** and connect the **STM Nucleo Board**.
   
<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/09e9ff2f-f1e0-4ddf-b8d8-1b7ac1ddd7ac" />

13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
<img width="905" height="645" alt="image" src="https://github.com/user-attachments/assets/46a11d18-e3d2-45f5-bdfc-cea20d2174f6" />


CASE 2: LED OFF
<img width="889" height="626" alt="image" src="https://github.com/user-attachments/assets/01686da3-831e-4a7c-ab6c-18c62fd000c4" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
