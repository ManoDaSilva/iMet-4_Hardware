# iMet-4_Hardware
Since no data could be found about this specific model, I decided to dig into it. 
Structure of this repository is based on [bazjo's work.](https://github.com/bazjo/RS41_Hardware/)


# Board pictures and structure
This sonde's structure is very similar to the RS-41's. 



# Main component list
* U1: K30 - Unidentified.
* U2: [LTC3534 Buck-Boost DC/DC Converter] (datasheet/ltc3534.pdf)
* U3: Not found yet.
* U4: [MEAS MS560702BA03] (datasheet/MS560702BA03.pdf)
* U5: [Ublox CAM-M8Q-0-10] (datasheet/CAM-M8-FW3.pdf)
* U6: [STM32F373C8T6] (datasheet/stm32f373xxx)
* U7: [RFPA0133] (datasheet/rfpa0133.pdf)
* U8: [CC115L] (datasheet/cc115L.pdf)
* Y1: 16MHz oscillator
* Y2: 26MHz oscillator

# Edge connector pinout
                ┌───┐
                │4 5│
Component side  │3 6│
                │2 7│
                │1 8│
                └───┘
1.
2.
3.
4. GND
5.
6. VCC (+3.3V)
7.
8.
