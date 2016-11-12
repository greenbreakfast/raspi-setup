# Initial Setup of the Raspberry Pi


## Add Wifi Network

Change config file:
`sudo vi /etc/wpa_supplicant/wpa_supplicant.conf`

For each network, add:
```
network={
        ssid="mydesiredssid"
        psk="wifipassword"
        id_str="home"
}
```



## Changing Hostname

Change the name of the device

`sudo vi /etc/hosts`
Change line with `127.0.1.1` to desired hostname

`sudo vi /etc/hostname`
Change to desired hostname

Run `sudo /etc/init.d/hostname.sh`

Reboot to take effect



## Setup Zeroconf

Setup Zeroconf to give the Pi a local DNS name

```
sudo apt-get update
sudo apt-get install ahavi-daemon
sudo insserv avahi-daemon
```

Create config file: `sudo vi /etc/avahi/services/multiple.service`
Paste in:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
        <name replace-wildcards="yes">%h</name>
        <service>
                <type>_device-info._tcp</type>
                <port>0</port>
                <txt-record>model=RackMac</txt-record>
        </service>
        <service>
                <type>_ssh._tcp</type>
                <port>22</port>
        </service>
</service-group>
```

Apply new config: `sudo /etc/init.d/avahi-daemon restart`
