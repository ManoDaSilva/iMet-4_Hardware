# iMet-4_Hardware
Since no data could be found about this specific model, I decided to dig into it. 
Structure of this repository is based on [bazjo's work.](https://github.com/bazjo/RS41_Hardware/)


# Board pictures and structure
This sonde's structure is very similar to the RS-41's. 
![Main Board](pictures/main_board.jpg?raw=true "Main Board")



# Main component list
* U1: K30 - Unidentified.
* U2: [LTC3534 Buck-Boost DC/DC Converter](datasheets/ltc3534.pdf)
* U3: Not found yet.
* U4: [MEAS MS560702BA03](datasheets/MS560702BA03.pdf)
* U5: [Ublox CAM-M8Q-0-10](datasheets/CAM-M8-FW3.pdf)
* U6: [STM32F373C8T6](datasheets/stm32f373xxx)
* U7: [RFPA0133](datasheets/rfpa0133.pdf)
* U8: [CC115L](datasheets/cc115L.pdf)
* Y1: 16MHz oscillator
* Y2: 26MHz oscillator

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
12. PA2/USART2_TX ==> to Ublox GPS via 220ohm
13. PA3/USART3_RX ==> to Ublox GPS via 220ohm
26. PB13 		  ==> to LED1 via 180ohm
27. PB14 		  ==> to LED2 via 180ohm
28. PB15 		  ==> to LED3 via 180ohm
29. PA8 		  ==> to LED4 via 180ohm
34. PA13/SWDIO	  ==> to edge card pin 8
37. PA14/SWCLK	  ==> to edge card pin 5
