# Local Share

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

## References

Local share- Nico de Witte\[[SOURCE](https://www.raspberrypi.org/documentation/configuration/wireless/access-point.md)\]
