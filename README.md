# ZNID-GPON-2424A-0ET

This repository provides information about the ZNID-GPON-2424A-0ET router, which is customized by Etisalat UAE.

## Device Overview
* Model: ZNID-GPON-2424A-0ET
* ISP: Etisalat UAE
* Ports:4 LAN ports
* 2 telephone ports
* 1 fiber WAN port

 ## Access and Configuration
Initially, I had trouble accessing the router's web interface. After some investigation, I found out that this device is heavily customized by the ISP.

## Access Information
After performing a factory reset, I was able to access the router with the following details:
* IP Address: 192.168.1.1
* Username: zhone
* Password: admin

Once logged in, I enabled Telnet and SSH.


## Telnet and SSH Access

Although Telnet and SSH were enabled, I encountered difficulties logging in with several common usernames and passwords. Here’s what I tried
* :Username: root
* :Password: root (didn't work)
* Other combinations tried:
* root/zhone
* user/user


Eventually, I found a working set of credentials
* :Username: admin
* Password: zhone

 ```
root@kali:-# telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.

               Welcome to Zhone Technologies
               Model: ZNID-GPON-2424A-0ET Router
               Release: S3.0.207

Copyright (C) 2009-2014 by Zhone Technologies.  All Rights Reserved.
Confidential, Unpublished Property of Zhone Technologies.
Rights Reserved Under the Copyright Laws of the United States.

Login: admin
Password:
telnetd:210.583:zhnLogSecurityMsg:230:Telnetd: Authorized login successful  for user admin from IP 192.168.1.25:23

ZNID24xxA-Router>
  enable      Turn on privileged mode command
  exit        Exit current mode and down to previous mode
  list        Print command list
  logout      Log out from the current session
  ping        Send echo messages
  quit        Exit current mode and down to previous mode
  show        Show running system information
  ssh         Open an ssh connection
  telnet      Open a telnet connection
  terminal    Set terminal line parameters
  top         Exit from the current mode and go to the view node
  traceroute  Trace route to destination
ZNID24xxA-Router> enable
ZNID24xxA-Router#
  archive      Archive a software image
  configure    Configuration mode
  development  development mode
  disable      Turn off privileged mode command
  end          End current mode and change to enable mode
  exit         Exit current mode and down to previous mode
  list         Print command list
  lldp         Link-Layer Discovery Protocol (LLDP) information
  logout       Log out from the current session
  ping         Send echo messages
  quit         Exit current mode and down to previous mode
  reload       Reload a software image
  show         Show running system information
  ssh          Open an ssh connection
  telnet       Open a telnet connection
  terminal     Set terminal line parameters
  test         Test mode
  top          Exit from the current mode and go to the view node
  traceroute   Trace route to destination
ZNID24xxA-Router# development
ZNID24xxA-Router(development)# sh

start start-shell


BusyBox v1.17.2 (2015-10-06 14:23:51 EDT) built-in shell (ash)
Enter 'help' for a list of built-in commands.

~ #
~ # ls
bin         dev         lib         opt         sys         var
cferam.003  etc         linuxrc     proc        tmp         vmlinux.lz
data        include     mnt         sbin        usr         webs
~ # ssh
/bin/sh: ssh: not found
~ # dropbear
/bin/sh: dropbear: not found
~ # uname -a
Linux ZNID24xxA-Router 2.6.30 #2 Tue Oct 6 14:14:30 EDT 2015 mips GNU/Linux
~ #
~ #
~ #
~ # cat /proc/mtd
dev:    size   erasesize  name
mtd0: 03d60000 00020000 "rootfs"
mtd1: 03d60000 00020000 "rootfs_update"
mtd2: 00400000 00020000 "data"
mtd3: 00020000 00020000 "nvram"
~ # cd /etc
/etc #
/etc #
/etc # cat image_version
S3.0.207
/etc # cat passwd
root:KuRzVcdDb9Ypg:0:0:Zhone Technical Support:/:/bin/sh
reset2defaults:F9n8Z/0zN9S1E:0:0:Reset to Factory Defaults:/:/bin/sh
manufacturing:gYsZ25Avv8hLM:0:0:Manufacturing:/:/bin/sh
admin:C..9OCKu3.vZw:0:0:Administrator:/:/bin/sh
user:XbISGvXIaPIf2:0:0:User:/:/bin/sh
nobody:54IXFhufS24k.:0:0:nobody for ftp:/:/bin/sh
/etc #
~#
~# cd sys
/sys # ls
block     class     devices   fs        module
bus       dev       firmware  kernel
/sys # cd dev
/sys/dev # ls
block  char
/sys/dev # cd ..
/sys # ls
block     class     devices   fs        module
bus       dev       firmware  kernel
/sys # cd firmware
/sys/firmware # ls
/sys/firmware # cd ..
/sys # cd block
/sys/block # ls
mtdblock0  mtdblock1  mtdblock2  mtdblock3
/sys/block #
~ # ls /proc
1              215            8              ioports        ploam
10             3              80             irq            scsi
1082           317            9              kallsyms       self
11             328            bcmlog         kcore          slabinfo
1107           329            brcm           kmsg           stat               111            330            buddyinfo      kpagecount     switch
112            3384           bus            kpageflags     sys
113            3385           cmdline        led            sysrq-trigger
1138           3508           cpuinfo        loadavg        sysvipc
115            3520           crypto         locks          timer_list
12             375            devices        meminfo        tty
1254           397            diskstats      mii            uptime
1255           398            driver         misc           var
1258           4              execdomains    modules        version
13             432            fcache         mounts         vmallocinfo
1559           434            filesystems    mtd            vmstat
1560           438            fs             net            zhn_gpon
16             5              i2c_gpon       nvram          zoneinfo
172            6              i2c_moca       omci
2              7              i2c_sfp        pagetypeinfo
207            71             interrupts     partitions
214            722            iomem          pktcmf
~ # cat /proc/cmdline
root=mtd:rootfs ro rootfstype=jffs2 console=ttyS0,115200
~ # ls /dev
ac97            ippp1           ptyp5           sdc             spu
bcm             isdn            ptyp6           sdc1            tty
bcm_omci        isdnctrl        ptyp7           sdc2            tty0
bcm_ploam       isdnctrl0       ptyp8           sdc3            tty1
bcm_user_ploam  isdninfo        ptyp9           sdc4            ttyS0
bcm_user_tod    kmem            ptypa           sdc5            ttyS1
bcmaal20        laser_dev       ptypb           sdc6            ttyUSB0
bcmadsl0        linux-uk-proxy  ptypc           sdc7            ttyUSB1
bcmadsl1        linux-user-bde  ptypd           sdc8            ttyUSB2
bcmarl          log             ptype           sdc9            ttyUSB3
bcmatm0         mem             ptypf           sdd             ttyUSB4
bcmatmb0        misc            pwrmngt         sdd1            ttyUSB5
bcmendpoint0    mtd0            ram             sdd2            ttyUSB6
bcmepon         mtd1            ram0            sdd3            ttyUSB7
bcmfap          mtd2            ram1            sdd4            ttyp0
bcmles0         mtd3            ram2            sde             ttyp1
bcmmoca0        mtdblock0       ram3            sde1            ttyp2
bcmmoca10       mtdblock1       random          sde2            ttyp3
bcmprof         mtdblock2       sda             sde3            ttyp4
bcmvdsl0        mtdblock3       sda1            sde4            ttyp5
bcmvlan         mtdblock4       sda2            sdf             ttyp6
bcmxtmcfg0      mtdblock5       sda3            sdf1            ttyp7
bounce          mtdblock6       sda4            sdf2            ttyp8
bpm             mtdblock7       sda5            sdf3            ttyp9
brcmboard       null            sda6            sdf4            ttypa
capi20          p8021ag0        sda7            sdg             ttypb
chipinfo        pktcmf          sda8            sdg1            ttypc
console         pmon            sda9            sdg2            ttypd
dect            port            sdb             sdg3            ttype
dectdbg         ppp             sdb1            sdg4            ttypf
dectshim        printer0        sdb2            sdh             ubi0
ext_bonding     ptm             sdb3            sdh1            ubi_ctrl
fcache          pts             sdb4            sdh2            urandom
fuse            ptyp0           sdb5            sdh3            watchdog
hwrandom        ptyp1           sdb6            sdh4            zero
i2c-0           ptyp2           sdb7            si3215
ingqos          ptyp3           sdb8            slac
ippp0           ptyp4           sdb9            soc4e
~ #
~ # busybox
BusyBox v1.17.2 (2015-10-06 14:23:51 EDT) multi-call binary.
Copyright (C) 1998-2009 Erik Andersen, Rob Landley, Denys Vlasenko
and others. Licensed under GPLv2.
See source distribution for full notice.

Usage: busybox [function] [arguments]...
   or: function [arguments]...

        BusyBox is a multi-call binary that combines many common Unix
        utilities into a single executable.  Most people will create a
        link to busybox for each function they wish to use and BusyBox
        will act like whatever it was invoked as.

Currently defined functions:
        [, [[, addgroup, adduser, arp, ash, awk, basename, bash, cat, chgrp,
        chmod, chown, chroot, clear, cp, cut, date, dd, delgroup, deluser,
        depmod, devmem, df, dhcprelay, diff, dirname, dmesg, dnsdomainname,
        dos2unix, du, dumpleases, echo, egrep, env, expr, false, fgrep, find,
        flash_eraseall, free, ftpget, ftpput, getopt, getty, grep, gunzip,
        gzip, halt, hd, head, hexdump, hostid, hostname, hush, ifconfig, init,
        insmod, kill, killall, klogd, less, linuxrc, ln, logger, login,
        logread, ls, lsmod, lsusb, md5sum, mkdir, mknod, modprobe, more, mount,
        mv, netstat, nice, nslookup, passwd, pidof, ping, ping6, pivot_root,
        poweroff, ps, pwd, reboot, renice, reset, rm, rmdir, rmmod, route, sed,
        sendarp, sh, sleep, su, sync, sysinfo, syslogd, tail, tar, telnet,
        telnetd, test, tftp, tftpd, top, touch, traceroute, traceroute6, true,
        tty, udhcpc, udhcpd, udpsvd, umount, uname, unix2dos, uptime, usleep,
        vconfig, vi, wget, which, whoami, yes, zcat

~ #
```

It seems that the standard Linux root filesystem on this device does not include Dropbear or SSH. Despite thorough checks, I was unable to find any related files.

However, the device runs a custom shell that includes SSH functionality, although it is quite limited and does not support features like SCP.

Upon examining the main /etc/passwd file, I encountered several accounts, including one that was particularly confusing:

* Username: reset2defaults
* Password: F9n8Z/0zN9S1E

The presence of these accounts is unusual and seems to serve different purposes.

 ## Web UI Login Credentials

I have discovered the following login credentials for the web UI:
Manufacturer Accounts & Superadmin
* Username: support
* Password: zhone

Administration (ISP User & Manager Accounts):
* Username: admin
* Password: zhone (Note: This password may be automatically changed by the ISP through their TR-069 server or by a technician)


* Normal Accounts & Users:
* Username: user
* Password: user

## Firmware and Software

This router has a feature for alternative firmware installations. If a new version is loaded, the standard Linux filesystem features might not function as expected because the software development options have been removed.

