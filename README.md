## telkam


### General description (purpose)

The **telkam** is an intellectual demon that turns your Chinese IP camera into a "gadget" or "detector" - a device that 
detects motion in the frame and transmits photos and short video clips to the messenger Telegram on alarm or request. 

It is important to note that this is not a streamer in the "classical sense", it does not transfer video stream to a 
server/client in a constant mode, as in conventional IP-cameras.

Supported hardware at the moment a two camera modules from XM (XiongMai), pinout fully corresponds:
- IVG-G3S Goke GK7205v210 SoC + Sony IMX307 sensor + 16 MB NOR flash, original firmware [000739AG](https://download.xm030.cn/d/MDAwMDE2NDU=)
- IVG-G41 Goke GK7205v210 SoC + SC5239S sensor + 16M MB NOR flash, original firmware [000659QA](https://download.xm030.cn/d/MDAwMDE2NTc=)


### Features

- Simplicity: all the functionality of the device is implemented out of the box, namely automatic day/night transition,
operation with two types of backlighting (infrared and visible spectrum), configuration through a simple (minimalistic)
and intuitive web interface (no need to use a terminal or command line).

- Improved motion detection algorithm (based on the analysis of the intersection of given lines by an object), instead
of the simple detection algorithm "light change" (changes in pixel brightness), which is a common implementation on
stock firmware.

- Video is transmitted to Telegram in short clips (~10s) only on demand or alarm, not in a continuous (constant) stream.
In this regard, the device can work on "expensive" and relatively "slow" mobile Internet, consuming Internet traffic
insignificantly. There is also no need for a dedicated server (cloud) to operate the device.

- Several users can connect to the detector in the Telegram at the same time.

- All video/photo information is stored in the device's RAM, so there is no need to connect an SD card and replace it
periodically due to "wear and tear".

- The “relay" and "alarm" outputs are organized, controlled from the telegram-bot, to which you can "hang actuators".

- There are two endpoints `http://<ip_address>/image` and `rtsp://root:<pass>@<ip_address>/stream=0`, to get snapshots
and video respectively.

- The program can be installed quite easily on the OpenIPC platform just a few commands
