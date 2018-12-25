---
layout: post
title: "AXE operator's guide"
image: images/axerunner.gif
categories:
  - software
tags:
  - axe
  - masternode
  - vps
---
# AXE masternode deployment

{% raw %}<img src="/images/axerunner-v0127.png" alt="axerunner-screenshot">{% endraw %}

> If you are running a masternode you need to be fairly familiar with network administration and securing your host. - Evan Duffield

Successful masternode deployment would require GNU/Linux server (Ubuntu 18.04) with 2GB of RAM and static IPv4 address ([Vultr](https://www.vultr.com/?ref=7231821)).  

To deploy AXE masternode you need to create a private key in your local wallet that would be the **control** wallet for your masternode park. Download [AXE binary](https://github.com/AXErunners/axe/releases/latest), install the wallet and let it sync with the network. When the wallet is ready - open the `Debug Console` and enter the following:

```
masternode genkey
```

This is your masternode private key that you will place into the `axe.conf` on your masternode.

Now generate new address `mn1` and send 1000 AXE collateral.

```
getaccountaddress mn1
```

Grab output with

```
masternode outputs
```

Open Masternode configuration file and replace the example with your node's IP, private key and tx output from previous command.

## Prepare
Now login on your VPS with and create new user if it's a fresh VPS instance (root login).

```
adduser axerunner
usermod -aG sudo axerunner
su axerunner
cd ~
```

### Tune security:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install ufw fail2ban
sudo ufw allow ssh/tcp
sudo ufw limit ssh/tcp
sudo ufw allow 9937/tcp
sudo ufw allow 9337/tcp
sudo ufw logging on
sudo ufw disable
sudo ufw enable
```

### Install dependencies:

```
sudo apt-get install python virtualenv git unzip pv
```

## Download
```
cd ~ && git clone https://github.com/axerunners/axerunner
```

## Install AXE core
```
axerunner/axerunner install
```

## Post
Follow the instructions in `axerunner` - install Sentinel with `axerunner/axerunner install sentinel` and insert masternode private key in the `axe.conf`. Then load the configuration with `axerunner/axerunner restart now` and start the masternode from your **control** wallet.
