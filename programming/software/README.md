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

Copy paset "script" into the terminal and exit by using Ctrl-x and confirm. The following code will give the script the right permissions to execute and runs the code. 

```text
chmod +X script
sudo -Y ./script
```

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
git clone https://github.com/pytobot/pytobot.git

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

Escape19

git config --global user.email "sybrenmarechal@icloud.com"
git config --global user.name "sybren-marechal"
git config --global credential.helper store
git pull
```
{% endcode-tabs-item %}
{% endcode-tabs %}

