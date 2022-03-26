# iMet-4 Hardware
Since no data could be found about this specific model, I decided to dig into it. 
Structure of this repository is based on [bazjo's work.](https://github.com/bazjo/RS41_Hardware/)


# Board pictures and structure
This sonde's structure is very similar to the RS-41's. 
![Main Board](pictures/main_board.jpg?raw=true "Main Board")
Seems to use 2mm FR4, but I'll measure it once I get my hands on calipers. 



# Main component list
* U1: K30 - Unidentified.
* U2: [LTC3534 Buck-Boost DC/DC Converter](datasheets/ltc3534.pdf)
* U3: Not found on the board. Could be the [HYT-271 humidity module](datasheets/hyt-271.pdf)
* U4: [MEAS MS560702BA03 Barometric Pressure Sensor](datasheets/MS560702BA03.pdf)
* U5: [Ublox CAM-M8Q-0-10 Concurrent GNSS receiver](datasheets/CAM-M8-FW3.pdf)
* U6: [STM32F373C8T6 ARM Cortex-M4 32b MCU+FPU, 64KB Flash, 32KB SRAM](datasheets/stm32f373xxx)
* U7: [RFPA0133 3 to 5V Programmable Gain Power Amplifier](datasheets/rfpa0133.pdf)
* U8: [CC115L Value Line Transmitter](datasheets/cc115L.pdf)
* Y1: 16MHz oscillator
* Y2: 26MHz oscillator
* Q3: [MMBT2222A](datasheets/mmbt2222a.pdf) (switches humidity sensor heating)

# Edge connector pinout

 ```
                ┌───┐
                │4 5│
Component side │3 6│
                │2 7│
                │1 8│
                └───┘
				
 ```
1. PWRON (to switching circuitry)
2. RX (via R24/220ohm to STM32 PA10)
3. TX (via R25/220ohm to STM32 PA9)
4. GND
5. SWCLK (to STM32 PA14)
6. VCC (+3.3V)
7. VBATT
8. SWDIO (to STM32 PA13)

# STM32 Pin Assignment
Still WIP. I'm probing all the pins... 

1.
2.
3.
4.
5.
6.
11. PA1 		  ==> to temp probe 4
12. PA2/USART2_TX ==> to Ublox GPS RXD via 220ohm
13. PA3/USART2_RX ==> to Ublox GPS TXD via 220ohm
26. PB14 		  ==> to LED1 via 180ohm
27. PB15 		  ==> to LED2 via 180ohm
28. PD8 		  ==> to LED3 via 180ohm
29. PA8 		  ==> to LED4 via 180ohm
34. PA13/SWDIO	  ==> to edge card pin 8
37. PA14/SWCLK	  ==> to edge card pin 5


# Temp/Humidity Flatflex specs.
Not much is known. From the iMet-4 datasheet, it seems that the glass bead thermistor's manufacturer is Shibaura. Might be the RB1 series. 
For the humidity sensor, the datasheets mentions a capacitive polymer, manufacturer's IST. I found three models that fit that description, and the HYT-271 is the most likely. It uses an I2C bus.
There seems to be a 100ohm resistor underneath the humidity sensor, probably to keep it above the dew point. 

Following pinout numbering follows the main board's connector.

1. GND
2. GND
3. Heater 1 ==> to VCC
4. NTC 1 ==> to STM32 PA1
5. HYT-271 SDA
6. GND
7. HYT-271 VCC ==> to VCC
8. HYT-271 SCL
9. NTC 2
10. Heater 2 ==> to Q3
11. GND
12. GND

# Software
At this time, I'm don't have access an ST-Link interface, I still don't know whether there's a lockout bit or not. 
As for building custom firmwares, a good start would be the [STM32 Arduino Core](https://github.com/stm32duino/Arduino_Core_STM32). This variant is supported, but it must be added to the boards.txt list. 