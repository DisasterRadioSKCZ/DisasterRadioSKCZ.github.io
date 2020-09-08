#  

# Welcome to Disaster Radio Slovakia and Czech Republic

![Cover image]({{ site.url }}/disaster-radio-bratislava.jpg)

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
/set sf 10
/set lorafrq 868
```

## How and what to flash

Right now we are running [compiled master branch](https://github.com/DisasterRadioSKCZ/disaster-radio/releases/tag/1.0-rc2-test-ttgo2) (will be rc2).

Replace /dev/tty.usb-serial-* with your USB device name (this is macOs naming):

```bash
unzip esp_flash.bin.zip
esptool.py -p /dev/tty.usbserial-* erase_flash
esptool.py -p /dev/tty.usbserial-* --baud 460800 write_flash 0x00000 esp_flash.bin
```
