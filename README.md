# Labyrinth PCB Board

A board made for Midburn projects (Labyrinth / Sangha).

This repo contains the Gerber file (defining the PCB circuitry), and the BOM/CPL (defining the placement for assembly)

![image](./labyrinth_pcb_v0.4_01.png)

# How to Order

## Main order - PCB

1. Go to [JLCPCB.com](https://jlcpcb.com/)
1. Create Account
1. Click Order Now in the top menu
1. Add Gerber file -> select the gerber zip
1. select the amount of boards you like (PCB Qty- 5/10/15 etc)
1. Most options should stay the same (2 layer board, 1 design, etc)
1. change the color if you like
1. Select PCB Assembly (assemble top side)
1. Click Next twice
1. Add BOM + CPL Files (CPL == "PickAndPlace")
1. Click Process BOM and CPL
1. Confirm BOM
1. Confirm placement
1. Product description - Category Other/Other, enter whatever ("leds board" etc)
1. Save to cart
1. Finalize order + shipping from cart
1. Make sure to select coupon on checkout (theres always something)

## Other components

## Esp32 Dev board

The Labyrinth board is designed to work with common [Esp32 30-pin development boards](https://www.aliexpress.com/item/32896618772.html?spm=a2g0o.order_list.order_list_main.17.81711802dsYyri)

Other boards will not work unless they're in the same form factor and have the same pinout.

## (Optional) Mic module

There are optional headers for an [IMNP441 mic module](https://www.aliexpress.com/item/4000045517597.html?spm).

## Connectors

You'll need to solder connectors for your leds to work. Generally JST-SM connectors are used (the 3-pin variant for the most popular WS2812 strips).
You can find these on AliExpress

## PCB Power switch

The LEDs power switch used is not available in economic PCB assembly (which is much cheaper)
So I batch order them from LCSC.

You can order them here https://www.lcsc.com/product-detail/Slide-Switches_XKB-Connectivity-SS-12M11G5_C2879839.html

Or you can solder where the big switch would be instead, and the LEDs will always be on if the PCB is connected to power.

## Capacitor

Optionally, you can add a 1000uF electrolytic capacitor to the board to smooth out the power supply a bit.

# Setup

## Installing WLED

(Tested on Windows)

1. Connect the Esp32 to your PC via USB
1. Go to [install.wled.me](http://install.wled.me)
1. Select a WLED version to install (if you want to use a microphone, make sure to pick a "Sound Reactive" version)
1. Press install
1. Select the relevant port (might say CH340 or CP2102 depending on the esp32's USB chip)
1. Hold the BOOT button on your Esp32 board
1. start the installation while holding the boot button
1. if it doesn't work, try again and hold the BOOT button somewhat earlier, or try releasing it a few secs after installation attempt starts.
1. Enter your WiFi credentials if you like

## Configure pins

Once WLED is working - connect to it (via APP or web interface), and go to settings to configure these pins:

### Led pins:

1. GPIO 13
1. GPIO 14
1. GPIO 27
1. GPIO 26

### Microphone pins

Set the mic mode to Digital (I2S), with these pins:

- SCK: GPIO 16
- SD: GPIO 4
- WS: GPIO 15
