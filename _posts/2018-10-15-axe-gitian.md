---
layout: post
title: "Gitian builds for AXE"
image: images/axe-gitian.gif
categories:
  - software
tags:
  - axe
  - gitian
  - macos
---
# AXE-GITIAN

This guide covers deterministic build process for [AXE](https://github.com/AXErunners/axe) binaries on macOS. [axe-gitian](https://github.com/AXErunners/axe-gitian) is a Vagrant box, provisioned with Ansible and deployed in VirtualBox environment. Gitian affords a way to be assured that AXE binaries are built from the exact source, provided on GitHub.

### Prepare
#### Vagrant
Download and install the latest version of Vagrant from their <a href="https://www.vagrantup.com/downloads.html">website</a>.

#### VirtualBoX
Download and install the latest version of VirtualBox from their <a href="https://www.virtualbox.org/wiki/Downloads">website</a>.

#### Ansible
Install prerequisites
```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew doctor
brew install git
sudo easy_install pip
```
Setup Ansible

`sudo pip install ansible`

### Build
```
git clone https://github.com/AXErunners/axe-gitian
cd axe-gitian
```
Edit your <code>gitian.yml</code> file:
```
# URL of repository containing AXE source code.
axe_git_repo_url: 'https://github.com/AXErunners/axe'

# Specific tag or branch you want to build.
axe_version: 'master'

# The name@ in the e-mail address of your GPG key, alternatively a key ID.
gpg_key_name: 'F16219F4C23F91112E9C734A8DFCBF8E5A4D8019'

# OPTIONAL set to import your SSH key into the VM. Example: id_rsa, id_ed25519. Assumed to reside in ~/.ssh
ssh_key_name: ''
```
Start the build with <code>vagrant up --provision axe-build</code>. When environment is ready - connect with <code>vagrant ssh axe-build</code> and download <a href="https://github.com/AXErunners/axe/blob/master/doc/README_osx.md">Apple SDK</a> into <code>gitian-builder/inputs</code> (<code>wget</code> + dropbox).

Then prepare container and start the build with:
```
#replace $SIGNER and $VERSION to match your gitian.yml
./gitian-build.py --setup $signer $version
./gitian-build.py -B $SIGNER $VERSION
```
### Transfer files

Use `vagrant scp` [plugin](https://github.com/AXErunners/axe-gitian#copying-files).
