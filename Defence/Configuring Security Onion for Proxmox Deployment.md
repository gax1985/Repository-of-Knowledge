---
title: "Configuring Security Onion for Proxmox Deployment"
source: "https://medium.com/meese-enterprises/configuring-security-onion-for-proxmox-deployment-ecfc7b38c6da"
author:
  - "[[Aaron Meese]]"
published: 2025-04-04
created: 2025-10-25
description: "Configuring the network interfaces correctly is a daunting task for first-timers, this guide aims to simplify the process so you can get operational."
tags:
  - "clippings"
---
[Sitemap](https://medium.com/sitemap/sitemap.xml)

[Mastodon](https://me.dm/@ajmeese7)## [Meese Enterprises](https://medium.com/meese-enterprises?source=post_page---publication_nav-74de64bcf656-ecfc7b38c6da---------------------------------------)

[![Meese Enterprises](https://miro.medium.com/v2/resize:fill:38:38/1*6AhnZI2pO8Gv3XAjnYLpkw.png)](https://medium.com/meese-enterprises?source=post_page---post_publication_sidebar-74de64bcf656-ecfc7b38c6da---------------------------------------)

Detailed write-ups about client projects and any technical challenges we encounter throughout the course of our work.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/0*DaumDekKYuCaSetG.jpg)

Courtesy of Security Onion Solutions.

Wanting to have better visibility into my network, I decided to try doing a local deployment of Security Onion. I have Proxmox running on my homelab, so I assumed it would be easy to drop the ISO into that environment and spin it up just like any other OS.

I was mistaken.

### Documentation

The project itself has very extensive documentation, which can be found here:## [Security Onion Documentation - Security Onion Documentation 2.4 documentation](https://docs.securityonion.net/en/2.4/?source=post_page-----ecfc7b38c6da---------------------------------------)

Edit description

docs.securityonion.net

[View original](https://docs.securityonion.net/en/2.4/?source=post_page-----ecfc7b38c6da---------------------------------------)

The issue is that their [Proxmox documentation](https://docs.securityonion.net/en/2.4/proxmox.html) is… lacking. I was able to follow their “First Time Users” [deployment guide](https://docs.securityonion.net/en/2.4/first-time-users.html#first-time-users) to get me to this point:

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*di0rXf_3V6-JX5Hys4BE8g.png)

Oh boy, this is gonna be fun…

Searching up the issue, I found their [configuration page](https://docs.securityonion.net/en/2.4/configuration.html) has an instance of this exact message! Should be easy to solve then, right?

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*oGkMYbgcnuCjWZnzfYPX-g.png)

Wrong…

This tells me what the fix is *supposed* to be, but gives no indication as to how you are supposed to implement it.

### Proxmox Configuration

To back up some, this section is the configurations I went through to get to this point of having a box I could interact with.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*_BehJo13BgxpgmNZt96q3g.png)

Go to “local (proxmox)” and upload your ISO, which you can get from here.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*NwX43tBLUxC_pPo19OB3XQ.png)

Then you create a VM.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*gh1mIIPDMvqKEkxww5NAww.png)

Selecting whatever options make sense for your setup on this first page.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*D2CvHa2tNq7obDeTNcOYMA.png)

Then choosing that ISO for the OS, ensuring that Linux is selected for the Guest OS type.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*qVP2qLpkKZn9Pd42W47bYw.png)

Choose the machine type.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*dQRXSjAqha6w2Udyn06XwA.png)

Make sure you add enough storage to meet the specifications.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*GaYNxZhEatDUY-C0-AkwUw.png)

Do the same with the CPU.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*9RpPANjXZrrjv2L-HBYPtw.png)

And the memory.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*l8wSpXys3Hwwi82a_8guug.png)

We can start with the default network settings, we will change this later.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*dOYR1tmBUMS2YDZjKhvcSg.png)

And you can go ahead and create it, but do not boot it yet.

### Network Configuration

At this point, we have to figure out how to create the IP-less network interface that SecOnion is requesting. I was eventually able to accomplish this using a combination of these resources, although I ended up taking a different approach from the first two:## [\[TUTORIAL\] - Proxmox + Security Onion without OVS](https://forum.proxmox.com/threads/proxmox-security-onion-without-ovs.128473/?source=post_page-----ecfc7b38c6da---------------------------------------)
[[TUTORIAL - Proxmox + Security Onion without OVS]]
Since there is a complete lack of SPAN/Mirror examples using Linux Bridges into Security Onion, I thought I'd post what…

forum.proxmox.com

[View original](https://forum.proxmox.com/threads/proxmox-security-onion-without-ovs.128473/?source=post_page-----ecfc7b38c6da---------------------------------------)## [GitHub - 0xvext/proxmox-seconiontap.sh: A bash script to create a persistent port mirror for an IDS…](https://github.com/0xvext/proxmox-seconiontap.sh?source=post_page-----ecfc7b38c6da---------------------------------------)


# proxmox-seconiontap.sh
>[!code]
>```
#!/bin/dash
SECONIONLOG=/root/proxmox-seconiontap.log
date >> $SECONIONLOG
echo "####################" >> $SECONIONLOG
echo "Clearing any existing mirror..." >> $SECONIONLOG
ovs-vsctl clear bridge vmbr4 mirrors
echo "Creating mirror on vmbr4 for Security Onion..." >> $SECONIONLOG
ovs-vsctl -- --id=@p get port tap202i1 \
-- --id=@m create mirror name=span1 select-all=true output-port=@p \
-- set bridge vmbr4 mirrors=@m >> $SECONIONLOG
echo "Showing existing mirrors..." >> $SECONIONLOG
ovs-vsctl list Mirror >> $SECONIONLOG
echo "####################" >> $SECONIONLOG
>```


A bash script to create a persistent port mirror for an IDS within a Proxmox hypervisor - 0xvext/proxmox-seconiontap.sh

github.com

[View original](https://github.com/0xvext/proxmox-seconiontap.sh?source=post_page-----ecfc7b38c6da---------------------------------------)## [Network Configuration](https://pve.proxmox.com/wiki/Network_Configuration?source=post_page-----ecfc7b38c6da---------------------------------------)

Proxmox VE is using the Linux network stack. This provides a lot of flexibility on how to set up the network on the…

pve.proxmox.com

[View original](https://pve.proxmox.com/wiki/Network_Configuration?source=post_page-----ecfc7b38c6da---------------------------------------)

The method I used was **Creating a Dedicated Sniffing Bridge in Proxmox**, which turned out to be pretty straightforward. The steps were:

1. **Navigate to Proxmox Host Network Settings:** Go to Datacenter -> YourProxmoxNode -> System -> Network.
2. **Create a New Bridge:** Click Create -> Linux Bridge.
3. **Apply Configuration:** Click Apply Configuration (you might need to reboot the host or reload networking, Proxmox will usually prompt if needed, often it applies dynamically).

For the second step, the options we had to use were:

- **Name:** Give it a descriptive name, e.g., *vmbr1* (if not already used)
- **IP Address / CIDR:** Leave **BLANK**. This is crucial.
- **Gateway:** Leave **BLANK**.
- **Bridge ports:** This is where you link the physical NIC that receives the SPAN/TAP traffic.  
	\- **If using a physical SPAN/TAP port:** Identify the physical NIC on your Proxmox host (e.g., eno2, eth1) that is *exclusively* connected to your switch’s SPAN/mirror port. Enter that physical NIC name here (e.g., eno2). **Important:** This physical NIC should *not* be part of any other bridge (like vmbr0).  
	\- **If monitoring traffic between VMs on the *same* Proxmox host:** You might leave “Bridge ports” blank for now. You’ll attach the VMs you want to monitor *and* the SO sniffing interface to this bridge later.
- **Comment:** Add a note like “Security Onion Sniffing Port” or “SPAN Input”.
- Click Create.

The resulting entry will look like so:

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*bk15RxZEOsnEQ_HQJgkgQw.png)

Very, very basic.

### Additional Proxmox Configuration

Now that we have our new bridge, we can go back to the *securityonion* machine and make our final tweaks. You’re going to want to navigate to the “Hardware” tab and click “Add,” then choose “Network Device.” You are going to choose the new *vmbr1* and uncheck the “Firewall” box.

From here, you can start up the machine and begin configuration like normal. When prompted to choose the management interface, select the first NIC (ex. *ens18*) and select the other interface (ex. *ens19*) when prompted to choose the sniffing interface.

Then you’ll have a production instance of Security Onion to use on Proxmox!

[![Meese Enterprises](https://miro.medium.com/v2/resize:fill:48:48/1*6AhnZI2pO8Gv3XAjnYLpkw.png)](https://medium.com/meese-enterprises?source=post_page---post_publication_info--ecfc7b38c6da---------------------------------------)

[![Meese Enterprises](https://miro.medium.com/v2/resize:fill:64:64/1*6AhnZI2pO8Gv3XAjnYLpkw.png)](https://medium.com/meese-enterprises?source=post_page---post_publication_info--ecfc7b38c6da---------------------------------------)

[Last published Apr 4, 2025](https://medium.com/meese-enterprises/configuring-security-onion-for-proxmox-deployment-ecfc7b38c6da?source=post_page---post_publication_info--ecfc7b38c6da---------------------------------------)

Detailed write-ups about client projects and any technical challenges we encounter throughout the course of our work.

CTI Hunter, OSINT Enthusiast, Full Stack Developer

## More from Aaron Meese and Meese Enterprises

## Recommended from Medium

[

See more recommendations

](https://medium.com/?source=post_page---read_next_recirc--ecfc7b38c6da---------------------------------------)