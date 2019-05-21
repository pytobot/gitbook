# setup

download the image from github

Burn the image to the SD card with etcher

follow the soldering instruction.

turn the robot on and read the ip addres from the device.

## installing software

```text
#pip3 install --upgrade pip

sudo apt update
sudo apt upgrade 

#install git
sudo apt install git
git clone https://github.com/pytobot/pytobot.git

#install I2C tools
sudo apt install i2c-tools

#install pip
sudo apt install python3-pip
#sudo apt install python-pip

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

Escape19

git config --global user.email "sybrenmarechal@icloud.com"
git config --global user.name "sybren-marechal"
git config --global credential.helper store
git pull
```

