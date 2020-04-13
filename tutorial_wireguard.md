---
author: Justin Ellingwood
date: 2017-11-09
language: en
license: cc by-nc-sa
source: https://www.digitalocean.com/community/tutorials/how-to-create-a-point-to-point-vpn-with-wireguard-on-ubuntu-16-04
---

# How To Create a Point-To-Point VPN with WireGuard on Ubuntu 16.04

## Installation

    sudo add-apt-repository -y ppa:wireguard/wireguard
    sudo apt-get update
    sudo apt-get install -y wireguard wireguard-dkms wireguard-tools linux-headers-$(uname -r)
    sudo modprobe wireguard
    
## Key Generation

    Umask 077
    wg genkey | tee server_private_key | wg pubkey > server_public_key
    wg genkey | tee client_private_key | wg pubkey > client_public_key

## Configuration

    sudo nano /etc/wireguard/wg0.conf
    
    
/etc/wireguard/wg0.conf

    [Interface]
    PrivateKey = generated_private_key
    ListenPort = 5555
    SaveConfig = true

**Note:** When `SaveConfig` is enabled, the `wg-quick` service will overwrite the contents of the `/etc/wireguard/wg0.conf` file whenever the service shuts down. If you need to modify the WireGuard configuration, either shut down the `wg-quick` service prior to editing the `/etc/wireguard/wg0.conf` file or make the changes to the running service using the `wg` command (these will be be saved in the file when the service shuts down). Any changes made to the configuration file while the service is running will be overwritten when `wg-quick` stores its active configuration.
