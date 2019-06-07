# setup

download the image from github

Burn the image to the SD card with etcher

follow the soldering instruction.

turn the robot on and read the ip addres from the device. 

## installing software

```text
git clone https://github.com/pytobot/pytobot.git

#pip3 install --upgrade pip

sudo apt update
sudo apt upgrade 

#install git
sudo apt install git

#install I2C tools
sudo apt install i2c-tools

#install pip
sudo apt install python3-pip
#sudo apt install python-pip

#install led drivers
sudo pip3 install adafruit-circuitpython-neopixel

#install motor drivers
sudo pip3 install gpiozero

#install dependecies
sudo pip3 install flask

#install camerea
sudo pip3 install picamera

#install OLED
sudo pip3 install adafruit-circuitpython-ssd1306
sudo apt-get install python3-pil

Escape19

git config --global user.email "sybrenmarechal@icloud.com"
git config --global user.name "sybren-marechal"
git config --global credential.helper store
git pull
```

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
ssid=NameOfNetwork
hw_mode=g
channel=7
wmm_enabled=0
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=AardvarkBadgerHedgehog
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
sudo nanot /etc/sysctl.conf
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
sudo iptables-restore < /etc/iptables.ipv4.nat
```

Using a wireless device, search for networks. The network SSID you specified in the hostapd configuration should now be present, and it should be accessible with the specified password.

If SSH is enabled on the Raspberry Pi access point, it should be possible to connect to it from another Linux box \(or a system with SSH connectivity present\) as follows, assuming the `pi` account is present:

```text
ssh pi@192.168.4.1
```

By this point, the Raspberry Pi is acting as an access point, and other devices can associate with it. Associated devices can access the Raspberry Pi access point via its IP address for operations such as `rsync`, `scp`, or `ssh`.

## Setting up a Share

> Source Gitbook [Developing apps for the RPi from Nico de witte](https://vives.gitbook.io/iot-devices/developing-apps-for-the-rpi/05_developing_apps_for_rpi#setting-up-a-share)

To share network folders to a Windows computer we need to install some special software on the Raspberry Pi. The software providing the secret sauce this time is called _Samba_. The Samba software package implements the SMB protocol and provides support for the Windows naming service \(WINS\) and for joining a Windows Workgroup.

Installing the software using the commands below:

```text
sudo apt update
sudo apt install samba samba-common-bin
```

After installation configure the software by opening the file `/etc/samba/smb.conf` using nano.

```text
sudo nano /etc/samba/smb.conf
```

Read through the file and make sure you have the following parameters set:

```text
workgroup = WORKGROUP
wins support = yes
```

You can use anything as your workgroup name as long as it is alphanumerical and matches the workgroup you would like to join. The default workgroup in Windows 7, 8 and 10 is WORKGROUP.

### Setup a folder to share

With the folder created we can now tell the Samba software to share it on the network. Open the file `/etc/samba/smb.conf` using nano.

```text
sudo nano /etc/samba/smb.conf
```

Scroll to the bottom and add the following:

```text
# Sharing our Pytobot directory
[Pytobot]
 comment=Pytobot Share
 path=/home/pi/pytobot
 browseable=Yes
 writeable=Yes
 only guest=no
 public=no
 create mask=0664
 directory mask=0775
```

Notice how we tell Samba that public access is not allowed via `public=no` – this means that anyone wanting to access the shared folder must login with a valid user.

In this case the valid user is the user called `pi`. To set the Samba access password for the `pi` user, execute the `smbpasswd` command.

```text
sudo smbpasswd -a pi
```

**Restart the Samba service** using `sudo service smbd restart`.

## Control

Raspberry Pi try connect to network with SSID = ... PASS= ...

If Raspberry Pi cant connect to the network it will setup as an AP. \`  




[https://learn.sparkfun.com/tutorials/setting-up-a-raspberry-pi-3-as-an-access-point/all](https://learn.sparkfun.com/tutorials/setting-up-a-raspberry-pi-3-as-an-access-point/all)

