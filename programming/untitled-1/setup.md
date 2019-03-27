# setup

download the image from github

Burn the image to the SD card with etcher

follow the soldering instruction.

turn the robot on and read the ip addres from the device. 

## installing software

```text
git clone https://github.com/pytobot/pytobot.git

sudo apt update
sudo apt upgrade 

#install git
sudo apt install git

#install pip
sudo apt install python3-pip
#sudo apt install python-pip

#install led drivers
sudo pip3 install adafruit-circuitpython-neopixel

#install motor drivers
sudo pip3 install gpiozero

#install dependecies
sudo pip3 install flask






Escape19







```

## setup a share

{% embed url="https://vives.gitbook.io/iot-devices/developing-apps-for-the-rpi/05\_developing\_apps\_for\_rpi\#setting-up-a-share" %}



## Pinout

| Raspberry |  |
| :--- | :--- |
| 17 | H-bridge IN1 |
| 22 | H-bridge IN2 |
| 23 | H-bridge IN3 |
| 24 | H-bridge IN4 |
| 18 | LED Control |
| 21 | step motor |

## Control

Raspberry Pi try connect to network with SSID = ... PASS= ...

If raspberry pi cant connect to the network it will setup as an AP. \`  




[https://learn.sparkfun.com/tutorials/setting-up-a-raspberry-pi-3-as-an-access-point/all](https://learn.sparkfun.com/tutorials/setting-up-a-raspberry-pi-3-as-an-access-point/all)

