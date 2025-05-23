# Real-time Linux Playground

This repo contains experimental code to play with Real-time Linux and other RTOS.

# Ubuntu

Real-time Ubuntu will be supported on LTS and interim versions. See <https://documentation.ubuntu.com/real-time/en/latest/reference/releases/>.
The LTS versions have been created by Ubuntu merging the [PREEMPT_RT](https://wiki.linuxfoundation.org/realtime/documentation/technical_details/start) patches into kernel. The latest interim version 25.04 (Kernel 6.14) does rely on [fully merged PREEMPT_RT](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=baeb9a7d8b60b021d907127509c44507539c15e5) into kernel 6.12 (09/2024).

Note: Real-time Ubuntu requires a Ubuntu Pro subscription, which is available for free for personal use. See [Ubuntu Pro](https://ubuntu.com/pro).

## Installation Ubuntu 24.04 LTS (Noble Numbat)

Ubuntu 24.04 LTS has been installed on an Parallels (20.3.1) VM (2 cores, 4 GB RAM, 64 GB disk) on a MacBook Pro M1 MAX (32 GB RAM).

* Create new VM of Parallels type "Ubuntu 24.04 ARM64" with defaults
* Install Parallel Tools Installation Agent
* Update all software packages

Note: I am aware that reliable tests should be done on bare metal, this VM was just used for simple development.

```bash
# check kernel version
# expected: 6.8.0-40-generic, 6.8.0-60-generic
uname -r

# TODO
# update all packages
# sudo apt-get update -y && sudo apt-get upgrade -y

# make sure latest Ubunto Pro client is installed
sudo apt update && sudo apt install ubuntu-advantage-tools
# attach your installation to your subscription
sudo pro attach <free-personal-token>
pro status
# enable real time
sudo pro enable realtime-kernel
# a reboot is necessary
reboot

# check if Real-time kernel is installed, should be
# expected: 6.8.1-1022-realtime
uname -r
```

## Installation Ubuntu 25.04 (Plucky Puffin)

Ubuntu 25.04 has been installed on an Intel NUC8 (Intel Core i7 x 8, 64 GiB RAM, 1 TB SSD).
Ubuntu is updated to latest packages.

```bash
# check kernel version
uname -r

# for interim versions, universe repo is needed. Not needed for LTS versions
sudo add-apt-repository universe
sudo apt update
sudo apt install ubuntu-realtime

# make sure latest Ubunto Pro client is installed
sudo apt update && sudo apt install ubuntu-advantage-tools
# attach your installation to your subscription
sudo pro attach <free-personal-token>
pro status
# enable real time
sudo pro enable realtime-kernel
# a reboot is necessary
reboot

# check if Real-time kernel is installed, should be
# 6.14.0-1002-realtime
uname -r
```

## Testing

TODO

# Ubuntu Core 

TODO after Ubuntu is working

# References

Real-time Linux in general:

* <https://wiki.linuxfoundation.org/realtime/start>
* <https://wiki.linuxfoundation.org/realtime/preempt_rt_versions>
* <https://www.linutronix.de/blog/A-Checklist-for-Real-Time-Applications-in-Linux>
* Final [merge commit](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=baeb9a7d8b60b021d907127509c44507539c15e5)

Ubuntu:

* <https://ubuntu.com/real-time>
* <https://documentation.ubuntu.com/real-time/en/latest/>
* <https://documentation.ubuntu.com/real-time/en/latest/how-to/uc-image-creation/>
* <https://packages.ubuntu.com/source/plucky/linux-realtime>
* <https://ubuntu.com/pro/dashboard>
* <https://documentation.ubuntu.com/pro-client/en/latest/howtoguides/enable_realtime_kernel/>
