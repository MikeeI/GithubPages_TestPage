---
author: Justin Ellingwood
date: 2017-11-09
language: en
license: cc by-nc-sa
source: https://www.digitalocean.com/community/tutorials/how-to-create-a-point-to-point-vpn-with-wireguard-on-ubuntu-16-04
---

# How To Create a Point-To-Point VPN with WireGuard on Ubuntu 16.04

## Introduction

    sudo add-apt-repository ppa:wireguard/wireguard
    sudo apt-get update
    sudo apt-get install wireguard wireguard-dkms wireguard-tools

**Note:** When `SaveConfig` is enabled, the `wg-quick` service will overwrite the contents of the `/etc/wireguard/wg0.conf` file whenever the service shuts down. If you need to modify the WireGuard configuration, either shut down the `wg-quick` service prior to editing the `/etc/wireguard/wg0.conf` file or make the changes to the running service using the `wg` command (these will be be saved in the file when the service shuts down). Any changes made to the configuration file while the service is running will be overwritten when `wg-quick` stores its active configuration.
