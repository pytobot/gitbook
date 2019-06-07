# SystemD

SystemD is a system and service manager for Linux. In order to run a command or program when the Pi boots, it can be added as a service. Once this is done, the comacoand can start/stop enable/disable from the linux prompt.

Show system status:

```text
systemctl status
```

Activates the service "example1" immediately:

```text
systemctl start example1
```

Deactivates the service "example1" immediately:

```text
# systemctl stop example1
```

Restarts the service "example1" immediately:

```text
 systemctl restart example1
```

Shows status of the service "example1":

```text
systemctl status example1
```

Enables "example1" to be started on bootup:

```text
systemctl enable example1
```

Disables "example1" to not start during bootup:

```text
systemctl disable example1
```

## Update SSID

The following code will create _ssid\_update.service_ file.

```text
sudo nano /etc/systemd/system/ssid_update.service
```

ssid\_update.service will _execute acc\_point\_update.sh_ file

{% code-tabs %}
{% code-tabs-item title="ssid\_update.service" %}
```bash
[Unit]
Description=Update SSID and PWD

[Service]
ExecStart=/bin/bash acc_point_update.sh
WorkingDirectory=/home/pi/pytobot/systemD
StandardOutput=inherit
StandardError=inherit
User=pi

[Install]
WantedBy=multi-user.target
```
{% endcode-tabs-item %}
{% endcode-tabs %}

To start and enable the the service the following code is used.

```text
sudo systemctl start ssid_update.service
sudo systemctl enable ssid_update.service
```

By executing the start command the following code wil run:

{% code-tabs %}
{% code-tabs-item title="acc\_point\_update.sh" %}
```bash
#!/bin/bash

SSID=pytobot:$(ifconfig wlan0 | grep -Eo ..\(\:..\){5} | tail -c 9) #update SSID 
echo $SSID

PASSWORD=$((10000000 + RANDOM % 9999999)) #update PASSWORD
echo $PASSWORD

sudo sed -i "s/SSIDNAME/$SSID/g" /etc/hostapd/hostapd.conf
sudo sed -i "s/PASSWORD/$PASSWORD/g" /etc/hostapd/hostapd.conf
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Screen

The following code will create _screen.service_ file.

```text
sudo nano /etc/systemd/system/screen.service
```

ssid\_update.service will _execute screen.service_ file **after network.target** is executed

{% code-tabs %}
{% code-tabs-item title="screen.service" %}
```bash
[Unit]
Description=print SSID and PASSWORD on OLED 
After=network.target

[Service]
ExecStart=/usr/bin/python3 -u screen.py
WorkingDirectory=/home/pi/pytobot/systemD/screen
StandardOutput=inherit
StandardError=inherit
#Restart=always
User=pi

[Install]
WantedBy=multi-user.target
```
{% endcode-tabs-item %}
{% endcode-tabs %}

To start and enable the the service the following code is used.

```text
sudo systemctl start screen.service
sudo systemctl enable screen.service
```

## Shutdown

The following code will create _screen.service_ file.

```text
sudo nano /etc/systemd/system/shutdown.service
```

The following script shuts down the Raspberry Pi when the shutdown button is used or the battery voltage is to low.

{% code-tabs %}
{% code-tabs-item title="shutdown.service" %}
```bash
[Unit]
Description=Shutdown Raspberry Pi on voltage or switch 

[Service]
ExecStart=/usr/bin/python3 -u shutdown.py
WorkingDirectory=/home/pi/pytobot/systemD
StandardOutput=inherit
StandardError=inherit
Restart=always
User=pi

[Install]
WantedBy=multi-user.target
```
{% endcode-tabs-item %}
{% endcode-tabs %}

To start and enable the the service the following code is used.

{% hint style="danger" %}
Only enable this service when the Raspberry Pi is inside the PCB. Or Pin 20 needs to have a manual High pin
{% endhint %}

{% hint style="warning" %}
```text
sudo systemctl start shutdown.service
sudo systemctl enable shutdown.service
```
{% endhint %}

By executing the start command the following code wil run:

```python
from subprocess import call
import RPi.GPIO as GPIO            # import RPi.GPIO module
GPIO.setmode(GPIO.BCM)
GPIO.setup(20, GPIO.IN)           # set GPIO20 as an input

while True:
    if not GPIO.input(20):
        print('SYSTEM SHUTDOWN')
        call("sudo shutdown -h now", shell=True)
```

## References

SystemD- Raspberry Pi\[[SOURCE](https://www.raspberrypi.org/documentation/linux/usage/systemd.md)\]

