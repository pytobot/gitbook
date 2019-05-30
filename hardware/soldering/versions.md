# Versions

## Version 0.1

The first prototype is made on a breadboard. In the first protype is the main functionality to power the devices. The input power is 7.2V because later in the project the power source will change from an Voltage Regulator to 2X 3.6V battery's. This input power is used to power the H-bridge that controls the motors. 

The DC-DC converter is used to convert the battery input to 5V to power on the raspberry Pi.

{% hint style="danger" %}
While using the Breadbord there was an 0.2 voltage drop throug the circuit. Breadboards are good for testing. But if you want a stady desing. Soldering is the solution. 
{% endhint %}

![Pytobot print V0.1](../../.gitbook/assets/img_5078-2-copy.jpg)

## Version 0.2

The second version of the print was made to get rid of the voltage drop throug the circuit and have a more stady design. Screw terminals where added  to have a more easy connection with the hardware. Because the DC-DC converter cant take more than 1A and the LED's take more than 1A. 2 extra DC-DC converters where added for 2 extra LED strips. Also an diod is added to the circuit to secuire the devices if the battery's would not placed correctly and pot power on the ground. The condensator was added to have a more stady circuit for the raspberry pi

![](../../.gitbook/assets/img_3614-copy.jpg)

## Version 0.3

Controlling H-Bridge, Motors, LED's Line Sensor's Distance Sensor, Oled, GDoF

![](../../.gitbook/assets/img_3612-copy.jpg)

## Version 0.4

Controlling H-Bridge, Motors, LED's Line Sensor's Distance Sensor, Oled, GDoF,  
On/Off Switch. 

![](../../.gitbook/assets/img_3615-copy.jpg)

## Version 0.5 PCB 

Controlling H-Bridge, Motors, LED's Line Sensor's Distance Sensor, Oled, GDoF,  
On/Off Switch.  

![](../../.gitbook/assets/a713f79a-dcf2-4669-ae03-5ea1c64fb7e3_1_0_1.png)

## Version 1.0 PCB

![](../../.gitbook/assets/0a3b964b-c420-445c-a626-979100233cd0_1_0_1.png)

### Improvements

While Testing the first 1.0 PCB some minor and major eassues came up. 

1. Make use of smaller via's
2. Make the screw hole's from the Raspberry Pi zero to 2.5mm.
3. Change distance sensor on pin RX
4. Lower the electronics so the camera cable can fit in the raspberry Pi
5. Change the motor circuit to the raspberry Pi circuit. do not need Q3 anymore
6. IC1 higher because the fet comes out of the pcb
7. Change some io's to have less via's.
8. Change the value of the restores
9. Add positve and negative side at the capacitor sign
10. Change the value of the capacitors
11. change the 2 pin screw connectors to the right size

