# Setting Up Autostart

Setup Autostart utility to perform specific commands at boottime.


## Opening a Browser to a Webpage on Boot

Modify the following file:
```
/etc/xdg/lxsession/LXDE-pi/autostart
```

If that doesn't work, try modifying:
```
/root/pi/.config/lxsession/LXDE-pi/autostart
```

*User config files take precedence over system files*

With:
```
@lxpanel --profile LXDE-pi
@pcmanfm --desktop --profile LXDE-pi

# Disable the screensaver
#@xscreensaver -no-splash

# Setup powersaving to not turn the screen off or start screen saver
@xset s off
@xset -dpms
@xset s noblank

#@point-rpi

# Launch the browser in full screen
# clear out any errors from unclean exit
@sed -i 's/"exited_cleanly": false/"exited_cleanly": true/' ~/.config/chromium/Default/Preferences
@chromium-browser --noerrdialogs --kiosk <URL TO DISPLAY>
```
