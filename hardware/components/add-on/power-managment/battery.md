# Battery

## FENIX ARB-L18-3400 RECHARGEABLE 18650 BATTERY

The Fenix ARB-L18-3400 is a high capacity 18650 Li-ion rechargeable with a protection circuit in the anode to help prevent short circuits, over charge/discharge and over heating. The battery also includes pressure relief vents which expel waste gas in the rare case of an internal short circuit preventing an explosion.

![](../../../../.gitbook/assets/arb-l18-3400.jpg)

## **Integration in the project.**

To to use the the Motors an 6-12V input is required. For this project and max speed of the motors 2X 3.6V batteries are used what gives an 7.2V input voltage with 3400mAh. 

{% hint style="success" %}
On full power the robot batteries can last for approximately 45 minutes
{% endhint %}

## Battery Voltage

To be able to secure the components and the controller. A voltage detection is needed to shutdown the circuit when the batteries drop below the minimum. 

{% hint style="warning" %}
The Raspberry Pi computer does not have a way to read analog inputs. It's a digital-only computer.
{% endhint %}

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-La0d0m_n5WeIuwPKggN%2F-LdxtCp3PEfmMmehdjSJ%2F-LdyLT6i57B1-3AmUv0I%2F856-01.jpg?alt=media&token=b29ad416-0f57-4869-8cf6-3aa45b669a48)

###  <a id="adc"></a>

**​**[**https://github.com/aboudou/picheckvoltage**](https://github.com/aboudou/picheckvoltage)**​**  
  


* 
{% file src="../../../../.gitbook/assets/1048p \(1\).PDF" caption="SMT Polarized Holder" %}



