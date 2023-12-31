# Welcome to Disaster Radio Slovakia and Czech Republic

![Cover image](disaster-radio-bratislava.jpg?a)

## Our settings

We haved moved to RNode/Reticulum/Nomadnet/Sideband.

First install required software (sideband only if you want GUI):

```bash
pip install rns nomadnet sbapp
```

or macOS:

```bash
pip install rns nomadnet sbapp[macos]
```

Then flash:

```bash
rnodeconf --autoinstall
```

Answer the questions and node the device name of your device (should start with /dev/).

Then run either nomadnet or sideband. Quit. This creates default configuration files.

Edit ~/.reticulum/config and add this towards the end (I kept the 'Default Interface' part for context). Of course add your own device port in the 'port =' section:

```
  [[Default Interface]]
    type = AutoInterface
    ## enabled = No means we only want LoRA, so we know it's working
    enabled = No


[[RNode LoRa Interface]]
  type = RNodeInterface

  interface_enabled = True
  # Your port device here
  port = /dev/cu.usbserial-

  # Set frequency to 867.2 MHz
  frequency = 867200000
  bandwidth = 250000
  txpower = 17
  # Important: We are using spreadingfactor 10
  spreadingfactor = 10
  codingrate = 6
  flow_control = False
```

## Who to write when testing

You can write using nomadnet to:

 - j: 3008c42f9db940091f14a48c3d1cbf6f

## On propagation and routing

There are two ways messages are routed. First is routing when the other node is online. You can enable this
mode in .reticulum/config by setting enable_transport=True. I think this is almost always a good idea.

Another operation is propagation. This means sending a message to a propagation node, which will deliver it
when the destination will become online. You can trigger the sync to a propagation node from the sidekick menu.
If you want to run a propagation node, you need to run nomadnet with .nomadnet/config's enable_node = yes. Then
when sending a message, click the network icon in sideband and change direct delivery to propagation node (there
is also a "qr code" option, which is paper QR code, which is a real delivery mode too!

## Useful links

 - [RNode](https://unsigned.io/rnode/)
 - [Sideband](https://unsigned.io/website/sideband/)
 - [Official How-to](https://unsigned.io/private-messaging-over-lora/)
 - [Included utility programs](https://reticulum.network/manual/using.html#included-utility-programs)

## Obsolete

 - [Disaster Radio](https://github.com/sudomesh/disaster-radio) - the implementation we currently use
 - [Meshtastic](https://www.meshtastic.org/) - an alternative to Disaster Radio
 - [LoraCaster](https://github.com/valerio-vaccaro/LoraCaster) - low-level implementation of Lora with examples on how to broadcast BTC transactions
 - [ArmaChat](https://hackaday.io/project/171790-armawatch-armachat-long-range-radio-messengers) - another broadcaster solution - with a keyboard!

### Our connectivity

[View the map of Bratislava](https://disasterradio.o-matic.sk/app/dr#/nodes_map) - this is out of date, need to be edited collectively or replaced (in progress)

