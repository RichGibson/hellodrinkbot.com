---
title: "Assembly and Operation Instructions (Maker Faire 2019)"
date: 2019-05-19
tags: ["hardware", "assembly", "instructions"]
summary: "Step-by-step assembly and operation instructions for Hello Drinkbot as of Maker Faire 2019."
---

*Please — if you have a better way to do anything, let me know. I made it up as I went along.*

## Assembly

### Parts

The bot starts with laser-cut parts and a few other components. All parts (except wire and the laser-cut frame) are listed in the [Bill of Materials on Amazon](https://www.amazon.com/hz/wishlist/ls/1FNW8R9Y1KKDV?ref_=wl_share).

### Electronics

**Raspberry Pi** is a tiny single-board computer which runs Linux and supports a graphical user interface.

**The AdaFruit DC & Stepper Motor HAT** connects to the Pi and allows you to control four (or with a trick, eight) peristaltic pumps. Up to 32 of these boards can be stacked, so you could control 256 pumps — well beyond the scope of a hello world project!

The motor hat requires a small amount of soldering on the terminal blocks used to attach pump wires to the board, and to attach the headers that connect the HAT to the Pi.

### Pumps

There are many ways to move and dispense liquids in a cocktail robot. Hello Drinkbot uses peristaltic pumps. The Adafruit motor controller hat can control two stepper motors, or control forward and reverse on four DC motors. Since we don't normally need forward and reverse, we can control eight peristaltic pumps with a single HAT.

To double the pump capacity: connect one side of your first motor to the first of the M1 pins and the other side to ground; connect your second motor to the second pin of M1 and ground.

### Case

The default case is a basic box with:
- Openings cut for four peristaltic pumps
- Mounting holes for a Raspberry Pi
- Holes for a monitor cable, 12V power cable, and USB cable

This needs to be placed on a shelf or other support, or mounted to something to have it above the supply bottles. Several case designs are available in the [GitHub repository](https://github.com/RichGibson/hellodrinkbot).

## Operation

Once the insides are complete:

1. Make sure the SD card is inserted
2. Connect 5V 2.5A Micro USB power to the Pi
3. Connect 12V power to the 12V pigtail
4. Attach the dispenser, connect hoses, and run them into the dispenser
5. Your kit has holes on the front panel for two screws and captive nuts to hold the front in place. You can also glue the back, sides, and top of the case. You probably don't want to glue the front because you'll want access to the Pi.

### Connecting

Associate with the **HelloDrinkbot** WiFi access point, then go to `hellodrinkbot.local` in your browser, or `10.0.0.1`.

You can also connect the Pi to your computer or hub via Ethernet cable. If you have a Mac, enable internet sharing (System Preferences → Internet Sharing). Your Pi will probably get address `192.168.2.2`.

The Pi is set up with mDNS, so you can connect as `hellodrinkbot.local`. The hostname is set in `/etc/hostname`.

### Making Drinks

You can make drinks by calling the RESTful interface:

```
http://hellodrinkbot.local/ws/drink/12?booze14=75&booze11=75
```

### Testing Pumps

The repository has utility programs demonstrating how to talk to the motor control hat from Python:

```bash
cd hellodrinkbot/software/utility
# Test all pumps, turning each on for 2 seconds
python ./pumptest.py 2
```

### Logs

You can look at the logs by SSH-ing into the Pi over any interface (`10.0.0.1`, `192.168.2.2`, or `hellodrinkbot.local`):

```bash
tail -f /var/log/nginx/bartendro-error.log
tail -f /var/log/nginx/bartendro-combined.log
tail -f /var/log/nginx/access.log
tail -f /var/log/nginx/error.log
tail -f /var/log/syslog
```

Click on the Bartendro logo in the upper right corner of the screen to access admin mode.
