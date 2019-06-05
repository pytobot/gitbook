# Voltage regulation

## R-78B05

The R-78Bxx-2.0 series is a high efficiency switching regulator. The efficiency of up to 96% means that very little energy is wasted as heat. Full power is available over a temperature range of -40°C up to 70°C without the need for heatsinks with their additional space and mounting costs.

{% hint style="success" %}
The R-78Bxx-1.0 series high efficiency switching regulators are ideally suited to replace 78xx linear regulators and are pin compatible.
{% endhint %}

![](../../../../.gitbook/assets/r-78b-2.0_spl-2.jpg)

## Usage

The input voltage of the batteries\(7.2V\) is used to power the H-bridge and the Motors.  
To use the controller and sensors, a 5V input is needed. So a step down to 5V is necessary.

{% hint style="warning" %}
The Ampere use of the LED's is variable from a lot of diffrent factors. Because the variation is so high, a seperature 2A sercuit is needed. 
{% endhint %}

## Trouble shooting

### AN7805

At first the **AN7805 DC DC step down** was used to have an 5V regulator that has the possebilty to regulate until 1A. But the efficiency was much lower and there was a lot energy going into heat. So a heat sink is needed to use the AN7805.   



![AN7805CV](../../../../.gitbook/assets/to-220.jpg)

{% hint style="info" %}
The big diffrence between AN7805 and the R-78B05 is the big price diffrence and the efficiency 
{% endhint %}

## Datasheet

{% file src="../../../../.gitbook/assets/r-78bxx-2.0-1093437-2.pdf" %}

