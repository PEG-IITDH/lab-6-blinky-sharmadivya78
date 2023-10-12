
# UART

* DIVYA SHARMA [ee23mt005@iitdh.ac.in] 
* SHWETA K TOTLA [200030053@iitdh.ac.in]
* Group: 02
* [11.10.2023]



### AIM:

Part 1:

To Program our microontroller to transmit:

"F0" if SW1 is pressed

"AA" if SW2 is pressed 

over UART with baud rate 9600 and odd parity. 

our program should also listen for incoming data on the UART with the same baud and parity config; if "AA" is received LED should be GREEN; if "F0" is recieved, the LED should be BLUE and if any error is detected LED should be RED. And we have to Test this by communicating with our neighboring group.



### UART IN ARM :

1.UART is a serial communication protocol.
2.UART is universal asynchronous receiver transmitter.
3.In ARM, UART is having 8 modules and each module is having its own input and output pin in the GPIO port.
4.In this program, we had used 4th module of UART and in that module the transmitter pin is PC5 and the receiver pin is PC4.
5.As the UART communication is asynchronous, we need to use the baud rate for the transmitter and receiver for the proper communication.


### PROCEDURE:

1.Make the PORTF configurations.
2.Make the PORTF interrupt configurations.
3.Make the UART and UART interrupt configurations.
4.Make the systick configurations.
5.Take the press of the switch as a GPIO interrupt.
6.If the GPIO interrupt occurs the program should go to the GPIO handler and the GPIO handler logic is 
       if the switch 1 is pressed transmit the data "FO".
       if the switch 2 is pressed transmit the data "AA".
7.If the signal is received on Rx pin of UART, then UART interrupt occurs and then code will go to UART interrupt handler and the UART interrupt handler logic is
       if AA is received green LED is ON.
       if FO is received blue LED is ON.
       if incomplete signal is received then red LED is ON.
8.If any of the LED is ON, then give a delay using systick counter. If the counter value is zero, then the code will go the systick handler and the logic inside systick handler is turn off          
  the LED and clear all the interrupts and the interrupt flag.
      



### BAUD RATE CALCULATION:
    
    Integer baud rate = uartsysclk/(clkdiv*baudrate)
    Fractional baud rate = (BRDF * 64 + 0.5)

    Integer baud rate = 16000000/(16*9600)
                      = 104.16666
    Fractional baud rate = (0.16666 * 64 + 0.5)
                         = 11.16666
                         = 11

   Thus IBRD=104
        FBRD=11 



### Measurements and Results for part 1:


when switch 1 is pressed, and F0 is received in receiver, the observed output is 
<img src="images_blue.jpg" alt="Blue LED" width="300"/>





when switch 2 is pressed, and AA is received in receiver, the observed output is 
![green](green.jpeg)





By giving disturbance to the jumper, the observed output is
![red](red.jpeg)








### Conclusions:

Thus a very good knowledge and exposure on UART is gained after doing this experiment.