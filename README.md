# pyledshop

**Upstream repo. Contains breaking features.**

Python module for interacting with LED Shop Compatible Wifi Controllers (e.g. SP108E)

Fork of the original project, located at https://github.com/kylezimmerman/pyledshop

## Installation

Using pip:
- macOS/Linux
  - ```python3 -m pip install pyledshop```
- Windows
  - ```pip3 install pyledshop```
    - On some systems, it is ```pip install pyledshop```.
- Source
  - ```https://pypi.org/project/pyledshop/```

## Contributing

- Fork the repository
- Clone the repository: `$ git clone https://github.com/your-name/pyledshop`
- Checkout new branch: `$ git checkout -b my-awesome-feature`
- Make your changes
- Run Black: `$ python3 -m pip install black`
  - `black .`
- Commit: `$ git add . && git commit -m "add my awesome feature"`
	- Push: `$ git push origin master`
- Open a new pull request.


 ## Usage

```py
from pyledshop import WifiLedShopLight, MonoEffect, CustomEffect

# The IP assigned to the device on your network
# I recommend setting a static IP to avoid the IP changing over time with DHCP
light_ip = "192.168.0.100" 

light = WifiLedShopLight(light_ip)

# Power controls
light.turn_off()
light.turn_on()
light.toggle()

# Color
light.set_color(255, 0, 0) # Red

# Effects
light.set_preset(MonoEffect.STATIC) # Enum for single color customizable effects
light.set_preset(0) # Rainbow - See <pyledshop>/effects.py for full list of values
light.set_custom(CustomEffect.CUSTOM_1) # Custom Effects upload via app

# Brightness
light.set_brightness(0) # Dimmest
light.set_brightness(255) # Brightest

# Speed
light.set_speed(0) # Slowest
light.set_speed(255) # Fastest

# Segments - Manual (Like the official app)
light.set_segments(3) # Sets the total number of segments
light.set_lights_per_segment(100) # Sets the total number of lights per segment

# Segments - Automatic (Calculate the lights per segment to fill a target number of lights)
light.set_calculated_segments(300, 1) # Equivalent to 1 segment, 300 lights per segment = 300 lights
light.set_calculated_segments(300, 4) # Equivalent to 4 segments, 75 lights per segment = 300 lights

# Sync state
light.sync_state() # Updates light.state with the latest state on the controller
```

## Features

This project is mostly a reverse engineering of the LED Shop protocol by capturing packets sent to the controller using the app.
Most of the features in the app are supported, but not everything.

### Supported
- [x] Turn On / Off
- [x] Set Color (rgb)
- [x] Set Brightness
- [x] Set Speed
- [x] Select Preset Effect
- [x] Select Custom Effect
- [x] Sync State
- [x] Change number of segments
- [x] Change length of segments

