# 3d-printer
This is random content that I have assembled while using my 3d printer. It is a list of useful links, software, hardware and other stuff. Therefor it will change with time and as my usage of my 3d printer adapts.

## Current Setup
The current setup I use is a heavily modded ELEGOO Neptune 3 printer. Following is a list of all the hardware modifications I have performed:

### Fans
I switched the fan in the PSU for a Noctua one. Noctua doesn't make a 60mm fan, so I opted for a more standard 40mm fan. While this means the fan will not be as quite as a 60mm one would be, and provide less airflow, I have yet to notice any negative effects.  
Additionaly I also switched the main hot-end fand for a Noctua 40mm one.  
Both fans are regular computer fans and therefore require a 12v power supply. I accomplished this by using a 24v to 12v linear regulator purchased cheap on Amazon. So far it seems to do it's job just fine.

### Lights
The power supply of the Neptune 3 already has a 5.5mm by 2.5mm barell jack on the side. I had some 24v LED strips still lying which I mounted on the inside of the aluminum extrusion on the Z axis. The LED strip was small enough to fit snuggly inside the V slot and still not interfere with the rollers of the X gantry.

### Fan shroud
While switching the main hot-end fan I also printed a ned fan enclosure. I used [this design](https://www.printables.com/model/270983-elegoo-neptune-3-fan-duct) by Tal.

### "Direct" extruder
Because printing TPU on a bowden printer can be a real tough challenge I decided to mount the extruder directly above the hot-end. Luckily there already exists [this design](https://www.thingiverse.com/thing:5532317) by MaddatmyHat.

### BananaPi
Due to the ongoing shortage of RaspberryPis I used a BananaPI M2 Zero to run Octoprint on. As the serial connection was really flaky for me, I integrated the BananPi directly into the enclosure of the Neptune 3 and connected the GPIO UART port of the M2 Zero directly to the spare UART 2 port (label for use with an optional and not yet announces WiFi module) on the Neptune 3 main board. This also required a modified firmware. Luckily the official Firmware for the Neptune 3 is open sourced on GitHub. You can find my modifications in [this repository](https://github.com/Piets/Neptune_3). As the Octopi image does not natively support the BananaPi I resorted to using the Armbian build for it and install Octoprint manually.

### OctoPrint
As noted in the BananaPi section I run Octoprint. One of the plugins I have utilized is the PSU Control which enabled me to remotely turn the power to the printer on and off. This also ensures the power to the printer als automatically turned off after a print completed. I already use a few IKEA Tradfri outlets in my home, so I threw together a simple IKEA Tradfri plugin for the PSU Control plugin. You can find the repository [here](https://github.com/Piets/OctoPrint-PSUControl-Tradfri). But be warned that setup can be a bit of a pain due to the dependency on libcoap.

### Camera
To remotely monitor my 3d printer I mounted an old PlayStation 2 EyeToy camera to the side of the printer. It is supported natively by mjpedstreamer so works flawlessly with Octoprint.

### Klipper
One of the latest changes to my Neptune 3 was installing Klipper on the BananaPi and flashing the accompanying firmware. You can find my currently used configuration in the `printer.cfg` file in this repository. The configuration ans build instructions were taken from [this repository](https://github.com/bsas/Neptune-Elegoo3-Klipper).  
I have not yet mounted the ADXL345 sensors to the print bed and print head. As far as I currently understand it, the BananaPi has to independent SPI buses and therefore should support simultaneous operation of both sensors. I will update this information once I have confirmed this.