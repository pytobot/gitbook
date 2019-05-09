# Scripts

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



