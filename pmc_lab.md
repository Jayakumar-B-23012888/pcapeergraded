 Question 1.	Execute and analyse arithmetic  operations using the 8086 microprocessor emulator.

 Addition of 16 bit ALP
```c
MOV AX,1A52h

MOV BX,32B3h

ADD AX,BX
```
 Subtraction of 8 bit numbers ALP
```c
MOV AX,1a52h

SUB AX,32b3h

ret
```
 Multiplication alp
```c
MOV AX, 0X2A35H

MOV BX, 0X5F35H

MUL BX

RET
```
 Division alp
```c
MOV AX, 0X2A35H

MOV BX, 0X5F35H

DIV BX

RET
```

 2.	Execute and analyse logical operations using the 8086 microprocessor emulator.
 AND of 16 bit ALP

```c
MOV AX, 1A52h
MOV BX, 32B3h
AND AX,BX
ret      
```
 OR of 16 bit ALP 

```c
MOV AX, 1A52h
MOV BX, 32B3h
OR AX,BX
ret       
```
 NOT of 16 bit ALP 

```c
MOV AX, 1A52h
NOT AX
ret      
```
  XOR of 16 bit ALP
```c
MOV AX, 1A52h
MOV BX, 32B3h
XOR AX,BX
ret   
```

 3.	Execute and analyse arithmetic and logical operations using the 8086 microprocessor emulator.

 Addition of 16 bit ALP
```c
MOV AX,1A52h

MOV BX,32B3h

ADD AX,BX
```
 Subtraction of 8 bit numbers ALP
```c
MOV AX,1a52h

SUB AX,32b3h

ret
```
 Multiplication alp
```c
MOV AX, 0X2A35H

MOV BX, 0X5F35H

MUL BX

RET
```
 Division alp
```c
MOV AX, 0X2A35H

MOV BX, 0X5F35H

DIV BX

RET
```
 AND of 16 bit ALP

```c
MOV AX, 1A52h
MOV BX, 32B3h
AND AX,BX
ret      
```
 OR of 16 bit ALP 

```c
MOV AX, 1A52h
MOV BX, 32B3h
OR AX,BX
ret       
```
 NOT of 16 bit ALP 

```c
MOV AX, 1A52h
NOT AX
ret      
```
  XOR of 16 bit ALP
```c
MOV AX, 1A52h
MOV BX, 32B3h
XOR AX,BX
ret   
```


 4.	Interface a digital output for the ARM development board (simulation) and blink the led 5 times with a delay of 500 ms.--

```c
include "main.h"
include "stdbool.h"
bool button_status;
while (1)
{
    button_status = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_15);

    if (button_status == 0)
    {
        for (int i = 0; i < 5; i++)
        {
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_SET);   
            HAL_Delay(500);

            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_RESET); 
            HAL_Delay(500);
        }
    }
}

```

 5.	Generate an interrupt using a pushbutton, simulate the output using led toggling
```c
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
	if(GPIO_Pin==GPIO_PIN_0)
	{
		HAL_GPIO_TogglePin(GPIOC,GPIO_PIN_1);
	}
}
```

 6.	Generate a Square wave at the output pin using a timer and visualize it on the virtual oscilloscope and calculate the duty and frequency for the same.

```c
HAL_TIM_Base_Start(&htim2);
HAL_TIM_PWM_Init(&htim2);
HAL_TIM_PWM_Start(&htim2,TIM_CHANNEL_1);
```

7.	  Interface a digital input to the ARM development board and visualize the activation of the input using led.--

```c
while (1)
{
    button_status = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_13); 

    if (status == 0)   
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);   
    else
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET); 
}

```

8.Interface a digital input to the ARM development board and visualize the activation of the input using led blinking.--
```c
while (1)
{
    button_status = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_13);

    if (status == 0)   // Button active
    {
        HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5);
        HAL_Delay(500);    // Blink every 500 ms
    }
    else
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET); // LED OFF
    }
}

```

9.	Simulation of pushbutton and led interface with arm controller and blink upon activation of the pushbutton.--

```c
while (1)
  {
	  	 button_status = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_13);
	  	 if (button_status == 0) {
	  		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
	  		HAL_Delay(1000);
	  		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
	  		HAL_Delay(1000);
	  	 }
	  	 else {
	  		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
	  		HAL_Delay(1000);
	  	 }

  }
```

10.	 Interfacing a 16x2 LCD display with arm and display string “YOUR NAME”.--
```c
  Lcd_PortType ports[] = { GPIOA, GPIOA, GPIOA, GPIOA };
  Lcd_PinType pins[] = {GPIO_PIN_7, GPIO_PIN_6, GPIO_PIN_5, GPIO_PIN_4};
  Lcd_HandleTypeDef lcd;
  lcd = Lcd_create(ports, pins, GPIOB, GPIO_PIN_1, GPIOB, GPIO_PIN_0, LCD_4_BIT_MODE);
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "HARIHARAN J");
```

11.	Interfacing a 16x2 LCD display with arm and display string “YOUR ROLL NUMBER”.--
```c
  Lcd_PortType ports[] = { GPIOA, GPIOA, GPIOA, GPIOA };
  Lcd_PinType pins[] = {GPIO_PIN_7, GPIO_PIN_6, GPIO_PIN_5, GPIO_PIN_4};
  Lcd_HandleTypeDef lcd;
  lcd = Lcd_create(ports, pins, GPIOB, GPIO_PIN_1, GPIOB, GPIO_PIN_0, LCD_4_BIT_MODE);
  Lcd_cursor(&lcd, 0,1);
  Lcd_string(&lcd, "212223240047");
```

12.	Interface a 4x4 matrix keypad and display the output on LCD for keys 4,5,6.--
```c
void keypad() {

	Lcd_PortType ports[] = {GPIOA,GPIOA,GPIOA,GPIOA};
	Lcd_PinType pins[] = {GPIO_PIN_5,GPIO_PIN_4,GPIO_PIN_3,GPIO_PIN_2};
	Lcd_HandleTypeDef lcd;
	lcd = Lcd_create(ports,pins,GPIOA,GPIO_PIN_7,GPIOA,GPIO_PIN_6,LCD_4_BIT_MODE);

    HAL_GPIO_WritePin(GPIOC,GPIO_PIN_0,GPIO_PIN_SET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_1,GPIO_PIN_RESET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_2,GPIO_PIN_SET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_3,GPIO_PIN_SET);

	col1 = HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_4);
	col2 = HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_5);
	col3 = HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_6);

	Lcd_cursor(&lcd,0,0);
	if (!col1) {
		Lcd_string(&lcd, "Key pressed is 4");
		HAL_Delay(1000);
	}else if(!col2) {
		Lcd_string(&lcd, "Key pressed is 5");
		HAL_Delay(1000);
	}
	else if(!col3) {
		Lcd_string(&lcd, "key pressed is 6");
		HAL_Delay(1000);
	}
}
```

13.	Interface a 4x4 matrix keypad and display the output on LCD for keys 1,2,3.--
```c
void keypad() {
	Lcd_PortType ports[] = {GPIOA,GPIOA,GPIOA,GPIOA};
	Lcd_PinType pins[] = {GPIO_PIN_5,GPIO_PIN_4,GPIO_PIN_3,GPIO_PIN_2};
	Lcd_HandleTypeDef lcd;
	lcd = Lcd_create(ports,pins,GPIOA,GPIO_PIN_7,GPIOA,GPIO_PIN_6,LCD_4_BIT_MODE);
    
    HAL_GPIO_WritePin(GPIOC,GPIO_PIN_0,GPIO_PIN_SET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_1,GPIO_PIN_SET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_2,GPIO_PIN_RESET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_3,GPIO_PIN_SET);

	col1 = HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_4);
	col2 = HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_5);
	col3 = HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_6);
	col4 = HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_7);
	Lcd_cursor(&lcd,0,0);
	if (!col1) {
		Lcd_string(&lcd, "Key pressed is 1");
		HAL_Delay(1000);
	}else if(!col2) {
		Lcd_string(&lcd, "Key pressed is 2");
		HAL_Delay(1000);
	}else if(!col3) {
		Lcd_string(&lcd, "key pressed is 3");
		HAL_Delay(1000);
    }
}
```

14.	Interface a 4x4 matrix keypad and display the output on LCD for keys arithmetic operations.
```c
void keypad() {
	Lcd_PortType ports[] = {GPIOA,GPIOA,GPIOA,GPIOA};
	Lcd_PinType pins[] = {GPIO_PIN_5,GPIO_PIN_4,GPIO_PIN_3,GPIO_PIN_2};
	Lcd_HandleTypeDef lcd;
	lcd = Lcd_create(ports,pins,GPIOA,GPIO_PIN_7,GPIOA,GPIO_PIN_6,LCD_4_BIT_MODE);

HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_RESET); // Row A LOW
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_SET);   // Row B HIGH
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_SET);   // Row C HIGH
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_SET);   // Row D HIGH

if (!HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7)) {
    Lcd_string(&lcd, "Key: /");
    HAL_Delay(500);
}

HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_RESET); // Row B LOW
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_SET);

if (!HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7)) {
    Lcd_string(&lcd, "Key: *");
    HAL_Delay(500);
}

HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_RESET); // Row C LOW
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_SET);

if (!HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7)) {
    Lcd_string(&lcd, "Key: -");
    HAL_Delay(500);
}


HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_SET);
HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_RESET); // Row D LOW

if (!HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7)) {
    Lcd_string(&lcd, "Key: +");
    HAL_Delay(500);
}
}

```

15.	Interface an ARM hardware board with an Analog-to-Digital Converter (ADC) and display the converted digital output using the Serial Port Utility (SPU) software.
```c
#include "main.h"
#include "string.h"
#include <stdio.h>
uint16_t adcval;
char msg[20];
  while (1)
  {
	  HAL_ADC_Start(&hadc1);
	  HAL_ADC_PollForConversion(&hadc1, 20);
	  adcval=HAL_ADC_GetValue(&hadc1);
	  sprintf(msg, "ADC: %d\r\n", adcval);
	  HAL_UART_Transmit(&huart2,(uint8_t *)msg, strlen(msg),HAL_MAX_DELAY);
	  HAL_Delay(5000);
  }
```


