# Local Hotspot

## Setup a local hotspot

{% embed url="https://www.raspberrypi.org/documentation/configuration/wireless/access-point.md" %}

In order to work as an access point, the Raspberry Pi will need to have access point software installed, along with DHCP server software to provide connecting devices with a network address. Ensure that your Raspberry Pi is using an up-to-date version of Raspbian \(dated 2017 or later\).

Install the required software \(dnsmasq and hostapd\) with this command:

```text
sudo apt update
sudo apt install dnsmasq hostapd
```

### Configuring a static IP

To configure the static IP address, open the dhcpcd configuration file with the following command:

```text
sudo nano /etc/dhcpcd.conf
```

Go to the end of the file and edit it so that it looks like the following:

```text
interface wlan0
    static ip_address=192.168.4.1/24
    nohook wpa_supplicant
```

Now restart the `dhcpcd` daemon:

```text
sudo systemctl restart dhcpcd
```

### Configuring the DHCP server \(dnsmasq\)

The DHCP service is provided by dnsmasq. By default, the configuration file contains a lot of information that is not needed, and it is easier to start from scratch. Rename this configuration file, and edit a new one:

```text
sudo mv /etc/dnsmasq.conf /etc/dnsmasq.conf.orig
```

```text
sudo nano /etc/dnsmasq.conf
```

Type or copy the following information into the dnsmasq configuration file and save it:

```text
interface=wlan0      # Use the require wireless interface - usually wlan0
dhcp-range=192.168.4.2,192.168.4.20,255.255.255.0,24h
```

Reload `dnsmasq` to use the updated configuration:

```text
sudo systemctl reload dnsmasq
```

### Configuring the access point host software \(hostapd\)

```text
sudo nano /etc/hostapd/hostapd.conf
```

add the following text into the file

```text
interface=wlan0
driver=nl80211
ssid=SSIDNAME
hw_mode=g
channel=7
wmm_enabled=0
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=PASSWD
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```

We now need to tell the system where to find this configuration file.

```text
sudo nano /etc/default/hostapd
```

Find the line with \#DAEMON\_CONF, and replace it with this:

```text
DAEMON_CONF="/etc/hostapd/hostapd.conf"
```

### Start it up

Now enable and start `hostapd`:

```text
sudo systemctl unmask hostapd
sudo systemctl enable hostapd
sudo systemctl start hostapd
```

#### Add routing and masquerade

Edit /etc/sysctl.conf

```text
sudo nano /etc/sysctl.conf
```

and uncomment this line:

```text
net.ipv4.ip_forward=1
```

Add a masquerade for outbound traffic on eth0:

```text
sudo iptables -t nat -A  POSTROUTING -o eth0 -j MASQUERADE
```

Save the iptables rule.

```text
sudo sh -c "iptables-save > /etc/iptables.ipv4.nat"
```

Edit /etc/rc.local and add this just above "exit 0" to install these rules on boot.

```text
sudo nano /etc/rc.local
```

Add the following line aboce Exit 0

```text
iptables-restore < /etc/iptables.ipv4.nat
```

Using a wireless device, search for networks. The network SSID you specified in the hostapd configuration should now be present, and it should be accessible with the specified password.

If SSH is enabled on the Raspberry Pi access point, it should be possible to connect to it from another Linux box \(or a system with SSH connectivity present\) as follows, assuming the `pi` account is present:

```text
ssh pi@192.168.4.1
```

By this point, the Raspberry Pi is acting as an access point, and other devices can associate with it. Associated devices can access the Raspberry Pi access point via its IP address for operations such as `rsync`, `scp`, or `ssh`.

## Update the SSID and Password

The following script updates the SSID name to the last 8 Digits of the Mac Addres.   
The PASSWD is updated to an random 8 Digit number. 

{% code-tabs %}
{% code-tabs-item title="acc\_point\_update.sh" %}
```bash
#!/bin/bash

SSID=pytobot:$(ifconfig eth0 | grep -Eo ..\(\:..\){5} | tail -c 9)
echo $SSID

PASSWD=$((10000000 + RANDOM % 9999999))
echo $PASSWD

sudo sed -i "s/SSIDNAME/$SSID/g" /etc/hostapd/hostapd.conf
sudo sed -i "s/PASSWD/$PASSWD/g" /etc/hostapd/hostapd.conf

sudo systemctl unmask hostapd
sudo systemctl enable hostapd
sudo systemctl start hostapd
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### ​Execute Script from startup

Go to your rc.local file

```text
sudo nano /etc/rc.local
```

add the folowing code above exit 0

```text
./home/pi/pytobot/acc_point_update
```

Print SSID and PASSWD

```text
sudo python3 pytobot/screen/screen.py 
```

{% hint style="warning" %}
TODO: At this moment the script wil search for SSIDNAME and PASSWD in the conf file. The first time on startup the SSIDNAME and PASSWD will be changed to the MACADDR and Random PASSWD, But after that its not possible to change it anymore. Thats not a problem as long the SD CARD Stays in the same controller with the Same MACADDR. 
{% endhint %}

