# OLED

## Troubleshooting 

### Scrambled Screen

![Scrambled Screen](../../../.gitbook/assets/img_2994.jpg)

It's the pin for the RESET line. In transferring from library to my working code, I omitted to re-edit the definition of the reset pin. If it's not working, check that RST is wired to the correct pin, and that it is set for output. The reset is necessary for both the SPI and and I2C versions with the Adafruit library. \[[SOURCE](http://engineeringnotes.blogspot.com/2015/03/why-is-oled-display-scrambled-random.html)\]

#### Adding hardware reset pin

If you have a reset pin \(which may be required if your OLED does not have an auto-reset chip like the FeatherWing\) also pass in a reset pin like so:

```python
import digitalio
import board
 
reset_pin = digitalio.DigitalInOut(board.D4) # any pin!
oled = adafruit_ssd1306.SSD1306_I2C(128, 32, i2c, reset=reset_pin)
```

{% embed url="https://learn.adafruit.com/adafruit-oled-featherwing/circuitpython-and-python-usage" %}



### No I2C Device

{% hint style="danger" %}
ValueError: No I2C device at address: 3d
{% endhint %}

**`sudo i2cdetect -y 1`**

You should see the following, indicating that address **0x3d** \(the OLED display\) was found

![I2C address 3D](../../../.gitbook/assets/screenshot-2019-04-13-at-14.13.53.png)

{% code-tabs %}
{% code-tabs-item title="screen/screen.py" %}
```text
disp = adafruit_ssd1306.SSD1306_I2C(128, 64, i2c, addr=0x3d)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
Change the address: "**addr=0x3d**" to the addres what whas found in the _I2Cdetect_
{% endhint %}



