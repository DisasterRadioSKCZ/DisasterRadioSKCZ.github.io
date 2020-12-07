#  

# Welcome to Disaster Radio Slovakia and Czech Republic

![Cover image](disaster-radio-bratislava.jpg?a)

## Our connectivity

[View the map of Bratislava](https://umap.openstreetmap.fr/en/map/disaster-radio-sk-cz_495988)

## Our settings

Connect to the device. If you have pio configured, then run

```bash
pio device monitor
```

If not, connect to the device (disaster.radio .... network) and

```bash
telnet 192.168.4.1
```

In the console, configure frequencies and spreading factor:

```bash
/set sf 12
/set lorafrq 868
/set interval 300000
```

## How and what to flash

Right now we are running [compiled master branch](https://github.com/DisasterRadioSKCZ/disaster-radio/releases/tag/1.0-rc.1.eu-new) (will be rc2). Build for TTGO2

Replace /dev/tty.usb-serial-* with your USB device name (this is macOs naming):

```bash
unzip esp_flash.bin.zip
esptool.py -p /dev/tty.usbserial-* erase_flash
esptool.py -p /dev/tty.usbserial-* --baud 460800 write_flash 0x00000 esp_flash.bin
```

## Useful links

 - [Disaster Radio](https://github.com/sudomesh/disaster-radio) - the implementation we currently use
 - [Meshtastic](https://www.meshtastic.org/) - an alternative to Disaster Radio
 - [LoraCaster](https://github.com/valerio-vaccaro/LoraCaster) - low-level implementation of Lora with examples on how to broadcast BTC transactions
 - [ArmaChat](https://hackaday.io/project/171790-armawatch-armachat-long-range-radio-messengers) - another broadcaster solution - with a keyboard!
