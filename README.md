# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/eab6b238-646c-41f4-87c2-023641b2ae28" />


2. Click **File → New STM32 Project**.
<img width="880" height="908" alt="image" src="https://github.com/user-attachments/assets/a5799efb-57e1-42b8-ba46-b09f32d86fcb" />
<img width="880" height="908" alt="image" src="https://github.com/user-attachments/assets/edf33429-8eea-4857-a991-c2d7706fc787" />

3. Select the **target microcontroller** or board and click **Next**.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/ee55287e-735d-4626-9a19-9cc6fe8ca112" />

4. Name the project.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/f83dfbef-426e-48ec-b978-85af0a532195" />

5. The corresponding `.ioc` file will be generated automatically.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/7b209cb3-f3ec-4718-9a18-97f6f9517157" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/49653a2e-39ef-42a7-971e-a7d4f18879d7" />
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/0e00dd1e-3dbf-4ce8-87b2-0d82db8ce2e6" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/2faa1dce-36fa-4608-a63b-002edb7523a8" />
 
8. Edit the generated main program as required.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/92ab02c6-2d25-4bf4-891c-2bef9d986b96" />
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/e0bc9ba4-1757-4ed7-aa38-fbb357795b9f" />

9. Click **Project → Build All**.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/cf92f54e-4954-44db-aea7-71f1e95d29f4" />

10. Link the **HEX file** using the post-build process.
<img width="673" height="294" alt="image" src="https://github.com/user-attachments/assets/5afe6a28-89d7-49ac-b063-76ef5d2b88de" />

11. Click **Debug** and connect the **STM Nucleo Board**.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/8af0be24-eca0-441d-a763-39eb4f48fb5f" />


12. Click **Run** to execute the program.
    
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
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

<img width="640" height="708" alt="image" src="https://github.com/user-attachments/assets/e48b8a56-79f0-4514-82eb-feaa4385060d" />

CASE 2: LED OFF

<img width="640" height="649" alt="image" src="https://github.com/user-attachments/assets/13c0b7d4-b5f8-465a-8894-11aa1fad22d5" />


---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




