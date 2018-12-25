---
layout: post
title: "AXE masternode deployment"
image: images/axerunner.gif
categories:
  - software
tags:
  - axe
  - mastermnode
  - vps
---
# AXE masternode deployment

{% raw %}<img src="/images/axerunner-v0127.png" alt="axerunner screenshot">{% endraw %}

# Binary deployment

_If you are running a masternode you need to be fairly familiar with network administration and securing your host. - Evan Duffield._

To deploy AXE masternode on VPS you need to create private key in your local wallet that would be a control wallet for your masternode park. Open AXE Core and enter the following in the `Debug Console`:

```
masternode genkey
```

This is your private key that you will place into the `axe.conf` on your masternode.

Now generate new address `mn1` and send 1000 AXE collateral.

```
getaccountaddress mn1
```

Grab output with

```
masternode outputs
```

Open Masternode configuration file and replace the example with your node's IP, private key and tx output from previous command.

#### Prepare
Now login on your VPS with and create new user if its a fresh VPS instance (root login).

```
adduser axerunner
usermod -aG sudo axerunner
su axerunner
cd ~
```

Tune security:

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

Install dependencies:

```
sudo apt-get install python virtualenv git unzip pv
```

#### Download
```
cd ~ && git clone https://github.com/axerunners/axerunner
```

#### Install
```
axerunner/axerunner install
```

##### Post
Follow the instructions in `axerunner` - install sentinel with `axerunner/axerunner install sentinel` and insert masternode private key in the `axe.conf`.
