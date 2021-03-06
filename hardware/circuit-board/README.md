# Circuit board

## Circuit board

A **printed circuit board** \(**PCB**\) mechanically supports all of the electronic components.  

## Version 0.1

The first prototype is made on a **breadboard**. In the first prototype is the main functionality to power the devices. The input power is 7.2V because later in the project the power source will change from a Voltage Regulator to 2X 3.6V batteries. This input power is used to power the H-bridge that controls the motors.

The DC-DC converter is used to regulate the battery input to 5V to power on the Raspberry Pi.

{% hint style="danger" %}
While using the Breadboard there was an **0.2 voltage drop** through the circuit. Breadboards are good for testing, but if you want a steady design, soldering is the solution.
{% endhint %}

![Pytobot print V0.1](../../.gitbook/assets/img_5078-2-copy.jpg)

## Version 0.2

The **second version** of the print was **soldered** to get rid of the voltage drop through the circuit and have a more steady design. Screw terminals were added to have an easier connection with the hardware. Because the DC-DC regulator can't take more than 1A and the LED's take more than 1A. 2 extra DC-DC regulators were added for 2 extra LED strips. Also a diode is added to the circuit to add Polarity Protection to secure the devices. The capacitor was added to have a more steady circuit for the Raspberry Pi.

> Version 0.2 is the first design that was used with battery power to have the first tests of the motors and remote control

![](../../.gitbook/assets/img_3614-copy.jpg)

## Version 0.3

In the 3th design, **heat sinks** were added. Because the voltage regulation creates a lot of heat and couldn't handle the heat for a long time. Also new screw terminals were added to control the H-Bridge, Motors, LED's, Line Sensor's, Distance Sensor, Oled & 9DoF.

On the print, all connections from the Raspberry Pi were connected by extra jumpers. The reason fo this is to have a possibility to quickly change IO Pins and test different situations.

![](../../.gitbook/assets/img_3612-copy.jpg)

## Version 0.4

After Version 0.3 the **power** on/off **switch** was added to be able to **shut down** the Raspberry Pi in a safe way. In version 0.4 tests were done to see how to handle the heat without using heat sinks, because heat sinks take a lot of extra space.

![](../../.gitbook/assets/img_3615-copy.jpg)

## Version 1.0 PCB

After testing the first 5 designs the **PCB** came into place. The design of this PCB was made to fit in the robot and has all functionalities to test all of the sensors and to fit all of the screw terminals on the print, smaller screw terminal was used with a with of 3.5mm. Also the Raspberry Pi is integrated into the print.

![](../../.gitbook/assets/0a3b964b-c420-445c-a626-979100233cd0_1_0_1.png)

### Improvements

While Testing the first 1.0 PCB, some minor and major issues came up.

1. Make use of smaller via's.
2. Make the screw holes from the Raspberry Pi zero to 2.5mm.
3. Change distance sensor on pin RX.
4. Lower the electronics, so the camera cable can fit in the Raspberry Pi.
5. Change the motor circuit to the Raspberry Pi circuit. Do not need Q3 anymore.
6. IC1 higher because the FET comes out of the PCB.
7. Change some IO's to have less via's.
8. Change the value of the resistors.
9. Add a positive and negative side of the capacitor sign.
10. Change the value of the capacitors.
11. Change the 2 pin screw connectors to the right size.
12. Change the diode to smaller one.
13. Add names for the wires.



## Version 2.0 PCB

![](../../.gitbook/assets/8eed0183-0295-4a34-a908-02e2056b03bf_1_0_1.png)

