# Real-time Linux Playground

This repo contains experimental code to play with Real-time Linux and other RTOS.

# Ubuntu

Real-time Ubuntu will be supported on LTS and interim versions. See <https://documentation.ubuntu.com/real-time/en/latest/reference/releases/>.
The LTS versions have been created by Canonical merging the [PREEMPT_RT](https://wiki.linuxfoundation.org/realtime/documentation/technical_details/start) patches into kernel. The latest interim version 25.04 (Kernel 6.14) does rely on [fully merged PREEMPT_RT](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=baeb9a7d8b60b021d907127509c44507539c15e5) into kernel 6.12 (09/2024).

Note: Real-time Ubuntu requires a Ubuntu Pro subscription, which is available for free for personal use. See [Ubuntu Pro](https://ubuntu.com/pro).

## Installation Ubuntu 24.04 LTS (Noble Numbat)

Ubuntu 24.04 LTS has been installed on an Parallels (20.3.1) VM (2 cores, 4 GB RAM, 64 GB disk) on a MacBook Pro M1 MAX (32 GB RAM).

* Create new VM of Parallels type "Ubuntu 24.04 ARM64" with defaults
* Install Parallel Tools Installation Agent
* Update all software packages

Note: I am aware that reliable stress and latency tests of Real-time capabilities should be done on bare metal, this VM was just used for simple development.

```bash
# check kernel version
# expected: 6.8.0-40-generic, 6.8.0-60-generic
uname -r

# make sure latest Ubunto Pro client is installed
sudo apt update && sudo apt install ubuntu-advantage-tools
# attach your installation to your subscription
sudo pro attach <free-personal-token>
pro status

# enable real time
sudo pro enable realtime-kernel
One moment, checking your subscription first
No variant specified. To specify a variant, use the variant option.
Auto-selecting generic variant. Proceed? (y/N) y
The Real-time kernel is an Ubuntu kernel with PREEMPT_RT patches integrated.

This will change your kernel. To revert to your original kernel, you will need
to make the change manually.

Do you want to continue? [ default = Yes ]: (Y/n) y
Configuring APT access to Real-time kernel
Updating Real-time kernel package lists
Updating standard Ubuntu package lists
Installing Real-time kernel packages
Real-time kernel enabled
A reboot is required to complete install.

# a reboot is necessary
reboot

# check if Real-time kernel is installed
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
# This seems to fail, even checking realtime feature does show "disabled"
# But after reboot it seems that realtime kernel has been installed
# Create bug for Canonical: https://github.com/canonical/ubuntu-pro-client/issues/3447
sudo pro enable realtime-kernel
One moment, checking your subscription first
Real-time kernel is not available for Ubuntu 25.04 (Plucky Puffin).
Could not enable Real-time kernel.

# After reboot it seems that realtime kernel has been installed
reboot

# check if Real-time kernel is installed
# expected: 6.14.0-1002-realtime
uname -r
```

## Testing

Follow Ubuntu tutorial here: <https://documentation.ubuntu.com/real-time/en/latest/tutorial/first-rt-app/>.

Notes:
* All Ubuntu samples run as expected also in VM
* Samples require to be run as root using sudo as `sched_setscheduler` needs root privilegdes. Otherwise you will see in strace a failed call: `sched_setscheduler(20759, SCHED_FIFO, [89]) = -1 EPERM (Operation not permitted)`

TODO stress testing

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
* <https://ubuntu.com/blog/real-time-kernel-technical>
