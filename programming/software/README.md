# Software

## Image

In the major version of the Pytobot is an image included. The image comes loaded with the last features of the software.

The default features are:

* Battery security
* Startup with hotspot
* SSID and PASSWD printed on OLED
* Camera stream
* Basic tutorial to setup The API's 
* Driving the car

## Setup

When you would like to start from scratch. And go the whole procedure by yourself. This chapter will guide you through it. 

## Installing software

The following script includes all of the libraries that are needed in the software.  
When you like to run the whole script in one time, use following commands:

```text
touch scirpt
nano script
```

Copy paset "script" into the terminal and exit by using Ctrl-x and confirm. 

{% code-tabs %}
{% code-tabs-item title="script" %}
```bash
#pip3 install --upgrade pip

#Enable I2C
#Enable SPI

sudo apt update
sudo apt upgrade 

#install git
sudo apt install git

#install I2C tools
sudo apt install i2c-tools

#install pip
sudo apt install python3-pip

#install led drivers
sudo pip3 install adafruit-circuitpython-neopixel

#install motor drivers
sudo pip3 install gpiozero

#install flask
sudo pip3 install flask

#install camerea
sudo pip3 install picamera

#install OLED
sudo pip3 install adafruit-circuitpython-ssd1306
sudo apt install python3-pil

#install MCP3008
sudo pip3 install adafruit-circuitpython-mcp3xxx

#delte script
sudo rm script
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Download repo

```text
git clone https://github.com/pytobot/pytobot.git
```

## Enable interfaces

The following code will give the script the right permissions to execute and runs the code. 

```text
chmod +x script
yes | sudo ./script
rm script
```

```text
sudo raspi-config
```

Go to 5. \[interfacing options\] and enable:

* Camera
* SSH
* SPI
* I2C
* 
