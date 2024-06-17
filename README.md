## telkam

Telkam - a demon that turns a camera into a smart security detector


### General description (purpose)

The “telkam” is an original firmware that turns your Chinese IP camera into a "gadget" or "detector" - a device that 
detects motion in the frame and transmits photos and short video clips to the messenger Telegram on alarm or request. 
It is important to note that this is not a streamer in the "classical sense", it does not transfer video stream to a 
server/client in a constant mode, as in conventional IP-cameras.

Supported hardware at the moment - camera module from XM (Xiongmai) IVG-G3S:
GK7205v210(v200) + Sony IMX307, 16 MB flash, original firmware [000739AG](https://download.xm030.cn/d/MDAwMDE2NDU=).


### Features

- simplicity: all the functionality of the device is implemented out of the box, namely automatic day/night transition,
operation with two types of backlighting (infrared and visible spectrum), configuration through a simple (minimalistic)
and intuitive web interface (no need to use a terminal or command line).

- improved motion detection algorithm (based on the analysis of the intersection of given lines by an object), instead
of the simple detection algorithm "light change" (changes in pixel brightness), which is a common implementation on
stock firmware.

- video is transmitted to Telegram in short clips (~10s) only on demand or alarm, not in a continuous (constant) stream.
In this regard, the device can work on "expensive" and relatively "slow" mobile Internet, consuming Internet traffic
insignificantly. There is also no need for a dedicated server (cloud) to operate the device.

- several users can connect to the detector in the Telegram at the same time.

- all video/photo information is stored in the device's RAM, so there is no need to connect an SD card and replace it
periodically due to "wear and tear".

- “relay" and "alarm" outputs are organized, controlled from the telegram-bot, to which you can "hang actuators".

- there are two endpoints `http://<ip_address>/image` and `rtsp://root:<pass>@<ip_address>/stream=0`, to get snapshots
and video respectively.

- the program can be installed quite easily on the OpenIPC platform (Buildroot), without using any libraries and
components directly from OpenIPC (like "divinus", "majestic", "mini", "venc", etc.).

- In case of installation on stock/factory firmware, it is possible to revert back to Chinese firmware (regular IP
camera) in a few clicks. When installing on OpenIPC, reverting back to factory firmware is possible only if the crypto
partition from XM is saved.
