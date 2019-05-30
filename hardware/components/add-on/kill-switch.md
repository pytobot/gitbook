# Kill switch

## Kill Switch

The raspberry Pi needs a proper shutdown before the power goes of, otherwhise your SD card can be curropted. To shutdown the Raspberry Pi the command `sudo shutdown now` must be executed.

{% hint style="danger" %}
If the raspberry Pi isnt shutdown propperly you can corrupt the SD card!
{% endhint %}

## Circuit

#### When SWITCH =&gt; ON

The 5V from the DC reguator will go through D1 and will power the Gate of Q1.  
While putting Q1 High C1 will start charging. And BCM\_20 of the Raspberry Pi will go up.

![](../../../.gitbook/assets/screenshot-2019-05-30-at-20.33.13.png)

#### When SWITCH =&gt; OFF 

The remaining Votage before D1 will drain through R1 to the ground.   
So BCM\_20 will become LOW. And the following code will run.

```python
 if not GPIO.input(20):
        print('SYSTEM SHUTDOWN')
        call("sudo shutdown -h now", shell=True)
```

C1 will Load off his voltage to the Raspberry Pi, so that the Raspberry Pi has enough time to execute the command and shut down propperly 

### RC Time Constant 

![](../../../.gitbook/assets/rc1.gif)

{% hint style="info" %}
Time constant is a measurement of the time needed to charge or discharge a capacitor by ~63.2% of the differenece between the old value and new value after an impulse that induces a change has been applied.
{% endhint %}

$$
t(ms) = R(π) * C(uF) = 10 000* 3300 =  33000
$$

$$
T(s)=33 seconds
$$

## IRFZ44N

  
The IRFZ44N is an _n-channel_ enhancement mode power MOSFET manufactured by International Rectifier Corporation, in a TO-220 package. It has a continuous drain current of 49 A at 25 °C, and 35 A at 100 °C, making it an ideal component for switched mode power supplies, and general switching applications. This MOSFET has an operating temperature of 175 °C and therefore a heatsink is vital.

![](../../../.gitbook/assets/irfz44n_circuit.gif)





