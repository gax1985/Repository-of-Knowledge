


  
[

# ![](https://book.hacktricks.wiki/images/CLOUD-web-logo.png)HackTricks

](https://book.hacktricks.wiki/)

[Hacktricks Training](https://training.hacktricks.xyz/)[Twitter](https://twitter.com/hacktricks_live)[Linkedin](https://www.linkedin.com/company/hacktricks)[Sponsor](https://github.com/sponsors/carlospolop)

 Translations

# [Volatility - CheatSheet](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#volatility---cheatsheet)

Reading time: 22 minutes

Learn & practice AWS Hacking:![](https://book.hacktricks.wiki/images/arte.png)[**HackTricks Training AWS Red Team Expert (ARTE)**](https://training.hacktricks.xyz/courses/arte)![](https://book.hacktricks.wiki/images/arte.png)  
Learn & practice GCP Hacking: ![](https://book.hacktricks.wiki/images/grte.png)[**HackTricks Training GCP Red Team Expert (GRTE)**](https://training.hacktricks.xyz/courses/grte)![](https://book.hacktricks.wiki/images/grte.png)

Support HackTricks

- Check the [**subscription plans**](https://github.com/sponsors/carlospolop)!
- **Join the** 💬 [**Discord group**](https://discord.gg/hRep4RUj7f) or the [**telegram group**](https://t.me/peass) or **follow** us on **Twitter** 🐦 [**@hacktricks_live**](https://twitter.com/hacktricks_live)**.**
- **Share hacking tricks by submitting PRs to the** [**HackTricks**](https://github.com/carlospolop/hacktricks) and [**HackTricks Cloud**](https://github.com/carlospolop/hacktricks-cloud) github repos.

​

If you need a tool that automates memory analysis with different scan levels and runs multiple Volatility3 plugins in parallel, you can use autoVolatility3:: [https://github.com/H3xKatana/autoVolatility3/](https://github.com/H3xKatana/autoVolatility3/)

bash

```bash
# Full scan (runs all plugins)
python3 autovol3.py -f MEMFILE -o OUT_DIR -s full

# Minimal scan (runs a limited set of plugins)
python3 autovol3.py -f MEMFILE -o OUT_DIR -s minimal

# Normal scan (runs a balanced set of plugins)
python3 autovol3.py -f MEMFILE -o OUT_DIR -s normal

```

If you want something **fast and crazy** that will launch several Volatility plugins on parallel you can use: [https://github.com/carlospolop/autoVolatility](https://github.com/carlospolop/autoVolatility)

bash

```bash
python autoVolatility.py -f MEMFILE -d OUT_DIRECTORY -e /home/user/tools/volatility/vol.py # It will use the most important plugins (could use a lot of space depending on the size of the memory)
```

## [Installation](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#installation)

### [volatility3](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#volatility3)

bash

```bash
git clone https://github.com/volatilityfoundation/volatility3.git
cd volatility3
python3 setup.py install
python3 vol.py —h
```

### [volatility2](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#volatility2)

Method1Method 2

```
Download the executable from https://www.volatilityfoundation.org/26
```

## [Volatility Commands](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#volatility-commands)

Access the official doc in [Volatility command reference](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference#kdbgscan)

### [A note on “list” vs. “scan” plugins](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#a-note-on-list-vs-scan-plugins)

Volatility has two main approaches to plugins, which are sometimes reflected in their names. “list” plugins will try to navigate through Windows Kernel structures to retrieve information like processes (locate and walk the linked list of `_EPROCESS` structures in memory), OS handles (locating and listing the handle table, dereferencing any pointers found, etc). They more or less behave like the Windows API would if requested to, for example, list processes.

That makes “list” plugins pretty fast, but just as vulnerable as the Windows API to manipulation by malware. For instance, if malware uses DKOM to unlink a process from the `_EPROCESS` linked list, it won’t show up in the Task Manager and neither will it in the pslist.

“scan” plugins, on the other hand, will take an approach similar to carving the memory for things that might make sense when dereferenced as specific structures. `psscan` for instance will read the memory and try to make`_EPROCESS` objects out of it (it uses pool-tag scanning, which is searching for 4-byte strings that indicate the presence of a structure of interest). The advantage is that it can dig up processes that have exited, and even if malware tampers with the `_EPROCESS` linked list, the plugin will still find the structure lying around in memory (since it still needs to exist for the process to run). The downfall is that “scan” plugins are a bit slower than “list” plugins, and can sometimes yield false positives (a process that exited too long ago and had parts of its structure overwritten by other operations).

From: [http://tomchop.me/2016/11/21/tutorial-volatility-plugins-malware-analysis/](http://tomchop.me/2016/11/21/tutorial-volatility-plugins-malware-analysis/)

## [OS Profiles](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#os-profiles)

### [Volatility3](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#volatility3-1)

As explained inside the readme you need to put the **symbol table of the OS** you want to support inside _volatility3/volatility/symbols_.  
Symbol table packs for the various operating systems are available for **download** at:

- [https://downloads.volatilityfoundation.org/volatility3/symbols/windows.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/windows.zip)
- [https://downloads.volatilityfoundation.org/volatility3/symbols/mac.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/mac.zip)
- [https://downloads.volatilityfoundation.org/volatility3/symbols/linux.zip](https://downloads.volatilityfoundation.org/volatility3/symbols/linux.zip)

### [Volatility2](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#volatility2-1)

#### [External Profile](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#external-profile)

You can get the list of supported profiles doing:

bash

```bash
./volatility_2.6_lin64_standalone --info | grep "Profile"
```

If you want to use a **new profile you have downloaded** (for example a linux one) you need to create somewhere the following folder structure: _plugins/overlays/linux_ and put inside this folder the zip file containing the profile. Then, get the number of the profiles using:

bash

```bash
./vol --plugins=/home/kali/Desktop/ctfs/final/plugins --info
Volatility Foundation Volatility Framework 2.6


Profiles
--------
LinuxCentOS7_3_10_0-123_el7_x86_64_profilex64 - A Profile for Linux CentOS7_3.10.0-123.el7.x86_64_profile x64
VistaSP0x64                                   - A Profile for Windows Vista SP0 x64
VistaSP0x86                                   - A Profile for Windows Vista SP0 x86
```

You can **download Linux and Mac profiles** from [https://github.com/volatilityfoundation/profiles](https://github.com/volatilityfoundation/profiles)

In the previous chunk you can see that the profile is called `LinuxCentOS7_3_10_0-123_el7_x86_64_profilex64`, and you can use it to execute something like:

bash

```bash
./vol -f file.dmp --plugins=. --profile=LinuxCentOS7_3_10_0-123_el7_x86_64_profilex64 linux_netscan
```

#### [Discover Profile](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#discover-profile)

```
volatility imageinfo -f file.dmp
volatility kdbgscan -f file.dmp
```

#### [**Differences between imageinfo and kdbgscan**](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#differences-between-imageinfo-and-kdbgscan)

[**From here**](https://www.andreafortuna.org/2017/06/25/volatility-my-own-cheatsheet-part-1-image-identification/): As opposed to imageinfo which simply provides profile suggestions, **kdbgscan** is designed to positively identify the correct profile and the correct KDBG address (if there happen to be multiple). This plugin scans for the KDBGHeader signatures linked to Volatility profiles and applies sanity checks to reduce false positives. The verbosity of the output and the number of sanity checks that can be performed depends on whether Volatility can find a DTB, so if you already know the correct profile (or if you have a profile suggestion from imageinfo), then make sure you use it from .

Always take a look at the **number of processes that kdbgscan has found**. Sometimes imageinfo and kdbgscan can find **more than one** suitable **profile** but only the **valid one will have some process related** (This is because to extract processes the correct KDBG address is needed)

bash

```bash
# GOOD
PsActiveProcessHead           : 0xfffff800011977f0 (37 processes)
PsLoadedModuleList            : 0xfffff8000119aae0 (116 modules)
```

bash

```bash
# BAD
PsActiveProcessHead           : 0xfffff800011947f0 (0 processes)
PsLoadedModuleList            : 0xfffff80001197ac0 (0 modules)
```

#### [KDBG](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#kdbg)

The **kernel debugger block**, referred to as **KDBG** by Volatility, is crucial for forensic tasks performed by Volatility and various debuggers. Identified as `KdDebuggerDataBlock` and of the type `_KDDEBUGGER_DATA64`, it contains essential references like `PsActiveProcessHead`. This specific reference points to the head of the process list, enabling the listing of all processes, which is fundamental for thorough memory analysis.

## [OS Information](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#os-information)

bash

```bash
#vol3 has a plugin to give OS information (note that imageinfo from vol2 will give you OS info)
./vol.py -f file.dmp windows.info.Info
```

The plugin `banners.Banners` can be used in **vol3 to try to find linux banners** in the dump.

## [Hashes/Passwords](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#hashespasswords)

Extract SAM hashes, [domain cached credentials](https://book.hacktricks.wiki/en/windows-hardening/stealing-credentials/credentials-protections.html#cached-credentials) and [lsa secrets](https://book.hacktricks.wiki/en/windows-hardening/authentication-credentials-uac-and-efs/index.html#lsa-secrets).

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.hashdump.Hashdump #Grab common windows hashes (SAM+SYSTEM)
./vol.py -f file.dmp windows.cachedump.Cachedump #Grab domain cache hashes inside the registry
./vol.py -f file.dmp windows.lsadump.Lsadump #Grab lsa secrets
```

## [Memory Dump](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#memory-dump)

The memory dump of a process will **extract everything** of the current status of the process. The **procdump** module will only **extract** the **code**.

```
volatility -f file.dmp --profile=Win7SP1x86 memdump -p 2168 -D conhost/
```

## [Processes](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#processes)

### [List processes](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#list-processes)

Try to find **suspicious** processes (by name) or **unexpected** child **processes** (for example a cmd.exe as a child of iexplorer.exe).  
It could be interesting to **compare** the result of pslist with the one of psscan to identify hidden processes.

vol3vol2

bash

```bash
python3 vol.py -f file.dmp windows.pstree.PsTree # Get processes tree (not hidden)
python3 vol.py -f file.dmp windows.pslist.PsList # Get process list (EPROCESS)
python3 vol.py -f file.dmp windows.psscan.PsScan # Get hidden process list(malware)
```

### [Dump proc](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#dump-proc)

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.dumpfiles.DumpFiles --pid <pid> #Dump the .exe and dlls of the process in the current directory
```

### [Command line](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#command-line)

Anything suspicious was executed?

vol3vol2

bash

```bash
python3 vol.py -f file.dmp windows.cmdline.CmdLine #Display process command-line arguments
```

Commands executed in `cmd.exe` are managed by **`conhost.exe`** (or `csrss.exe` on systems before Windows 7). This means that if **`cmd.exe`** is terminated by an attacker before a memory dump is obtained, it's still possible to recover the session's command history from the memory of **`conhost.exe`**. To do this, if unusual activity is detected within the console's modules, the memory of the associated **`conhost.exe`** process should be dumped. Then, by searching for **strings** within this dump, command lines used in the session can potentially be extracted.

### [Environment](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#environment)

Get the env variables of each running process. There could be some interesting values.

vol3vol2

bash

```bash
python3 vol.py -f file.dmp windows.envars.Envars [--pid <pid>] #Display process environment variables
```

### [Token privileges](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#token-privileges)

Check for privileges tokens in unexpected services.  
It could be interesting to list the processes using some privileged token.

vol3vol2

bash

```bash
#Get enabled privileges of some processes
python3 vol.py -f file.dmp windows.privileges.Privs [--pid <pid>]
#Get all processes with interesting privileges
python3 vol.py -f file.dmp windows.privileges.Privs | grep "SeImpersonatePrivilege\|SeAssignPrimaryPrivilege\|SeTcbPrivilege\|SeBackupPrivilege\|SeRestorePrivilege\|SeCreateTokenPrivilege\|SeLoadDriverPrivilege\|SeTakeOwnershipPrivilege\|SeDebugPrivilege"
```

### [SIDs](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#sids)

Check each SSID owned by a process.  
It could be interesting to list the processes using a privileges SID (and the processes using some service SID).

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.getsids.GetSIDs [--pid <pid>] #Get SIDs of processes
./vol.py -f file.dmp windows.getservicesids.GetServiceSIDs #Get the SID of services
```

### [Handles](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#handles)

Useful to know to which other files, keys, threads, processes... a **process has a handle** for (has opened)

vol3vol2

bash

```bash
vol.py -f file.dmp windows.handles.Handles [--pid <pid>]
```

### [DLLs](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#dlls)

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.dlllist.DllList [--pid <pid>] #List dlls used by each
./vol.py -f file.dmp windows.dumpfiles.DumpFiles --pid <pid> #Dump the .exe and dlls of the process in the current directory process
```

### [Strings per processes](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#strings-per-processes)

Volatility allows us to check which process a string belongs to.

vol3vol2

bash

```bash
strings file.dmp > /tmp/strings.txt
./vol.py -f /tmp/file.dmp windows.strings.Strings --strings-file /tmp/strings.txt
```

It also allows to search for strings inside a process using the yarascan module:

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.vadyarascan.VadYaraScan --yara-rules "https://" --pid 3692 3840 3976 3312 3084 2784
./vol.py -f file.dmp yarascan.YaraScan --yara-rules "https://"
```

### [UserAssist](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#userassist)

**Windows** keeps track of programs you run using a feature in the registry called **UserAssist keys**. These keys record how many times each program is executed and when it was last run.

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.registry.userassist.UserAssist
```

​

## [Services](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#services)

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.svcscan.SvcScan #List services
./vol.py -f file.dmp windows.getservicesids.GetServiceSIDs #Get the SID of services
```

## [Network](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#network)

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.netscan.NetScan
#For network info of linux use volatility2
```

## [Registry hive](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#registry-hive)

### [Print available hives](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#print-available-hives)

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.registry.hivelist.HiveList #List roots
./vol.py -f file.dmp windows.registry.printkey.PrintKey #List roots and get initial subkeys
```

### [Get a value](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#get-a-value)

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.registry.printkey.PrintKey --key "Software\Microsoft\Windows NT\CurrentVersion"
```

### [Dump](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#dump)

bash

```bash
#Dump a hive
volatility --profile=Win7SP1x86_23418 hivedump -o 0x9aad6148 -f file.dmp #Offset extracted by hivelist
#Dump all hives
volatility --profile=Win7SP1x86_23418 hivedump -f file.dmp
```

## [Filesystem](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#filesystem)

### [Mount](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#mount)

vol3vol2

bash

```bash
#See vol2
```

### [Scan/dump](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#scandump)

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.filescan.FileScan #Scan for files inside the dump
./vol.py -f file.dmp windows.dumpfiles.DumpFiles --physaddr <0xAAAAA> #Offset from previous command
```

### [Master File Table](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#master-file-table)

vol3vol2

bash

```bash
# I couldn't find any plugin to extract this information in volatility3
```

The **NTFS file system** uses a critical component known as the _master file table_ (MFT). This table includes at least one entry for every file on a volume, covering the MFT itself too. Vital details about each file, such as **size, timestamps, permissions, and actual data**, are encapsulated within the MFT entries or in areas external to the MFT but referenced by these entries. More details can be found in the [official documentation](https://docs.microsoft.com/en-us/windows/win32/fileio/master-file-table).

### [SSL Keys/Certs](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#ssl-keyscerts)

vol3vol2

bash

```bash
#vol3 allows to search for certificates inside the registry
./vol.py -f file.dmp windows.registry.certificates.Certificates
```

## [Malware](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#malware)

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.malfind.Malfind [--dump] #Find hidden and injected code, [dump each suspicious section]
#Malfind will search for suspicious structures related to malware
./vol.py -f file.dmp windows.driverirp.DriverIrp #Driver IRP hook detection
./vol.py -f file.dmp windows.ssdt.SSDT #Check system call address from unexpected addresses

./vol.py -f file.dmp linux.check_afinfo.Check_afinfo #Verifies the operation function pointers of network protocols
./vol.py -f file.dmp linux.check_creds.Check_creds #Checks if any processes are sharing credential structures
./vol.py -f file.dmp linux.check_idt.Check_idt #Checks if the IDT has been altered
./vol.py -f file.dmp linux.check_syscall.Check_syscall #Check system call table for hooks
./vol.py -f file.dmp linux.check_modules.Check_modules #Compares module list to sysfs info, if available
./vol.py -f file.dmp linux.tty_check.tty_check #Checks tty devices for hooks
```

### [Scanning with yara](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#scanning-with-yara)

Use this script to download and merge all the yara malware rules from github: [https://gist.github.com/andreafortuna/29c6ea48adf3d45a979a78763cdc7ce9](https://gist.github.com/andreafortuna/29c6ea48adf3d45a979a78763cdc7ce9)  
Create the _**rules**_ directory and execute it. This will create a file called _**malware_rules.yar**_ which contains all the yara rules for malware.

vol3vol2

bash

```bash
wget https://gist.githubusercontent.com/andreafortuna/29c6ea48adf3d45a979a78763cdc7ce9/raw/4ec711d37f1b428b63bed1f786b26a0654aa2f31/malware_yara_rules.py
mkdir rules
python malware_yara_rules.py
#Only Windows
./vol.py -f file.dmp windows.vadyarascan.VadYaraScan --yara-file /tmp/malware_rules.yar
#All
./vol.py -f file.dmp yarascan.YaraScan --yara-file /tmp/malware_rules.yar
```

## [MISC](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#misc)

### [External plugins](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#external-plugins)

If you want to use external plugins make sure that the folders related to the plugins are the first parameter used.

vol3vol2

bash

```bash
./vol.py --plugin-dirs "/tmp/plugins/" [...]
```

#### [Autoruns](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#autoruns)

Download it from [https://github.com/tomchop/volatility-autoruns](https://github.com/tomchop/volatility-autoruns)

```
 volatility --plugins=volatility-autoruns/ --profile=WinXPSP2x86 -f file.dmp autoruns
```

### [Mutexes](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#mutexes)

vol3vol2

```
./vol.py -f file.dmp windows.mutantscan.MutantScan
```

### [Symlinks](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#symlinks)

vol3vol2

bash

```bash
./vol.py -f file.dmp windows.symlinkscan.SymlinkScan
```

### [Bash](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#bash)

It's possible to **read from memory the bash history.** You could also dump the _.bash_history_ file, but it was disabled you will be glad you can use this volatility module

vol3vol2

```
./vol.py -f file.dmp linux.bash.Bash
```

### [TimeLine](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#timeline)

vol3vol2

bash

```bash
./vol.py -f file.dmp timeLiner.TimeLiner
```

### [Drivers](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#drivers)

vol3vol2

```
./vol.py -f file.dmp windows.driverscan.DriverScan
```

### [Get clipboard](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#get-clipboard)

bash

```bash
#Just vol2
volatility --profile=Win7SP1x86_23418 clipboard -f file.dmp
```

### [Get IE history](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#get-ie-history)

bash

```bash
#Just vol2
volatility --profile=Win7SP1x86_23418 iehistory -f file.dmp
```

### [Get notepad text](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#get-notepad-text)

bash

```bash
#Just vol2
volatility --profile=Win7SP1x86_23418 notepad -f file.dmp
```

### [Screenshot](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#screenshot)

bash

```bash
#Just vol2
volatility --profile=Win7SP1x86_23418 screenshot -f file.dmp
```

### [Master Boot Record (MBR)](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#master-boot-record-mbr)

bash

```bash
volatility --profile=Win7SP1x86_23418 mbrparser -f file.dmp
```

The **Master Boot Record (MBR)** plays a crucial role in managing the logical partitions of a storage medium, which are structured with different [file systems](https://en.wikipedia.org/wiki/File_system). It not only holds partition layout information but also contains executable code acting as a boot loader. This boot loader either directly initiates the OS's second-stage loading process (see [second-stage boot loader](https://en.wikipedia.org/wiki/Second-stage_boot_loader)) or works in harmony with the [volume boot record](https://en.wikipedia.org/wiki/Volume_boot_record) (VBR) of each partition. For in-depth knowledge, refer to the [MBR Wikipedia page](https://en.wikipedia.org/wiki/Master_boot_record).

## [References](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html#references)

- [https://andreafortuna.org/2017/06/25/volatility-my-own-cheatsheet-part-1-image-identification/](https://andreafortuna.org/2017/06/25/volatility-my-own-cheatsheet-part-1-image-identification/)
- [https://scudette.blogspot.com/2012/11/finding-kernel-debugger-block.html](https://scudette.blogspot.com/2012/11/finding-kernel-debugger-block.html)
- [https://or10nlabs.tech/cgi-sys/suspendedpage.cgi](https://or10nlabs.tech/cgi-sys/suspendedpage.cgi)
- [https://www.aldeid.com/wiki/Windows-userassist-keys](https://www.aldeid.com/wiki/Windows-userassist-keys) ​* [https://learn.microsoft.com/en-us/windows/win32/fileio/master-file-table](https://learn.microsoft.com/en-us/windows/win32/fileio/master-file-table)
- [https://answers.microsoft.com/en-us/windows/forum/all/uefi-based-pc-protective-mbr-what-is-it/0fc7b558-d8d4-4a7d-bae2-395455bb19aa](https://answers.microsoft.com/en-us/windows/forum/all/uefi-based-pc-protective-mbr-what-is-it/0fc7b558-d8d4-4a7d-bae2-395455bb19aa)

Learn & practice AWS Hacking:![](https://book.hacktricks.wiki/images/arte.png)[**HackTricks Training AWS Red Team Expert (ARTE)**](https://training.hacktricks.xyz/courses/arte)![](https://book.hacktricks.wiki/images/arte.png)  
Learn & practice GCP Hacking: ![](https://book.hacktricks.wiki/images/grte.png)[**HackTricks Training GCP Red Team Expert (GRTE)**](https://training.hacktricks.xyz/courses/grte)![](https://book.hacktricks.wiki/images/grte.png)

Support HackTricks

- [](https://github.com/sponsors/carlospolop)
- [](https://discord.gg/hRep4RUj7f)[](https://t.me/peass)[](https://twitter.com/hacktricks_live)
- [](https://github.com/carlospolop/hacktricks)[](https://github.com/carlospolop/hacktricks-cloud)

[Memory dump analysis](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/index.html "Previous chapter")[Partitions/File Systems/Carving](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/partitions-file-systems-carving/index.html "Next chapter")