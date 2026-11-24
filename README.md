# EXPERIMENT-02-INTERFACING-A-DIGITAL-INPUT-OUTPUT-TO-IOT-DEVELOPMENT-BOARD


**DATE:**

**NAME:*MANIKANDAN T*

**ROLL NO:*212224110037*

**DEPARTMENT:*B.E CSE(IOT)*

## Aim

To Interface a Digital Input (IR pair ) to ARM IOT development board and write a program to obtain the data

## Components required

- STM32 CUBE IDE
- ARM IOT development board
- STM programmer tool
- IR Pair Sensor

## Theory

The ARM (Advanced RISC Machine) architecture is widely used in microcontrollers and processors due to its efficiency, low power consumption, and high performance. ARM processors follow the Reduced Instruction Set Computing (RISC) design, making them ideal for embedded systems, mobile devices, and IoT applications. Many well-known semiconductor companies, including STMicroelectronics, use ARM-based architectures to develop powerful and energy-efficient microcontrollers.

One such microcontroller is the STM32WLE5JC, which is part of the STM32 family and is based on the ARM Cortex-M4 core. It is specifically designed for LoRaWAN® and other sub-GHz wireless communication applications, making it ideal for IoT and LPWAN (Low Power Wide Area Network) solutions. This microcontroller integrates a LoRa® transceiver, eliminating the need for an external radio module and reducing both cost and power consumption. With a maximum clock speed of 48 MHz, 256 KB of Flash memory, and 64 KB of RAM, it provides enough computing power for real-time data processing and wireless communication.

The STM32WLE5JC is known for its ultra-low power consumption, making it perfect for battery-operated IoT devices such as smart agriculture sensors, environmental monitoring systems, industrial automation, and asset tracking. It supports multiple communication interfaces, including I2C, SPI, and UART, allowing seamless integration with various sensors and peripherals. Additionally, it features built-in security capabilities such as AES 256-bit encryption and a True Random Number Generator (TRNG) for secure data transmission.

With its power-efficient design, built-in LoRaWAN support, and flexible communication options, the STM32WLE5JC is an excellent choice for developers looking to build long-range, low-power IoT applications. It is fully compatible with STM32CubeIDE and LoRaWAN middleware, making development and deployment easier for engineers and learners alike.

## IR PAIR

![image](https://github.com/user-attachments/assets/c0e0a1c8-b7be-4d10-9307-46432c31f26e)

IR technology is used in a wide range of wireless applications which includes remote controls and sensing. The infrared part in the electromagnetic spectrum can be separated into three main regions: near IR, mid-IR & far IR. The wavelengths of these three regions vary based on the application. For the near IR region, the wavelength ranges from 700 nm- 1400 nm, the wavelength of the mid-IR region ranges from 1400 nm – 3000 nm & finally for the far IR region, the wavelength ranges from 3000 nm – 1 mm.The near IR region is used on fiber optic & IR sensors, the mid-IR region is used for heat sensing and the far IR region is used in thermal imaging. The range of frequency for IR is maximum as compared to microwave and minimum than visible light.

## Procedure

1. Click on STM 32 CUBE IDE, the following screen will appear
   
<img width="1060" height="607" alt="image" src="https://github.com/user-attachments/assets/7c293d1b-edcb-401f-9492-17b0f19dc12b" />

2. Click on FILE, click on new stm 32 project

<img width="1055" height="612" alt="image" src="https://github.com/user-attachments/assets/8d385242-3d34-4e00-b476-d3457f851318" />

<img width="1055" height="650" alt="image" src="https://github.com/user-attachments/assets/4b3c6e34-f953-4323-a55d-10cd56aee8eb" />


3. Select the target to be programmed as shown below and click on next

<img width="1047" height="635" alt="image" src="https://github.com/user-attachments/assets/34115a47-2a50-4505-a2ff-244050504c2c" />


4. Select the program name

<img width="617" height="692" alt="image" src="https://github.com/user-attachments/assets/3a8b9011-8c0a-417c-8e38-7a62e8c297d5" />

5. Corresponding ioc file will be generated automatically

<img width="1067" height="642" alt="image" src="https://github.com/user-attachments/assets/aa4096c3-7edd-4cf2-be0b-851b57473a32" />



6. Select the appropriate pins as GPIO, in or out, USART or required options and configure
<img width="1060" height="612" alt="image" src="https://github.com/user-attachments/assets/84ce825d-06be-448f-9582-970afd8afc97" />
<img width="1057" height="637" alt="image" src="https://github.com/user-attachments/assets/7af81f08-2b34-44ce-b9d7-1e321197483e" />



7. Click on Ctrl+S, automatically C program will be generated

<img width="1051" height="637" alt="image" src="https://github.com/user-attachments/assets/9e7e439c-ee2f-4f7d-8b44-e5fcad8720f0" />


8. Edit the program and as per required 

<img width="1060" height="590" alt="image" src="https://github.com/user-attachments/assets/33fe8da5-4e87-4642-b85b-4cd923055636" />



9. Use project and build all 

<img width="1067" height="601" alt="image" src="https://github.com/user-attachments/assets/a3d4d795-69a8-40de-a4c8-9703f944451e" />

10. Once the project is bulild 

<img width="1027" height="462" alt="image" src="https://github.com/user-attachments/assets/3df34ded-1f59-4d11-9428-57d60ff05cb2" />


11. connect the iot board to power supply and usb

12. After connecting open the STM cube programmer

<img width="1067" height="622" alt="image" src="https://github.com/user-attachments/assets/2d7a45bd-e59c-4f5e-90eb-3ef785210ac9" />



13. Connect the STM board through the COM port, then upload the corresponding project ELF file/Hex file or Bin file in Erasing & Programming Window,while ensuring the board is in flash mode, and click on 'Start Program'.
   <img width="1021" height="592" alt="image" src="https://github.com/user-attachments/assets/8ce7b78d-a32c-4d75-a270-2aad241c8647" />

14.  After the file download is complete, switch your board to run mode and press the reset button to see the output


## STM 32 CUBE PROGRAM

```
// Your STM 32 CUBE Program code here
#include "main.h"
#include "stdbool.h"

bool IRSENSOR;

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
  HAL_Init();

  SystemClock_Config();

  MX_GPIO_Init();

  while (1)
  {
	  IRSENSOR = HAL_GPIO_ReadPin(GPIOB, GPIO_PIN_4);
	  if(IRSENSOR == 0)
	  {
		  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_SET);
		  HAL_Delay(2000);
		  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
		  HAL_Delay(2000);
	  }
	  else
	  {
		  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
		  HAL_Delay(2000);
	  }
  }
}

void SystemClock_Config(void)
{
  RCC_OscInitTypeDef RCC_OscInitStruct = {0};
  RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};

  __HAL_PWR_VOLTAGESCALING_CONFIG(PWR_REGULATOR_VOLTAGE_SCALE2);

  RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_MSI;
  RCC_OscInitStruct.MSIState = RCC_MSI_ON;
  RCC_OscInitStruct.MSICalibrationValue = RCC_MSICALIBRATION_DEFAULT;
  RCC_OscInitStruct.MSIClockRange = RCC_MSIRANGE_6;
  RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE;
  if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK)
  {
    Error_Handler();
  }

  RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK3|RCC_CLOCKTYPE_HCLK
                              |RCC_CLOCKTYPE_SYSCLK|RCC_CLOCKTYPE_PCLK1
                              |RCC_CLOCKTYPE_PCLK2;
  RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_MSI;
  RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
  RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1;
  RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV1;
  RCC_ClkInitStruct.AHBCLK3Divider = RCC_SYSCLK_DIV1;

  if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK)
  {
    Error_Handler();
  }
}

static void MX_GPIO_Init(void)
{
  GPIO_InitTypeDef GPIO_InitStruct = {0};

  __HAL_RCC_GPIOB_CLK_ENABLE();
  __HAL_RCC_GPIOA_CLK_ENABLE();

  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);

  GPIO_InitStruct.Pin = GPIO_PIN_4;
  GPIO_InitStruct.Mode = GPIO_MODE_INPUT;
  GPIO_InitStruct.Pull = GPIO_PULLUP;
  HAL_GPIO_Init(GPIOB, &GPIO_InitStruct);

  GPIO_InitStruct.Pin = GPIO_PIN_0;
  GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);
}

void Error_Handler(void)
{
  __disable_irq();
  while (1)
  {
  }
}

#ifdef  USE_FULL_ASSERT
void assert_failed(uint8_t *file, uint32_t line)
{
}
#endif// Your STM 32 CUBE Program code here
```

## OUTPUT
<img width="901" height="965" alt="image" src="https://github.com/user-attachments/assets/a461e998-c47e-434c-bfcf-81a8651351a8" />
<img width="907" height="976" alt="image" src="https://github.com/user-attachments/assets/a4a555ed-b15b-4dae-baf3-f171d2deb6c8" />

## Result

Interfacing a digital Input (ir pair) with ARM microcontroller based IOT development is executed and the results are verified.
