# Line sensor

## Line sensor

Line sensors are included to have more interaction with the robot, while using the line sensors. The robot can serve as an line following robot. This can expent the usability of the robot, and learn how to use multiple sensors in combination wich each other

{% hint style="info" %}
ADD PICTURE
{% endhint %}

3 Line sensors are included in the robot. 2 sensors to detect of the robot goes left or right from the line, and 1 sensor to detect if the robot is still on a line. 

## Code

the following code is an simple example that prints out the value of the sensor.

```python
from gpiozero import  LineSensor
from time import sleep

left_sensor = LineSensor(10)
middle_sensor = LineSensor(17)
right_sensor= LineSensor(27)

while True:
	left_detect  = int(left_sensor.value)
	middle_detect  = int(middle_sensor.value)
	right_detect = int(right_sensor.value)
	print(left_detect, middle_sensor, right_detect)
```

## Datasheet

{% file src="../../.gitbook/assets/qre1113.pdf" %}



