# SystemD

In order to have a command or program run when the Pi boots, you can add it as a service. Once this is done, you can start/stop enable/disable from the linux prompt.

## Update SSID

The following Script updates the PassWD and the SSID to MAC ADDR

{% code-tabs %}
{% code-tabs-item title="ssid\_change.sh" %}
```bash
#!/bin/bash

SSID=pytobot:$(ifconfig eth0 | grep -Eo ..\(\:..\){5} | tail -c 9)
echo $SSID

PASSWD=$((10000000 + RANDOM % 9999999))
echo $PASSWD

sudo sed -i "s/SSIDNAME/$SSID/g" /etc/hostapd/hostapd.conf
sudo sed -i "s/PASSWD/$PASSWD/g" /etc/hostapd/hostapd.conf

```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Running from booth

create a .service file for your service

```text
sudo nano /etc/systemd/system/ssid_update.service
```

add the follwing parameters

```bash
[Unit]
Description=Update SSID and PWD

[Service]
ExecStart=/bin/bash acc_point_update.sh
WorkingDirectory=/home/pi/pytobot
StandardOutput=inherit
StandardError=inherit
User=pi

[Install]
WantedBy=multi-user.target
```

Once this has been copied, you can attempt to start the service using the following command:

```text
sudo systemctl start ssid_update.service
```

Stop it using following command:

```text
sudo systemctl stop ssid_update.service
```

When you are happy that this starts and stops your app, you can have it start automatically on reboot by using this command:

```text
sudo systemctl enable ssid_update.service
```

## Screen

```text
[Unit]
Description=My service
After=network.target

[Service]
ExecStart=/usr/bin/python3 -u screen.py
WorkingDirectory=/home/pi/pytobot/screen
StandardOutput=inherit
StandardError=inherit
#Restart=always
User=pi

[Install]
WantedBy=multi-user.target


```

