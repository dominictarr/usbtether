# usbtether

automatically connect a raspberry pi to a phone/tablet/etc
via usb tethering.

when installed as a systemd service, this will poll for the tether
at startup, but you do not need to login.

just plugin the the device, and enable USB tethering.

## signals

### short flash, every second

polling, but unable to find a usb tether.

### 2 short flashes

found USB Tether, starting dhcpcd.

### bunch of fash flashes

lost connection

### nothing

it's connected (hopefully)

## A small race condition.

because `dhcpcd` waits for the device to be ready if it's not there
(I can't see a way to disable this unhelpful feature)
then if the usb cable is unpluged at this time, it will just sit there
without doing anything helpful (such as flash a light)

pluging it back in should get it going again, though.
