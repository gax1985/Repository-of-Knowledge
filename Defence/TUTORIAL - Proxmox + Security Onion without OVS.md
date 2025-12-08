---
title: "[TUTORIAL] - Proxmox + Security Onion without OVS"
source: "https://forum.proxmox.com/threads/proxmox-security-onion-without-ovs.128473/?source=post_page-----ecfc7b38c6da---------------------------------------"
author:
  - "[[JD-Howard]]"
published: 2023-06-05
created: 2025-10-25
description: "Since there is a complete lack of SPAN/Mirror examples using Linux Bridges into Security Onion, I thought I'd post what got working.... Also is an example..."
tags:
  - "clippings"
---
#### JD-Howard

##### New Member

Since there is a complete lack of SPAN/Mirror examples using Linux Bridges into Security Onion, I thought I'd post what got working.... Also is an example using multiple bridge mirrors, which is discussed but never actually shown anywhere.  
  
Disclaimer, I am still in the very early stages of setting up a home security lab. So, I may eventually switch to OVS like everyone else, but I didn't want to redo my whole network configuration and I honestly hate the CLI syntax of OVS. I've been using Proxmox for about 2 weeks. So, there are random IDK, correct me if I am wrong parts, but I would welcome any best practice feedback on the entire write up too. Also, you may see some inconsistency in how I refer to things (like SPAN & TAP), that is specifically to generate more keywords so people in my situation find this...  
  

---

  
**My Hardware: Proxmox1 (Security Appliance) & Proxmox2 (VM Appliance)**  
8(16) core, 65w, i7-17700 (currently on clearance @ BestBuy -$130)  
Gigabyte Z590I Aorus Ultra (I had to play with bios but got pass through working just fine)  
64gb 3200 DDR4 RAM  
4-port PCIE NIC + 1 onboard + 1 wifi card  
1TB NVME & at least 2TB of HDD for backups  
  
Note: VM Appliance does not have the 4-port nic, that one has a GTX 2080 installed.  
  
**Proxmox Security Appliance: VM Stack**  
*pfSense -* 2 cores 4GB ram - Dual WAN with failover. Two general LANs, 1 management LAN and not currently using any VLAN tagging.  
*Security Onion* - 14 cores 58GB ram - may get rid of this and use ELK/HULK instead, undecided...  
*Solus Bundgie VM* - 1 core 2GB ram - Probably converting to a CT at some point. Whole reason it exists is for PCI passthrough of the wifi card to create a HotSpot. Which was necessary because FreeBSD/pfSense does not currently support AX200 drivers. Chose SB because it is relatively small, capable, can use CT hardware and boots almost as fast as a CT does. Note that auto-login must be configured to actually activate the hotspot on boot; suggest making non-admin user for this.  
  
My only goal is to protect pfSense (which is the heart of everything) from being starved by Security Onions often high resource usage. So, the slight over provisioning is of no concern. Thinking of adding 2 more cores for a TrueNAS VM and still think I would be perfectly fine as long as SO can only access 14 of the 16 thread cores. If I am wrong in this assumption, let me know.  
  
**Proxmox Security Appliance: Networking Stack**  
enp1s0f0 assigned vmbr0 - used as pfSense WAN1  
enp1s0f1 assigned vmbr1 - used as pfSense WAN2  
enp1s0f2 assigned vmbr2 - used as pfSense LAN1 (connects to physical switch)  
enp1s0f3 assigned vmbr3 - used as pfSense LAN2 (connects to Proxmox VM Appliance)  
enp6s0 assigned vmbr4 - used as pfSense LANMAN/Security Onion (management)  
vmbr5 dummy SPAN port  
vmbr6 dummy SPAN port  
  
The 2 dummy ports are both getting "monitored" by Security Onion and were created with absolutely no assignments or customization. Seriously, just clicked create...  
  
**Proxmox Security Appliance: Security Onion Installation Notes**  
My installation was standalone/production without the Analyst Workstation. I actually had problems with one of my mirrored ports getting assigned the same IP that the management port was getting assigned and installation failing. With that said, I would recommend Security Onion be setup with only 1 management and 1 monitor port initially. After everything is up and running, you can very easily attach more sniffed bridges in Proxmox, use the NoVNC console on the SO VM and go run the **so-monitor-add** command. I have read that a BOND in ALB mode would probably have solved the problem too, but I haven't tested it and I just preferred keeping them separate.  
  
Finally, I didn't understand the Email/Password importance during install. I thought it was going to use that email account to send notification. Since all my passwords are 20+ character of generated BS, I just entered "changelater" and that was a big mistake. This is actually your login information for various SO Tools. Which is important because the various tools do not have the same password requirements and changing your password in 1 of them doesn't necessarily update the others.  
  
**Proxmox Security Appliance: VM Configuration**  
The following was produced by the **so-report** command. Tip: use **so-report > report.txt** to save it to a file and open it up with nano because its way more information than the NoVNC shell will let you scroll up on.  
  
The **important** takeaways from this output are:  
No firewalls; see verification section  
Uses hookscript; see automation section  
  

Code:

```
# cat /etc/pve/qemu-server/102.conf
agent: 1
boot: order=ide2;scsi0;net0
cores: 14
hookscript: local:snippets/createMirror.pl
hotplug: disk,network,usb,cpu
ide2: none,media=cdrom
memory: 59392
meta: creation-qemu=7.2.0,ctime=1685923347
name: SecOnion
net0: virtio=F6:F3:6E:14:A5:13,bridge=vmbr4
net1: virtio=F6:A9:09:F4:52:B4,bridge=vmbr5
net2: virtio=5E:4C:43:7D:62:F0,bridge=vmbr6
numa: 1
onboot: 1
ostype: l26
scsi0: local-lvm:vm-102-disk-0,iothread=1,size=200G
scsi1: storage:102/vm-102-disk-0.qcow2,iothread=1,size=1000G
scsihw: virtio-scsi-single
smbios1: uuid=f039b707-e20b-481d-9393-bd9fd128850d
sockets: 1
tpmstate0: local-lvm:vm-102-disk-1,size=4M,version=v2.0
vga: virtio
vmgenid: fbb05185-22d9-4b3c-98ed-bce8d2ae82da
```

  
  
**Proxmox Security Appliance: Automation**  
I don't recall if OVS has this issue or not, but sniffing the traffic through a bridge TC (traffic control) qdisc is definitively not a permanent configuration change. From what I can tell, turning on promiscuous mode for the sniffed ports is also not permanent. With that said, I assume OVS has a similar issue upon reboot; correct me if I am wrong...  
  
Here is the full contents of **createMirror.pl** referenced in the hardware VM Configuration section:  
  

Perl:

```perl
#!/usr/bin/perl

use strict;
use warnings;

my $vmid = shift;
my $phase = shift;

print "GUEST BRIDGE MIRROR HOOK: " . join(' ', @ARGV). "\n";

sub MirrorSourceToDestination
{
  my $src = $_[0];
  my $des = $_[1];
  my $uid = $_[2];

  # ingress
  print "Creating INGRESS qdisc for $src \n";
  system("tc", "qdisc", "add", "dev", "$src", "ingress");

  print "Creating INGRESS filter for $src to $des \n";
  system("tc", "filter", "add", "dev", "$src", "parent", "ffff:0",
               "protocol", "all",
               "u32", "match", "u8", "0", "0",
               "action", "mirred", "egress", "mirror", "dev", "$des");

  # egress
  print "Creating EGRESS qdisc for $src \n";
  system("tc", "qdisc", "add", "dev", "$src", "handle", "$uid:0", "root", "prio" );

  print "Creating EGRESS filter for $src to $des \n";
  system("tc", "filter", "add", "dev", "$src", "parent", "$uid:0",
               "protocol", "all",
               "u32", "match", "u8", "0", "0",
               "action", "mirred", "egress", "mirror", "dev", "$des");

  print "Turning on $src promiscuous mode \n";
  system("ip", "link", "set", "$src", "promisc", "on");
}

sub RemoveMirror
{
  my $target = $_[0];

  print "Removing INGRESS mapping from $target \n";
  system("tc", "qdisc", "del", "dev", "$target", "ingress" );

  print "Removing EGRESS mapping from $target \n";
  system("tc", "qdisc", "del", "dev", "$target", "root" );

  print "Turning off $target promiscuous mode \n";
  system("ip", "link", "set", "$target", "promisc", "on");
}

if ($phase eq 'pre-start') {
  # Create mirrors from a valid/used bridge to a dummy bridge Security Onion
  MirrorSourceToDestination("vmbr2", "vmbr5", "10");
  MirrorSourceToDestination("vmbr3", "vmbr6", "20");
} elsif ($phase eq 'pre-stop') {
  # Remove bridge mirrors on stop so it can be restarted without script errors
  RemoveMirror("vmbr2");
  RemoveMirror("vmbr3");
}

exit(0);
```

  
That last little bit (the IF conditions) is where you'll need to define source/destination mirror interfaces. You just change the vmbr #s to match your own source (sniffed port) bridge and destination (mirror dummy port) bridge. If you only have 1 to monitor, then you'll delete 1 of the RemoveMirror & MirrorSourceToDestination lines. If you have more than 2, then you'll add more of those. Beyond the source/destination names being accurate, that number is a unique id and thus must be unique. If you added a 3rd bridge to monitor, then you could provide that it a value of 30.  
  
Related information:  
**Data Center -> Storage -> Local -> Edit** --- Make sure snippets are turned on. If they weren't already, visiting the left pane "Local" will usually generate the folder for you.  
  
Next you need to open the proxmox NoVNC shell and use whatever editor your comfortable with (I installed nano) to make the **/var/lib/vz/snippets/createMirror.pl** file. Note that using the NoVNC shell does give you the ability to copy/paste from this post into nano, but you may need to use the context menu to do it.  
  
Once the perl file is created and you've adjusted all the vmbr #s, then you just need to attach it to your VM. Open the PVE Shell and execute something like this:  

Code:

```
qm set 102 --hookscript local:snippets/createMirror.pl
```

Note that the VMID (102) I am using will likely be different from yours and you may have put the script in a different place with a different name. So, adjust accordingly...  
  
**Proxmox Security Appliance: Verification**  
I'll be writing this in the context of having 2 separate physical ports and I will be passing data between them, but the concepts are the same even with 1 mirror port. If you have more than 2 mirror ports, then you'll just do more tests.  
  
At this point it is expected that Security Onion is installed, all the automation is hooked up and you've done a reboot, but didn't see a bunch of errors in the PVE interface or its shell. IE, the perl script isn't saying "I don't know what vmbr$x8 is..." or anything like that. You could perform the same test by doing a "qm stop vmid#" and the script will show some teardown messages, but nothing that looks like errors. Then do a "qm start vmid#" and again, it will show some setup messages, but nothing that looks like errors.  
  
To verify your source bridge(s) received the conditioning they need, you should be able to run this command in the PVE Shell and see similar output; just change the vmbr#...  

Code:

```
root@proxsec:~# tc qdisc show dev vmbr3
-------
OUTPUT
qdisc prio 20: root refcnt 2 bands 3 priomap 1 2 2 2 1 2 0 0 1 1 1 1 1 1 1 1
qdisc ingress ffff: parent ffff:fff1 ----------------
```

  
  
Proxmox VM Appliance Machine 1: (vmbr3 LAN2)  
mine is running Zorin OS and in the terminal I will perform the following commands  

Code:

```
sudo apt install iperf3
ip a
iperf3 -s
```

This installs iperf3, runs ip to get the current ipv4 address and runs it in server (listenting) mode. Note that I got 10.10.50.141 from "ip a".  
  
Physical Machine 2: (vmbr2 LAN1)  
Mine is running windows and using the WSL2 Ubuntu terminal, I perform the following commands  

Code:

```
sudo apt install iperf3
iperf3 -c 10.10.50.141 -V
```

This installs iperf3, runs iperf3 in client mode and should start sending lots of data to Machine 1. If it is not, then you probably have some firewall rules preventing it. Fallback to using the ping command on that IP and tinkering with your pfsense and/or proxmox firewall rules until ping works. Once you've accomplished that connectivity, then repeat the iperf3 command again and it should work.  
  
Once you have successfully ran the iperf3 test. Its time to snoop the total transfer values of our dummy bridges. From the PVE shell install the net-tools and run netstat.  

Code:

```
apt install net-tools
netstat -i
```

The output of netstat has a bunch of stuff, but the 2 things we want to know are the FLG & TX-OK data.  
On your SOURCE bridges, they should have BMPRU for the FLG. The P tells us they are indeed in permiscuous mode.  
On your DESTINATION bridges, you should have some large numbers in the TX-OK because of the iperf3 transfer.  
  
If both of those are true, then you can finally go look in Security Onion. I would suggest using Graphana and the Standalone Dashboard with the time interval dialed down to something more resonable. If your not seeing a major spike in traffic, but you are seeing "some" traffic, then I can almost guarentee you have the Proxmox firewall turned on for the Security Onion VM. For the longest time I couldn't figure out why the only thing coming through was dns and similar broadcast traffic. As soon as I shut off the VM specific Proxmox firewall for each bridge, it immediately started working!  
  
Well, hopefully that helps someone out there, but like I said... I am just getting started and still very prone to remodels. So, I may in fact need to refer back to this myself...

Last edited:

Reactions:[linqBuilder and killmasta93](https://forum.proxmox.com/posts/562023/reactions)

#### JD-Howard

##### New Member

I saw/read the first one, but I probably skimmed the vext guide. My issue with both of them was just that I didn't really want OVS for my first implementation. My entry point for all of what I did was from halfway down on this [backreference](https://backreference.org/2014/06/17/port-mirroring-with-linux-bridges/) article; which covers Linux & OVS, but not specifically in reference to PM/PFS. It took me in all kinds of directions trying to understand how/what these methods were doing and where it fit into my Proxmox/pfSense setup.  
  
Yes, I am mirroring the ingress/egress from my 2 LAN ports into Security Onion and theoretically nothing that the firewall stopped from entering the network. I am not far enough along in my Security Onion configuration to definitively say I am capturing everything using this method, but I can say I haven't found anything missing yet. I did pencil whip the LANS & WANS together and humans can miss things. So please let me know if I missed something and its confusing you; I would like to go fix it.

Reactions:[killmasta93](https://forum.proxmox.com/posts/563606/reactions)

#### killmasta93

##### Renowned Member

Thank you so much for the reply, so i was trying to adapt a bit to my setup which cant seem to figure out before trying  
  
This is the setup i need to mirror all traffic from pfsense to security onion  
  
as your setup you have many physical network cards in my case only have one,  
So seeing that i need also a dummy network would i need to create on proxmox vmbr5 dummy SPAN port and  
vmbr6 dummy SPAN port? without portslave?  
in the security onion it asks for management and mirror network would this case be the same the vmbr0 which is the LAN of pfsense?  
  
im guessin i would need to change this part of the script to adapt to my network?  
  

Code:

```
if ($phase eq 'pre-start') {
  # Create mirrors from a valid/used bridge to a dummy bridge Security Onion
  MirrorSourceToDestination("vmbr2", "vmbr5", "10");
  MirrorSourceToDestination("vmbr3", "vmbr6", "20");
} elsif ($phase eq 'pre-stop') {
  # Remove bridge mirrors on stop so it can be restarted without script errors
  RemoveMirror("vmbr2");
  RemoveMirror("vmbr3");
```

  
as i already installed SO on the Vm would i need to reinstall it again adding the new 2 networks of vmbr5 and vmbr6? would i need to add something special in the VM of SO?  
  
Thank you  
  
[![1686799530881.png](https://forum.proxmox.com/threads/proxmox-security-onion-without-ovs.128473/1686799530881.png "1686799530881.png")](https://forum.proxmox.com/attachments/1686799530881-png.51622/)

[Bottom](https://forum.proxmox.com/threads/proxmox-security-onion-without-ovs.128473/?source=post_page-----ecfc7b38c6da---------------------------------------#footer)

- ## We value your privacy
	We use essential [cookies](https://forum.proxmox.com/help/cookies) to make this site work, and optional cookies to enhance your experience.
	[See further information and configure your preferences](https://forum.proxmox.com/threads/proxmox-security-onion-without-ovs.128473/?source=post_page-----ecfc7b38c6da---------------------------------------#)