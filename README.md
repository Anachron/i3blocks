# i3blocks
This has become an incredible big collection of blocks in use with i3wm. 
It can also be an inspiration of how to do stuff in bash.

## Maintained by the Community
I am not using i3 on my laptop anymore and thus I've started to transfer the maintainence to the Community.
You can apply for maintaining it [here](https://github.com/Anachron/i3blocks/issues/47).
I've tried merging it back with [i3blocks-contrib](https://github.com/vivien/i3blocks-contrib/issues/169) but there seems to be no interest.

## Requirements
- All scripts are written in bash. Every script should be optimized for performance.
- `font-awesome` is required to display special glyphs:
    - `apt install fonts-font-awesome` for Debian / Ubuntu

## WARNING:
Some scripts (like display) also change your computers behaving!
Please be very careful when you include those into your i3blocks.

## Screenshots
![audio bandwidth battery](scrots/audio_bandwidth_battery.png)
![bluetooth brightness countdown](scrots/bluetooth_brightness_countdown.png)
![cpu datetime display](scrots/cpu_datetime_display.png)
![feed firewall ip-address](scrots/feed_firewall_ip-address.png)
![keystate launcher load](scrots/keystate_launcher_load.png)
![locale mail memory](scrots/locale_mail_memory.png)
![microphone network packages](scrots/microphone_network_packages.png)
![playerctl process space](scrots/playerctl_process_space.png)
![ssid user temperature](scrots/ssid_user_temperature.png)
![usb trash scroll](scrots/usb_trash_scroll.png)
![vpn weather webcam](scrots/vpn_weather_webcam.png)
![window](scrots/window.png)
![keymap](scrots/keymap.png)

## Blocks

### Audio
Example config:
```
[audio]
label=
interval=5
```

### Bandwidth
Example config:
```
[bandwidth]
instance=wlp3s0;in
label=
interval=1

[bandwidth]
instance=wlp3s0;out
label=
interval=1
```

### Battery
Example config:
```
[battery]
label=
instance=0
interval=5
```

### Bluetooth
Example config:
```
[bluetooth]
label=
interval=10
```

### Brightness
Example config:
```
[brightness]
label=
interval=5
```

### Cmus
Example config:
```
[cmus]
command=~/.i3-blocks/blocks/scroll $BLOCK_NAME
label=
markup=pango
interval=repeat
```

### Countdown
Example config:
```
[countdown]
instance=tomorrow 05:00:00
label=
interval=1
```

### CPU
Example config:
```
[cpu]
label=
interval=2
```

### Datetime
Example config:
```
[datetime]
label=
interval=5
```

### Display
Example config:
```
[display]
label=
interval=5
```

### Feed
Example config:
```
[feed]
instance=http://goo.gl/bR2hcp
label=
interval=60
```

### Firewall
Example config:
```
[firewall]
label=
interval=10
```

### IP-Address
Example config:
```
[ip-address]
label=
interval=60
```

### Keymap
Example config:
```
[keymap]
label=
interval=10
```

### Keystate
Example config:
```
[keystate]
label=
instance=caps
interval=1

[keystate]
label=
instance=num
interval=1
```

### Launcher
Example config:
```
[launcher]
label=
interval=once
```

### Load
Example config:
```
[load]
label=
interval=10
```

### Locale
Example config:
```
[locale]
label=
interval=once
```

### Mail
Example config:
```
[mail]
label=
instance=~/.gmx-private
interval=60
```

### Memory
Example config:
```
[memory]
label=
instance=mem;free
interval=30

[memory]
label=
instance=swap;total
interval=30
```

### Microphone
Example config:
```
[microphone]
label=
interval=5
```

### Network
Example config:
```
[network]
label=
instance=enp4s0f2
interval=10

[network]
label=
instance=wlp3s0
interval=10
```

### Notifier
Example config:
```
[cmus]
command=~/.i3-blocks/blocks/notifier $BLOCK_NAME
label=
markup=pango
interval=repeat
```

### Packages
Example config:
```
[packages]
label=
interval=300
```

### Playerctl
Example config:
```
[playerctl]
label=
instance=rhythmbox
interval=5
```

### Process
Example config:
```
[process]
instance=http
label=
interval=10
```

### Scroll
Example config:
```
[cmus]
command=~/.i3-blocks/blocks/scroll $BLOCK_NAME
label=
markup=pango
interval=repeat
```

### Space
Example config:
```
[space]
label=
interval=30

[space]
label=
instance=/pub
interval=30
```

### SSID
Example config:
```
[ssid]
label=
interval=60
```

### Temperature
Example config:
```
[temperature]
instance=Core
label=
interval=5
```

### Trash
Example config:
```
[trash]
label=
interval=10
```

### USB
Example config:
```
[usb]
instance=PhotoSmart
label=
interval=10
```

### User
Example config:
```
[user]
label=
interval=once
```

### VPN
Example config:
```
[vpn]
label=
interval=5
```

### Weather
Example config:
```
[weather]
instance=2643743
interval=60
```

### Webcam
Example config:
```
[webcam]
label=
instance=/dev/video0
interval=5
```

### Window
Example config:
```
[window]
command=~/.i3-blocks/blocks/scroll $BLOCK_NAME
label=
markup=pango
interval=repeat
```

## Authors
Anachron ([https://github.com/Anachron](github profile))
