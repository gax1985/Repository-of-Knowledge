---
title: "0xvext/proxmox-seconiontap.sh: A bash script to create a persistent port mirror for an IDS within a Proxmox hypervisor"
source: "https://github.com/0xvext/proxmox-seconiontap.sh?source=post_page-----ecfc7b38c6da---------------------------------------"
author:
  - "[[0xvext]]"
published:
created: 2025-10-25
description: "A bash script to create a persistent port mirror for an IDS within a Proxmox hypervisor - 0xvext/proxmox-seconiontap.sh"
tags:
  - "clippings"
---
**[proxmox-seconiontap.sh](https://github.com/0xvext/proxmox-seconiontap.sh)** Public

A bash script to create a persistent port mirror for an IDS within a Proxmox hypervisor

[GPL-3.0 license](https://github.com/0xvext/proxmox-seconiontap.sh/blob/master/LICENSE)

[Open in github.dev](https://github.dev/) [Open in a new github.dev tab](https://github.dev/) [Open in codespace](https://github.com/codespaces/new/0xvext/proxmox-seconiontap.sh?resume=1)

<table><thead><tr><th colspan="2"><span>Name</span></th><th colspan="1"><span>Name</span></th><th><p><span>Last commit message</span></p></th><th colspan="1"><p><span>Last commit date</span></p></th></tr></thead><tbody><tr><td colspan="3"><p><span><a href="https://github.com/0xvext/proxmox-seconiontap.sh/commit/29576c95c6a72be3860977f7e1ed005f8368c5c1">Initial versions for github</a></span></p><p><span><a href="https://github.com/0xvext/proxmox-seconiontap.sh/commit/29576c95c6a72be3860977f7e1ed005f8368c5c1">29576c9</a> ·</span></p><p><a href="https://github.com/0xvext/proxmox-seconiontap.sh/commits/master/"><span><span><span>5 Commits</span></span></span></a></p></td></tr><tr><td colspan="2"><p><a href="https://github.com/0xvext/proxmox-seconiontap.sh/blob/master/LICENSE">LICENSE</a></p></td><td colspan="1"><p><a href="https://github.com/0xvext/proxmox-seconiontap.sh/blob/master/LICENSE">LICENSE</a></p></td><td><p><a href="https://github.com/0xvext/proxmox-seconiontap.sh/commit/96a9fb405afcc04c5a6c2ec7b5fa544e0beea478">Initial commit</a></p></td><td></td></tr><tr><td colspan="2"><p><a href="https://github.com/0xvext/proxmox-seconiontap.sh/blob/master/README.md">README.md</a></p></td><td colspan="1"><p><a href="https://github.com/0xvext/proxmox-seconiontap.sh/blob/master/README.md">README.md</a></p></td><td><p><a href="https://github.com/0xvext/proxmox-seconiontap.sh/commit/748d7220d2b829ff748a1a3de1ef7ee28d4ca099">Formatted readme</a></p></td><td></td></tr><tr><td colspan="2"><p><a href="https://github.com/0xvext/proxmox-seconiontap.sh/blob/master/proxmox-seconiontap.sh">proxmox-seconiontap.sh</a></p></td><td colspan="1"><p><a href="https://github.com/0xvext/proxmox-seconiontap.sh/blob/master/proxmox-seconiontap.sh">proxmox-seconiontap.sh</a></p></td><td><p><a href="https://github.com/0xvext/proxmox-seconiontap.sh/commit/29576c95c6a72be3860977f7e1ed005f8368c5c1">Initial versions for github</a></p></td><td></td></tr><tr><td colspan="3"></td></tr></tbody></table>

## proxmox-seconiontap.sh

A bash script to create a persistent port mirror for an IDS within a Proxmox hypervisor.

This bash script is intended to persist an OVS port mirror through a Proxmox reboot.

## Usage

Replace "tap202i1" with the appropriate interface of the appropriate VM you are trying to mirror to. Replace "vmbr4" with the OVS bridge your VM is attached to (you also need to configure a physical interface and upstream port mirroring to feed into the bridge). Replace "span1" with any name you would like the object to have, or leave it as it.

Save this script file in /root/ and then set up a crontab job to run it once 60 seconds after a reboot. Type `crontab -e` and add the following line:

`@reboot sleep 60 && /root/proxmox-seconiontap.sh`

Log output from the script will be created in /root/proxmox-seconiontap.log

## Releases

No releases published

## Packages

No packages published  

## Languages

- [Shell 100.0%](https://github.com/0xvext/proxmox-seconiontap.sh/search?l=shell)