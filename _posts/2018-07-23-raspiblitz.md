---
layout: post
title: "BTC Lightning Node on Raspberry Pi"
image: images/rpi-mbp.gif
categories:
  - hardware
tags:
  - rpi
  - btc
  - node
---
# RaspiBlitz

{% raw %}<img src="/images/rpi-mbp.jpg" alt="rpi-mbp-8bit">{% endraw %}

RaspiBlitz (by @rootzoll) is the fastest and cheapest way to get your own Lightning Node running on a RaspberryPi with a nice LCD.

## Hardware list (US):

* [Raspberry Pi 3](http://a.co/ahl7RIp)
* [Micro SD-Card 16GB](http://a.co/6R49HZz)
* [Card Reader](http://a.co/6e03D7Z)
* [Power](http://a.co/ciFRcYg)
* [Hard Drive 1TB](http://a.co/eUgVfLd)
* [Case](http://a.co/1774Hwl)
* [LCD Display](http://a.co/65p2wu6)

Follow [this](https://github.com/rootzoll/raspiblitz/blob/master/README.md#prepare-your-hardware) guide and spin up your node. After initial setup on the testnet (v0.4) you might want to go live. Enter `sudo nano /home/bitcoin/.bitcoin/bitcoin.conf` and comment out `testnet=1`. Then switch lightning service to `mainnet` with `sudo nano /mnt/hdd/lnd/lnd.conf` and reboot your node with `sudo reboot`. Use `lncli create` to finish mainnet setup.

[RaspiBlitz on GitHub](https://github.com/rootzoll/raspiblitz).
