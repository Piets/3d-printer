# Armbian
* Clean Setup
* Configure netplan for ethernet and wifi with the same static IP and different route metrics  
See `zz-static-ip.yaml` for more details, the file needs to live inside `/etc/netplan`
* Install Docker
* Install UART2 overlay and double spi overlay:  
The file `double-spi.dts` contains a custom overlay for Armbian for the Banana PI M2 Zero to enable both SPI buses. Copy to `/boot/overlay-user` and run `sudo armbian-add-overlay double-spi.dts` to enable.

# Docker
* Upload Files
* Build Image
* Flash Image