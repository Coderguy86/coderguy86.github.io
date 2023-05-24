---
title: How to install nvidia driver to ubuntu server 22.04
date: 2023-04-17 20:51 -500
categories: [nvidia, homelab, ubuntu]
tags: [proxmox, nvidia, ubuntu]
---




Update and upgrade your distro

```shell
sudo apt update &  sudo apt upgrade
```

## Install Prerequisites. The following prerequisites are required to compile and install Nvidia driver

```shell
sudo apt install build-essential libglvnd-dev pkg-config
```
## Disable Nouveau Nvidia driver

First step is to Blacklist Nvidia nouveau driver. Open up terminal and enter the following commands

```shell
 sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
 sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
```

Confirm the content of the newly created modeprobe file blacklist-nvidia-nouveau.conf

```shell
cat /etc/modprobe.d/blacklist-nvidia-nouveau.conf
```

## Enter the following Linux command to update kernel initramfs

```shell
sudo update-initramfs -u
```

## Reboot

```shell
sudo reboot
```

## Download the Official Nvidia Driver and fix permessions 

```shell
 wget https://http.download.nvidia.com/XFree86/Linux-x86_64/530.41.03/NVIDIA-Linux-x86_64-530.41.03.run
```
```shell
chmod +x NVIDIA-Linux-x86_64-530.41.03.run
```

## Now run on sudo.

```shell
sudo su
```

```shell
./NVIDIA-Linux-x86_64-530.41.03.run
```
