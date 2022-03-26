# iMet-4_Hardware
Since no data could be found about this specific model, I decided to dig into it. 
Structure of this repository is based on [bazjo's work.](https://github.com/bazjo/RS41_Hardware/)


# Board pictures and structure
This sonde's structure is very similar to the RS-41's. 
![Main Board](pictures/main_board.jpg?raw=true "Main Board")



# Main component list
* U1: K30 - Unidentified.
* U2: [LTC3534 Buck-Boost DC/DC Converter](datasheets/ltc3534.pdf)
* U3: Not found on the board. Could be the [HYT-271 humidity module](datasheets/hyt-271.pdf)
* U4: [MEAS MS560702BA03 Barometric Pressure Sensor](datasheets/MS560702BA03.pdf)
* U5: [Ublox CAM-M8Q-0-10 Concurrent GNSS receiver](datasheets/CAM-M8-FW3.pdf)
* U6: [STM32F373C8T6 ARM Cortex-M4 32b MCU+FPU, 256KB Flash, 32KB SRAM](datasheets/stm32f373xxx)
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

# STM32 Wiring
Still WIP. I'm probing all the pins... 

1.
2.
3.
4.
5.
6.
11. PA1 		  ==> To temp probe 4
12. PA2/USART2_TX ==> to Ublox GPS via 220ohm
13. PA3/USART3_RX ==> to Ublox GPS via 220ohm
26. PB13 		  ==> to LED1 via 180ohm
27. PB14 		  ==> to LED2 via 180ohm
28. PB15 		  ==> to LED3 via 180ohm
29. PA8 		  ==> to LED4 via 180ohm
34. PA13/SWDIO	  ==> to edge card pin 8
37. PA14/SWCLK	  ==> to edge card pin 5

# Temp/Humidity flatflex pinout
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

# Temp/Humidity flat flex specs
Not much is known. From the iMet-4 datasheet, it seems that the glass bead thermistor's manufacturer is Shibaura. Model number could be PT3-51F-K14. 

For the humidity sensor, the datasheets mentions a capacitive polymer, manufacturer's IST. I found three models that fit that description, and the HYT-271 is the most likely. It uses an I2C bus.
