# LED-Strip

## Digital RGBW Led Strip

Pytobot has 120 Led's included in the hardware. The Led's give an more visuble image what is happening behind the hardware of the car. 

![](../../.gitbook/assets/giphy-2.gif)

## Calculation

| Emitting color | Wavelength\(nm\) | Luminous intensity\(mcd\) | Current\(mA\) | Voltage\(V\) |
| :--- | :--- | :--- | :--- | :--- |
| Red | 620-630 | 550-700 | 20 | 1.8-2.2 |
| Green | 515-530 | 1100-1400 | 20 | 3.0-3.2 |
| Blue | 465-475 | 200-400 | 20 | 3.2-3.4 |

{% hint style="info" %}
The max rating is assuming all the LEDs are on full white, usually the actual current for colorful design is about 1/3 to 1/2 the max current.
{% endhint %}

$$
24*(20+20+20)=1440mA
$$

$$
1440mA/2=720mA
$$

## Code

```python
import board
import neopixel

pixel_pin = board.D18
num_pixels = 10
ORDER = neopixel.RGB

pixels = neopixel.NeoPixel(pixel_pin, num_pixels, brightness=0.2, auto_write=True,
                           pixel_order=ORDER)
while True:
   pixels.fill((255, 255, 255)) ##White
   time.sleep(1)
```

## Datasheets



