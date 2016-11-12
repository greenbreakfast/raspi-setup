# Using a USB Audio Adapter



## Setup USB Audio Adapter

Modify modprobe
```
sudo vi /lib/modprobe.d/aliases.conf
```

Comment out the following line:
```
options snd-usb-audio index=-2
```

## Test Playing Audio

Test playing a WAV file:
```
sudo aplay /usr/share/scratch/Media/Sounds/Vocals/Singer1.wav
```

Test playing an MP3 file:
```
sudo apt-get install mpg321
sudo mpg321 /usr/share/scratch/Media/Sounds/Animal/Cat.mp3
```
