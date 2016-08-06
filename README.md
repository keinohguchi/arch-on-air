# Arch-on-Air

Yet another notes on `Let's make ArchLinux up and running on MacBook Air!`

Thie is my way of running *Arch* on *Air*, based on the official
[ArchLinux on MacBook(Air)](https://wiki.archlinux.org/index.php/MacBook) wiki.

## Hardware

Her is my air:

```
Model Name:		MacBook Air
Model Identifier:	MacBookAir7,1
Processor Name:		Intel Core i7
Processor Speed:	2.2 GHz
Number of Processors:	1
Total Number of Cores:	2
L2 Cache (per Core):	256 KB
L3 Cache:		4 MB
Memory:			8 GB
```

I follow the officieal [Arch Installation guide](https://wiki.archlinux.org/index.php/installation_guide) section format, so that, I hope, it's easy to follow.

## Pre-installation

## Dual booting

As I use OSX ocasionally, I dual boot the air with OSX.  As recommended on
[Arch on MacBook(Air) wiki](https://wiki.archlinux.org/index.php/MacBook#OS_X_with_Arch_Linux),
I use the Apple partition tool to shrink the OSX partition to
around 180GB to make enough space for linux.  And based on the libvirt
recommendation, I create a dedicated partition for the libvirt storage pool,
which ended up like this:

```
root@archiso ~ # lsblk
NAME         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda            8:0    0 465.9G  0 disk
├─sda1         8:1    0   200M  0 part
├─sda2         8:2    0 179.2G  0 part
├─sda3         8:3    0 619.9M  0 part
├─sda4         8:4    0   152G  0 part
└─sda5         8:5    0 133.9G  0 part
```

Here, *sda1* for the EFI system partition, *sda2* for OSX, *sda4* for the base Linux,
and *sda5* for the libvirt storage pool.

### Set the keyboard layout

Load *emacs key binding*, as usual:

```
root@archiso ~ # loadkeys /usr/share/kbd/keymaps/i386/qwerty/emacs2.map.gz
```

### Connect to the Internet

As default wifi doesn't work out of the box, I just connect TP-Link power over
ether adapter and hook into the thunderbolt port:

```
root@archiso ~ # ip l
2: ens9: <BROADCAST,MULTICAST>
  link/ether 38:...
```

and then, run *dhcp* on top of it:

```
root@archiso ~ # systemctl start dhcpcd@ens9
```

### Partition the disks

I use OSX disk utilility to make a 

## Installation

## Post-installation
