

#### From "Module 1 - Discovery" 



Good search filters:  
● http.html:Apache  

>[!info]
>
>Here are some variations on the **http.** search filter : 
>
>1. **http.title**: Searches the title of web pages.
   > 
    - Example: `http.title:"Apache2 Ubuntu Default Page"`
>2. **http.favicon.hash**: Searches for web pages with a specific favicon hash.
 >
> - Example: `http.favicon.hash:123456789`
>3. **http.component**: Searches for specific components or technologies used on web pages.
  >  
    >- Example: `http.component:"WordPress"`
4. **http.status**: Searches for web pages with a specific HTTP status code.
    >
    >- Example: `http.status:200`
>5. **http.headers**: Searches for specific headers in the HTTP response.
  >  
   > - Example: `http.headers:"Server: Apache"`
>6. **http.html**: As you already know, searches the HTML content of web pages.
  >  
   > - Example: `http.html:Apache`
>7. **http.body**: Searches the body content of web pages.
  >  
  >  - Example: `http.body:"Welcome to Apache"`
>
>>[!Original]
>>
>>● hostname:nscc.ca  
>>● ssl.version:sslv2 -ssl.version:tlsv1,tlsv1.2,tlsv1.3  
>>● ssh port:22,3333  
>>● vuln:CVE-2014-0160 (paid filter)  
>>Make an account so you can use search filters

# Awesome Shodan Search Queries [![Awesome](https://camo.githubusercontent.com/3418ba3754faddfb88c5cbdc94c31ad670fc693c8caa59bc2806c9836acc04e4/68747470733a2f2f617765736f6d652e72652f62616467652e737667)](https://awesome.re/)

[](https://github.com/jakejarvis/awesome-shodan-queries#awesome-shodan-search-queries-)

Over time, I've collected an assortment of interesting, funny, and depressing search queries to plug into [Shodan](https://www.shodan.io/), the ([literal](https://www.vice.com/en_uk/article/9bvxmd/shodan-exposes-the-dark-side-of-the-net)) internet search engine. Some return facepalm-inducing results, while others return serious and/or ancient vulnerabilities in the wild.

[![](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/shodan.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/shodan.png)  
**[Most search filters require a Shodan account.](https://account.shodan.io/register)**

You can assume these queries only return unsecured/open instances when possible. For your own legal benefit, do not attempt to login (even with default passwords) if they aren't! Narrow down results by adding filters like `country:US` or `org:"Harvard University"` or `hostname:"nasa.gov"` to the end.

The world and its devices are quickly becoming more connected through the shiny new [Internet of ~~Things~~ Sh*t](https://motherboard.vice.com/en_us/topic/internet-of-shit) — and exponentially [more dangerous](https://blog.malwarebytes.com/101/2017/12/internet-things-iot-security-never/) as a result. To that end, I hope this list spreads awareness (and, quite frankly, pant-wetting fear) rather than harm.

**And as always, [discover and disclose responsibly](https://www.bugcrowd.com/resource/what-is-responsible-disclosure/)! 🤓**

---

### **Table of Contents**

[](https://github.com/jakejarvis/awesome-shodan-queries#table-of-contents)

- [Industrial Control Systems](https://github.com/jakejarvis/awesome-shodan-queries#industrial-control-systems)
- [Remote Desktop](https://github.com/jakejarvis/awesome-shodan-queries#remote-desktop)
- [Network Infrastructure](https://github.com/jakejarvis/awesome-shodan-queries#network-infrastructure)
- [Network Attached Storage (NAS)](https://github.com/jakejarvis/awesome-shodan-queries#network-attached-storage-nas)
- [Webcams](https://github.com/jakejarvis/awesome-shodan-queries#webcams)
- [Printers & Copiers](https://github.com/jakejarvis/awesome-shodan-queries#printers--copiers)
- [Home Devices](https://github.com/jakejarvis/awesome-shodan-queries#home-devices)
- [Random Stuff](https://github.com/jakejarvis/awesome-shodan-queries#random-stuff)

---

## Industrial Control Systems

[](https://github.com/jakejarvis/awesome-shodan-queries#industrial-control-systems)

### Samsung Electronic Billboards [🔎 →](https://www.shodan.io/search?query=%22Server%3A+Prismview+Player%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#samsung-electronic-billboards--)

```
"Server: Prismview Player"
```

[![Example: Electronic Billboards](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/billboard3.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/billboard3.png)

### Gas Station Pump Controllers [🔎 →](https://www.shodan.io/search?query=%22in-tank+inventory%22+port%3A10001)

[](https://github.com/jakejarvis/awesome-shodan-queries#gas-station-pump-controllers--)

```
"in-tank inventory" port:10001
```

[![Example: Gas Station Pump Inventories](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/7-11.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/7-11.png)

### Automatic License Plate Readers [🔎 →](https://www.shodan.io/search?query=P372+%22ANPR+enabled%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#automatic-license-plate-readers--)

```
P372 "ANPR enabled"
```

[![Example: Automatic License Plate Reader](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/plate-reader.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/plate-reader.png)

### Traffic Light Controllers / Red Light Cameras [🔎 →](https://www.shodan.io/search?query=mikrotik+streetlight)

[](https://github.com/jakejarvis/awesome-shodan-queries#traffic-light-controllers--red-light-cameras--)

```
mikrotik streetlight
```

### Voting Machines in the United States [🔎 →](https://www.shodan.io/search?query=%22voter+system+serial%22+country%3AUS)

[](https://github.com/jakejarvis/awesome-shodan-queries#voting-machines-in-the-united-states--)

```
"voter system serial" country:US
```

### Telcos Running [Cisco Lawful Intercept](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst6500/ios/12-2SX/lawful/intercept/book/65LIch1.html) Wiretaps [🔎 →](https://www.shodan.io/search?query=%22Cisco+IOS%22+%22ADVIPSERVICESK9_LI-M%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#telcos-running-cisco-lawful-intercept-wiretaps--)

```
"Cisco IOS" "ADVIPSERVICESK9_LI-M"
```

Wiretapping mechanism outlined by Cisco in [RFC 3924](https://tools.ietf.org/html/rfc3924):

> Lawful intercept is the lawfully authorized interception and monitoring of communications of an intercept subject. The term "intercept subject" [...] refers to the subscriber of a telecommunications service whose communications and/or intercept related information (IRI) has been lawfully authorized to be intercepted and delivered to some agency.

### Prison Pay Phones [🔎 →](https://www.shodan.io/search?query=%22%5B2J%5BH+Encartele+Confidential%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#prison-pay-phones--)

```
"[2J[H Encartele Confidential"
```

### [Tesla PowerPack](https://www.tesla.com/powerpack) Charging Status [🔎 →](https://www.shodan.io/search?query=http.title%3A%22Tesla+PowerPack+System%22+http.component%3A%22d3%22+-ga3ca4f2)

[](https://github.com/jakejarvis/awesome-shodan-queries#tesla-powerpack-charging-status--)

```
http.title:"Tesla PowerPack System" http.component:"d3" -ga3ca4f2
```

[![Example: Tesla PowerPack Charging Status](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/tesla.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/tesla.png)

### Electric Vehicle Chargers [🔎 →](https://www.shodan.io/search?query=%22Server%3A+gSOAP%2F2.8%22+%22Content-Length%3A+583%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#electric-vehicle-chargers--)

```
"Server: gSOAP/2.8" "Content-Length: 583"
```

### Maritime Satellites [🔎 →](https://www.shodan.io/search?query=%22Cobham+SATCOM%22+OR+%28%22Sailor%22+%22VSAT%22%29)

[](https://github.com/jakejarvis/awesome-shodan-queries#maritime-satellites--)

Shodan made a pretty sweet [Ship Tracker](https://shiptracker.shodan.io/) that maps ship locations in real time, too!

```
"Cobham SATCOM" OR ("Sailor" "VSAT")
```

[![Example: Maritime Satellites](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/sailor-vsat.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/sailor-vsat.png)

### Submarine Mission Control Dashboards [🔎 →](https://www.shodan.io/search?query=title%3A%22Slocum+Fleet+Mission+Control%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#submarine-mission-control-dashboards--)

```
title:"Slocum Fleet Mission Control"
```

### [CAREL PlantVisor](https://www.carel.com/product/plantvisor) Refrigeration Units [🔎 →](https://www.shodan.io/search?query=%22Server%3A+CarelDataServer%22+%22200+Document+follows%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#carel-plantvisor-refrigeration-units--)

```
"Server: CarelDataServer" "200 Document follows"
```

[![Example: CAREL PlantVisor Refrigeration Units](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/refrigeration.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/refrigeration.png)

### [Nordex Wind Turbine](http://www.nordex-online.com/en/products-services/wind-turbines.html) Farms [🔎 →](https://www.shodan.io/search?query=http.title%3A%22Nordex+Control%22+%22Windows+2000+5.0+x86%22+%22Jetty%2F3.1+%28JSP+1.1%3B+Servlet+2.2%3B+java+1.6.0_14%29%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#nordex-wind-turbine-farms--)

```
http.title:"Nordex Control" "Windows 2000 5.0 x86" "Jetty/3.1 (JSP 1.1; Servlet 2.2; java 1.6.0_14)"
```

### [C4 Max](https://www.mobile-devices.com/our-products/c4-max/) Commercial Vehicle GPS Trackers [🔎 →](https://www.shodan.io/search?query=%22%5B1m%5B35mWelcome+on+console%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#c4-max-commercial-vehicle-gps-trackers--)

```
"[1m[35mWelcome on console"
```

[![Example: C4 Max Vehicle GPS](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/c4max.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/c4max.png)

### [DICOM](https://www.dicomstandard.org/about/) Medical X-Ray Machines [🔎 →](https://www.shodan.io/search?query=%22DICOM+Server+Response%22+port%3A104)

[](https://github.com/jakejarvis/awesome-shodan-queries#dicom-medical-x-ray-machines--)

Secured by default, thankfully, but these 1,700+ machines still [have no business](https://documents.trendmicro.com/assets/rpt/rpt-securing-connected-hospitals.pdf) being on the internet.

```
"DICOM Server Response" port:104
```

### [GaugeTech](https://electroind.com/all-products/) Electricity Meters [🔎 →](https://www.shodan.io/search?query=%22Server%3A+EIG+Embedded+Web+Server%22+%22200+Document+follows%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#gaugetech-electricity-meters--)

```
"Server: EIG Embedded Web Server" "200 Document follows"
```

[![Example: GaugeTech Electricity Meters](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/power-gaugetech.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/power-gaugetech.png)

### Siemens Industrial Automation [🔎 →](https://www.shodan.io/search?query=%22Siemens%2C+SIMATIC%22+port%3A161)

[](https://github.com/jakejarvis/awesome-shodan-queries#siemens-industrial-automation--)

```
"Siemens, SIMATIC" port:161
```

### Siemens HVAC Controllers [🔎 →](https://www.shodan.io/search?query=%22Server%3A+Microsoft-WinCE%22+%22Content-Length%3A+12581%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#siemens-hvac-controllers--)

```
"Server: Microsoft-WinCE" "Content-Length: 12581"
```

### Door / Lock Access Controllers [🔎 →](https://www.shodan.io/search?query=%22HID+VertX%22+port%3A4070)

[](https://github.com/jakejarvis/awesome-shodan-queries#door--lock-access-controllers--)

```
"HID VertX" port:4070
```

### Railroad Management [🔎 →](https://www.shodan.io/search?query=%22log+off%22+%22select+the+appropriate%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#railroad-management--)

```
"log off" "select the appropriate"
```

---

## Remote Desktop

[](https://github.com/jakejarvis/awesome-shodan-queries#remote-desktop)

### Unprotected VNC [🔎 →](https://www.shodan.io/search?query=%22authentication+disabled%22+%22RFB+003.008%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#unprotected-vnc--)

```
"authentication disabled" "RFB 003.008"
```

[Shodan Images](https://images.shodan.io/) is a great supplementary tool to browse screenshots, by the way! [🔎 →](https://images.shodan.io/?query=%22authentication+disabled%22+%21screenshot.label%3Ablank)

[![Example: Unprotected VNC](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/vnc.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/vnc.png)  
_The first result right now. 😞_

### Windows RDP [🔎 →](https://www.shodan.io/search?query=%22%5Cx03%5Cx00%5Cx00%5Cx0b%5Cx06%5Cxd0%5Cx00%5Cx00%5Cx124%5Cx00%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#windows-rdp--)

99.99% are secured by a secondary Windows login screen.

```
"\x03\x00\x00\x0b\x06\xd0\x00\x00\x124\x00"
```

---

## Network Infrastructure

[](https://github.com/jakejarvis/awesome-shodan-queries#network-infrastructure)

### [Weave Scope](https://www.weave.works/oss/scope/) Dashboards [🔎 →](https://www.shodan.io/search?query=title%3A%22Weave+Scope%22+http.favicon.hash%3A567176827)

[](https://github.com/jakejarvis/awesome-shodan-queries#weave-scope-dashboards--)

Command-line access inside Kubernetes pods and Docker containers, and real-time visualization/monitoring of the entire infrastructure.

```
title:"Weave Scope" http.favicon.hash:567176827
```

[![Example: Weave Scope Dashboards](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/weavescope.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/weavescope.png)

### MongoDB [🔎 →](https://www.shodan.io/search?query=product%3AMongoDB+-authentication)

[](https://github.com/jakejarvis/awesome-shodan-queries#mongodb--)

Older versions were insecure by default. [Very scary.](https://krebsonsecurity.com/tag/mongodb/)

```
"MongoDB Server Information" port:27017 -authentication
```

[![Example: MongoDB](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/mongo.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/mongo.png)

### [Mongo Express](https://github.com/mongo-express/mongo-express) Web GUI [🔎 →](https://www.shodan.io/search?query=%22Set-Cookie%3A+mongo-express%3D%22+%22200+OK%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#mongo-express-web-gui--)

Like the [infamous phpMyAdmin](https://www.cvedetails.com/vulnerability-list/vendor_id-784/Phpmyadmin.html) but for MongoDB.

```
"Set-Cookie: mongo-express=" "200 OK"
```

[![Example: Mongo Express GUI](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/mongo-express.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/mongo-express.png)

### Jenkins CI [🔎 →](https://www.shodan.io/search?query=%22X-Jenkins%22+%22Set-Cookie%3A+JSESSIONID%22+http.title%3A%22Dashboard%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#jenkins-ci--)

```
"X-Jenkins" "Set-Cookie: JSESSIONID" http.title:"Dashboard"
```

[![Example: Jenkins CI](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/jenkins.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/jenkins.png)

### Docker APIs [🔎 →](https://www.shodan.io/search?query=%22Docker+Containers%3A%22+port%3A2375)

[](https://github.com/jakejarvis/awesome-shodan-queries#docker-apis--)

```
"Docker Containers:" port:2375
```

### Docker Private Registries [🔎 →](https://www.shodan.io/search?query=%22Docker-Distribution-Api-Version%3A+registry%22+%22200+OK%22+-gitlab)

[](https://github.com/jakejarvis/awesome-shodan-queries#docker-private-registries--)

```
"Docker-Distribution-Api-Version: registry" "200 OK" -gitlab
```

### [Pi-hole](https://pi-hole.net/) Open DNS Servers [🔎 →](https://www.shodan.io/search?query=%22dnsmasq-pi-hole%22+%22Recursion%3A+enabled%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#pi-hole-open-dns-servers--)

```
"dnsmasq-pi-hole" "Recursion: enabled"
```

### Already Logged-In as `root` via Telnet [🔎 →](https://www.shodan.io/search?query=%22root%40%22+port%3A23+-login+-password+-name+-Session)

[](https://github.com/jakejarvis/awesome-shodan-queries#already-logged-in-as-root-via-telnet--)

```
"root@" port:23 -login -password -name -Session
```

### Android Root Bridges [🔎 →](https://www.shodan.io/search?query=%22Android+Debug+Bridge%22+%22Device%22+port%3A5555)

[](https://github.com/jakejarvis/awesome-shodan-queries#android-root-bridges--)

A tangential result of Google's sloppy fractured update approach. 🙄 [More information here.](https://medium.com/p/root-bridge-how-thousands-of-internet-connected-android-devices-now-have-no-security-and-are-b46a68cb0f20)

```
"Android Debug Bridge" "Device" port:5555
```

### Lantronix Serial-to-Ethernet Adapter [Leaking Telnet Passwords](https://www.bleepingcomputer.com/news/security/thousands-of-serial-to-ethernet-devices-leak-telnet-passwords/) [🔎 →](https://www.shodan.io/search?query=Lantronix+password+port%3A30718+-secured)

[](https://github.com/jakejarvis/awesome-shodan-queries#lantronix-serial-to-ethernet-adapter-leaking-telnet-passwords--)

```
Lantronix password port:30718 -secured
```

### Citrix Virtual Apps [🔎 →](https://www.shodan.io/search?query=%22Citrix+Applications%3A%22+port%3A1604)

[](https://github.com/jakejarvis/awesome-shodan-queries#citrix-virtual-apps--)

```
"Citrix Applications:" port:1604
```

[![Example: Citrix Virtual Apps](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/citrix.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/citrix.png)

### Cisco Smart Install [🔎 →](https://www.shodan.io/search?query=%22smart+install+client+active%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#cisco-smart-install--)

[Vulnerable](https://2016.zeronights.ru/wp-content/uploads/2016/12/CiscoSmartInstall.v3.pdf) (kind of "by design," but especially when exposed).

```
"smart install client active"
```

### PBX IP Phone Gateways [🔎 →](https://www.shodan.io/search?query=PBX+%22gateway+console%22+-password+port%3A23)

[](https://github.com/jakejarvis/awesome-shodan-queries#pbx-ip-phone-gateways--)

```
PBX "gateway console" -password port:23
```

### [Polycom](https://www.polycom.com/hd-video-conferencing.html) Video Conferencing [🔎 →](https://www.shodan.io/search?query=http.title%3A%22-+Polycom%22+%22Server%3A+lighttpd%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#polycom-video-conferencing--)

```
http.title:"- Polycom" "Server: lighttpd"
```

Telnet Configuration: [🔎 →](https://www.shodan.io/search?query=%22Polycom+Command+Shell%22+-failed+port%3A23)

```
"Polycom Command Shell" -failed port:23
```

[![Example: Polycom Video Conferencing](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/polycom.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/polycom.png)

### [Bomgar Help Desk](https://www.beyondtrust.com/remote-support/integrations) Portal [🔎 →](https://www.shodan.io/search?query=%22Server%3A+Bomgar%22+%22200+OK%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#bomgar-help-desk-portal--)

```
"Server: Bomgar" "200 OK"
```

### Intel Active Management [CVE-2017-5689](https://www.exploit-db.com/exploits/43385) [🔎 →](https://www.shodan.io/search?query=%22Intel%28R%29+Active+Management+Technology%22+port%3A623%2C664%2C16992%2C16993%2C16994%2C16995)

[](https://github.com/jakejarvis/awesome-shodan-queries#intel-active-management-cve-2017-5689--)

```
"Intel(R) Active Management Technology" port:623,664,16992,16993,16994,16995
```

### HP iLO 4 [CVE-2017-12542](https://nvd.nist.gov/vuln/detail/CVE-2017-12542) [🔎 →](https://www.shodan.io/search?query=HP-ILO-4+%21%22HP-ILO-4%2F2.53%22+%21%22HP-ILO-4%2F2.54%22+%21%22HP-ILO-4%2F2.55%22+%21%22HP-ILO-4%2F2.60%22+%21%22HP-ILO-4%2F2.61%22+%21%22HP-ILO-4%2F2.62%22+%21%22HP-iLO-4%2F2.70%22+port%3A1900)

[](https://github.com/jakejarvis/awesome-shodan-queries#hp-ilo-4-cve-2017-12542--)

```
HP-ILO-4 !"HP-ILO-4/2.53" !"HP-ILO-4/2.54" !"HP-ILO-4/2.55" !"HP-ILO-4/2.60" !"HP-ILO-4/2.61" !"HP-ILO-4/2.62" !"HP-iLO-4/2.70" port:1900
```

### Outlook Web Access:

[](https://github.com/jakejarvis/awesome-shodan-queries#outlook-web-access)

#### Exchange 2007 [🔎 →](https://www.shodan.io/search?query=%22x-owa-version%22+%22IE%3DEmulateIE7%22+%22Server%3A+Microsoft-IIS%2F7.0%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#exchange-2007--)

```
"x-owa-version" "IE=EmulateIE7" "Server: Microsoft-IIS/7.0"
```

[![Example: OWA for Exchange 2007](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/owa2007.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/owa2007.png)

#### Exchange 2010 [🔎 →](https://www.shodan.io/search?query=%22x-owa-version%22+%22IE%3DEmulateIE7%22+http.favicon.hash%3A442749392)

[](https://github.com/jakejarvis/awesome-shodan-queries#exchange-2010--)

```
"x-owa-version" "IE=EmulateIE7" http.favicon.hash:442749392
```

[![Example: OWA for Exchange 2010](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/owa2010.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/owa2010.png)

#### Exchange 2013 / 2016 [🔎 →](https://www.shodan.io/search?query=%22X-AspNet-Version%22+http.title%3A%22Outlook%22+-%22x-owa-version%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#exchange-2013--2016--)

```
"X-AspNet-Version" http.title:"Outlook" -"x-owa-version"
```

[![Example: OWA for Exchange 2013/2016](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/owa2013.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/owa2013.png)

### Lync / Skype for Business [🔎 →](https://www.shodan.io/search?query=%22X-MS-Server-Fqdn%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#lync--skype-for-business--)

```
"X-MS-Server-Fqdn"
```

---

## Network Attached Storage (NAS)

[](https://github.com/jakejarvis/awesome-shodan-queries#network-attached-storage-nas)

### SMB (Samba) File Shares [🔎 →](https://www.shodan.io/search?query=%22Authentication%3A+disabled%22+port%3A445)

[](https://github.com/jakejarvis/awesome-shodan-queries#smb-samba-file-shares--)

Produces ~500,000 results...narrow down by adding "Documents" or "Videos", etc.

```
"Authentication: disabled" port:445
```

Specifically domain controllers: [🔎 →](https://www.shodan.io/search?query=%22Authentication%3A+disabled%22+NETLOGON+SYSVOL+-unix+port%3A445)

```
"Authentication: disabled" NETLOGON SYSVOL -unix port:445
```

Concerning [default network shares of QuickBooks](https://quickbooks.intuit.com/learn-support/en-us/help-articles/set-up-folder-and-windows-access-permissions-to-share-company/01/201880) files: [🔎 →](https://www.shodan.io/search?query=%22Authentication%3A+disabled%22+%22Shared+this+folder+to+access+QuickBooks+files+OverNetwork%22+-unix+port%3A445)

```
"Authentication: disabled" "Shared this folder to access QuickBooks files OverNetwork" -unix port:445
```

### FTP Servers with Anonymous Login [🔎 →](https://www.shodan.io/search?query=%22220%22+%22230+Login+successful.%22+port%3A21)

[](https://github.com/jakejarvis/awesome-shodan-queries#ftp-servers-with-anonymous-login--)

```
"220" "230 Login successful." port:21
```

### Iomega / LenovoEMC NAS Drives [🔎 →](https://www.shodan.io/search?query=%22Set-Cookie%3A+iomega%3D%22+-%22manage%2Flogin.html%22+-http.title%3A%22Log+In%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#iomega--lenovoemc-nas-drives--)

```
"Set-Cookie: iomega=" -"manage/login.html" -http.title:"Log In"
```

[![Example: Iomega / LenovoEMC NAS Drives](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/iomega.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/iomega.png)

### Buffalo TeraStation NAS Drives [🔎 →](https://www.shodan.io/search?query=Redirecting+sencha+port%3A9000)

[](https://github.com/jakejarvis/awesome-shodan-queries#buffalo-terastation-nas-drives--)

```
Redirecting sencha port:9000
```

[![Example: Buffalo TeraStation NAS Drives](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/buffalo.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/buffalo.png)

### Logitech Media Servers [🔎 →](https://www.shodan.io/search?query=%22Server%3A+Logitech+Media+Server%22+%22200+OK%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#logitech-media-servers--)

```
"Server: Logitech Media Server" "200 OK"
```

[![Example: Logitech Media Servers](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/logitech.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/logitech.png)

### [Plex](https://www.plex.tv/) Media Servers [🔎 →](https://www.shodan.io/search?query=%22X-Plex-Protocol%22+%22200+OK%22+port%3A32400)

[](https://github.com/jakejarvis/awesome-shodan-queries#plex-media-servers--)

```
"X-Plex-Protocol" "200 OK" port:32400
```

### [Tautulli / PlexPy](https://github.com/Tautulli/Tautulli) Dashboards [🔎 →](https://www.shodan.io/search?query=%22CherryPy%2F5.1.0%22+%22%2Fhome%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#tautulli--plexpy-dashboards--)

```
"CherryPy/5.1.0" "/home"
```

[![Example: PlexPy / Tautulli Dashboards](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/plexpy.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/plexpy.png)

---

## Webcams

[](https://github.com/jakejarvis/awesome-shodan-queries#webcams)

Example images not necessary. 🤦

### Yawcams [🔎 →](https://www.shodan.io/search?query=%22Server%3A+yawcam%22+%22Mime-Type%3A+text%2Fhtml%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#yawcams--)

```
"Server: yawcam" "Mime-Type: text/html"
```

### webcamXP/webcam7 [🔎 →](https://www.shodan.io/search?query=%28%22webcam+7%22+OR+%22webcamXP%22%29+http.component%3A%22mootools%22+-401)

[](https://github.com/jakejarvis/awesome-shodan-queries#webcamxpwebcam7--)

```
("webcam 7" OR "webcamXP") http.component:"mootools" -401
```

### Android IP Webcam Server [🔎 →](https://www.shodan.io/search?query=%22Server%3A+IP+Webcam+Server%22+%22200+OK%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#android-ip-webcam-server--)

```
"Server: IP Webcam Server" "200 OK"
```

### Security DVRs [🔎 →](https://www.shodan.io/search?query=html%3A%22DVR_H264+ActiveX%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#security-dvrs--)

```
html:"DVR_H264 ActiveX"
```

---

## Printers & Copiers:

[](https://github.com/jakejarvis/awesome-shodan-queries#printers--copiers)

### HP Printers [🔎 →](https://www.shodan.io/search?query=%22Serial+Number%3A%22+%22Built%3A%22+%22Server%3A+HP+HTTP%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#hp-printers--)

```
"Serial Number:" "Built:" "Server: HP HTTP"
```

[![Example: HP Printers](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/hp.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/hp.png)

### Xerox Copiers/Printers [🔎 →](https://www.shodan.io/search?query=ssl%3A%22Xerox+Generic+Root%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#xerox-copiersprinters--)

```
ssl:"Xerox Generic Root"
```

[![Example: Xerox Copiers/Printers](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/xerox.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/xerox.png)

### Epson Printers [🔎 →](https://www.shodan.io/search?query=%22SERVER%3A+EPSON_Linux+UPnP%22+%22200+OK%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#epson-printers--)

```
"SERVER: EPSON_Linux UPnP" "200 OK"
```

```
"Server: EPSON-HTTP" "200 OK"
```

[![Example: Epson Printers](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/epson.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/epson.png)

### Canon Printers [🔎 →](https://www.shodan.io/search?query=%22Server%3A+KS_HTTP%22+%22200+OK%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#canon-printers--)

```
"Server: KS_HTTP" "200 OK"
```

```
"Server: CANON HTTP Server"
```

[![Example: Canon Printers](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/canon.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/canon.png)

---

## Home Devices

[](https://github.com/jakejarvis/awesome-shodan-queries#home-devices)

### Yamaha Stereos [🔎 →](https://www.shodan.io/search?query=%22Server%3A+AV_Receiver%22+%22HTTP%2F1.1+406%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#yamaha-stereos--)

```
"Server: AV_Receiver" "HTTP/1.1 406"
```

[![Example: Yamaha Stereos](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/yamaha.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/yamaha.png)

### Apple AirPlay Receivers [🔎 →](https://www.shodan.io/search?query=%22%5Cx08_airplay%22+port%3A5353)

[](https://github.com/jakejarvis/awesome-shodan-queries#apple-airplay-receivers--)

Apple TVs, HomePods, etc.

```
"\x08_airplay" port:5353
```

### Chromecasts / Smart TVs [🔎 →](https://www.shodan.io/search?query=%22Chromecast%3A%22+port%3A8008)

[](https://github.com/jakejarvis/awesome-shodan-queries#chromecasts--smart-tvs--)

```
"Chromecast:" port:8008
```

### [Crestron Smart Home](https://www.crestron.com/Products/Market-Solutions/Residential-Solutions) Controllers [🔎 →](https://www.shodan.io/search?query=%22Model%3A+PYNG-HUB%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#crestron-smart-home-controllers--)

```
"Model: PYNG-HUB"
```

---

## Random Stuff

[](https://github.com/jakejarvis/awesome-shodan-queries#random-stuff)

### OctoPrint 3D Printer Controllers [🔎 →](https://www.shodan.io/search?query=title%3A%22OctoPrint%22+-title%3A%22Login%22+http.favicon.hash%3A1307375944)

[](https://github.com/jakejarvis/awesome-shodan-queries#octoprint-3d-printer-controllers--)

```
title:"OctoPrint" -title:"Login" http.favicon.hash:1307375944
```

[![Example: OctoPrint 3D Printers](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/octoprint.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/octoprint.png)

### Etherium Miners [🔎 →](https://www.shodan.io/search?query=%22ETH+-+Total+speed%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#etherium-miners--)

```
"ETH - Total speed"
```

[![Example: Etherium Miners](https://github.com/jakejarvis/awesome-shodan-queries/raw/main/screenshots/eth.png)](https://github.com/jakejarvis/awesome-shodan-queries/blob/main/screenshots/eth.png)

### Apache Directory Listings [🔎 →](https://www.shodan.io/search?query=http.title%3A%22Index+of+%2F%22+http.html%3A%22.pem%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#apache-directory-listings--)

Substitute `.pem` with any extension or a filename like `phpinfo.php`.

```
http.title:"Index of /" http.html:".pem"
```

### Misconfigured WordPress [🔎 →](https://www.shodan.io/search?query=http.html%3A%22*+The+wp-config.php+creation+script+uses+this+file%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#misconfigured-wordpress--)

Exposed [`wp-config.php`](https://github.com/WordPress/WordPress/blob/master/wp-config-sample.php) files containing database credentials.

```
http.html:"* The wp-config.php creation script uses this file"
```

### Too Many Minecraft Servers [🔎 →](https://www.shodan.io/search?query=%22Minecraft+Server%22+%22protocol+340%22+port%3A25565)

[](https://github.com/jakejarvis/awesome-shodan-queries#too-many-minecraft-servers--)

```
"Minecraft Server" "protocol 340" port:25565
```

### Literally [Everything](https://www.vox.com/2014/12/22/7435625/north-korea-internet) in North Korea 🇰🇵 [🔎 →](https://www.shodan.io/search?query=net%3A175.45.176.0%2F22%2C210.52.109.0%2F24)

[](https://github.com/jakejarvis/awesome-shodan-queries#literally-everything-in-north-korea---)

```
net:175.45.176.0/22,210.52.109.0/24,77.94.35.0/24
```

### TCP Quote of the Day [🔎 →](https://www.shodan.io/search?query=port%3A17+product%3A%22Windows+qotd%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#tcp-quote-of-the-day--)

Port 17 ([RFC 865](https://tools.ietf.org/html/rfc865)) has a [bizarre history](https://en.wikipedia.org/wiki/QOTD)...

```
port:17 product:"Windows qotd"
```

### Find a Job Doing This! 👩‍💼 [🔎 →](https://www.shodan.io/search?query=%22X-Recruiting%3A%22)

[](https://github.com/jakejarvis/awesome-shodan-queries#find-a-job-doing-this---)

```
"X-Recruiting:"
```

# Shodan Cheat Sheet

 less than 1 minute read

Shodan’s a search engine which helps find systems on the internet. It’s a great resource to provide passive reconnaissance on a target or as a measuring tool for how widespread a configuration or device is.

![Shodan Banner](https://thor-sec.com/assets/images/shodan_banner.jpg)

# Basic Search Filters

---

**port:** `Search by specific port`  
**net:** `Search based on an IP/CIDR`  
**hostname:** `Locate devices by hostname`  
**os:** `Search by Operating System`  
**city:** `Locate devices by city`  
**country:** `Locate devices by country`  
**geo:** `Locate devices by coordinates`  
**org:** `Search by organization`  
**before/after:** `Timeframe delimiter`  
**hash:** `Search based on banner hash`  
**has_screenshot:true** `Filter search based on a screenshot being present`  
**title:** `Search based on text within the title`


# Shodan Cheat Sheet by [sir_slammington](http://www.cheatography.com/sir-slammington/)

Shodan is a search engine that specializes in returning results for public facing devices on the Internet. The CLI tool allows you to make requests using an API to obtain results without using the Web UI.

|   |   |   |   |   |
|---|---|---|---|---|
|### Common General Search Filters<br><br>\|   \|   \|<br>\|---\|---\|<br>\|**ip:**\|Filter results by specific IP address.\|<br>\|**asn:**\|Filter results by specific ASN ID.\|<br>\|**hostname:**\|Filter results by specific hostname.\|<br>\|**port:**\|Filter results by specific port number of service.\|<br>\|**net:**\|Filter results from specified CIDR block.\|<br>\|**isp:**\|Filter results by devices assigned a particular address (space) from a specified ISP.\|<br>\|**city:**\|Filter results by specific city.\|<br>\|**country:**\|Filter results by specific two-digit country code.\|<br>\|**os:**\|Filter results by particular OS.\|<br>\|**product:**\|Filter results by particular software.\|<br>\|**version:**\|Filter results by specified version of software.\|<br><br>### Common Premium API Search Filters<br><br>\|   \|   \|<br>\|---\|---\|<br>\|**vuln:**\|Filter results by particular vulner­ability ID (commonly CVE).\|<br>\|**tag:**\|Filter results by tags on device.\|<br><br>### HTTP Filters<br><br>\|   \|   \|<br>\|---\|---\|<br>\|**http.c­omp­onent:**\|Filter results by a particular web techno­logy.\|<br>\|**http.s­tatus:**\|Filter results by specific status code.\|<br>\|**http.html:**\|Filter results by strings found in HTML of files served.\|<br>\|**http.t­itle:**\|Filter results by string found in title of web pages served.\|||### Common CLI Commands<br><br>\|   \|   \|<br>\|---\|---\|<br>\|**count**\|Returns the number of results for a search.\|<br>\|**domain**\|View all available inform­ation for a domain.\|<br>\|**download**\|Download search results and save them in a compressed JSON file.\|<br>\|**honeyscore**\|Check whether the IP is a honeypot or not.\|<br>\|**host**\|View all available inform­ation for an IP address.\|<br>\|**parse**\|Extract inform­ation out of compressed JSON files.\|<br>\|**scan**\|Scan an IP/ netblock using Shodan.\|<br>\|**search**\|Search the Shodan database.\|<br><br>### Common CLI Search Fields<br><br>\|   \|   \|<br>\|---\|---\|<br>\|**ip_str**\|   \|<br>\|**port**\|   \|<br>\|**org**\|   \|<br>\|**hostnames**\|   \|<br>\|**os**\|   \|<br>\|**country**\|   \|<br>\|**city**\|   \|<br><br>These will display their values upon a search, but won't provide statis­tics.<br><br>### Common CLI Stats Facets<br><br>\|   \|   \|<br>\|---\|---\|<br>\|**asn**\|   \|<br>\|**city**\|   \|<br>\|**country**\|   \|<br>\|**cloud.p­ro­vider**\|   \|<br>\|**cloud.s­ervice**\|   \|<br>\|**device**\|   \|<br>\|**domain**\|   \|<br>\|**ip**\|   \|<br>\|**org**\|   \|<br>\|**os**\|   \|<br>\|**version**\|   \|<br><br>These will return statis­tical inform­ation about a given series of devices found on the public facing Internet. For example, it could be used to return the most common version found among devices running MariaDB in a particular ASN.||### Use Case Examples<br><br>\|   \|   \|   \|<br>\|---\|---\|---\|<br>\|**host: 8.8.8.8**\|**shodan host 8.8.8.8**\|Display inform­ation about a Google's public DNS.\|<br>\|**asn:15169 produc­t:mysql**\|**shodan stats asn:15169 produc­t:mysql**\|Show inform­ation about devices within Google's ASN that run MySQL.\|<br>\|**microsoft iis 6.0**\|**shodan search --fields ip_str­,po­rt,­org­,ho­stnames microsoft iis 6.0**\|Detect IIS servers running on 6.0.\|<br>\|**Navigate to [https:­//h­one­ysc­ore.sh­oda­n.io/](https://honeyscore.shodan.io/) and enter target IP.**\|**shodan honeyscore [TARGET]**\|Detect if given target is a honeypot or not.\|<br><br>Column one is the search you would perform in the Web UI. Column two is the search you would perform using the CLI utility, and the third column is an explan­ation of the search.|

 [recon](https://cheatography.com/tag/recon/)      [osint](https://cheatography.com/tag/osint/)      [shodan](https://cheatography.com/tag/shodan/)


## What is Shodan?

Shodan is a search engine but very different from regular search engines like Google, Yahoo, Bing, etc., which search the web for standard websites. Shodan was explicitly designed and developed to pull information about IoT devices connected to the internet. It ranks critical information about various devices that the regular browser user would never see. Some of the things that you can find on the internet with Shodan include:

- Cameras (e.g CCTVs,Webcams)
- Routers and Devices
- Baby monitors
- Maritime satellites
- Prison payphones
- Traffic light systems
- Water treatment facilities
- Nuclear power plants, and much more

Don't freak out from the above examples and run hiding in a bunker. Yes, Shodan can provide you with publicly accessible information about a router, a server, or a nuclear plant, but that doesn't mean anybody with an active internet connection will now have full access to the device or system. However, there is also a catch! This publicly accessible information can also be very critical. For example, Hackers will indeed have access to these devices if you have a webcam or router connected to the internet and still use the default login username and password. That is why security measures like strong password, two-factor authentication, the use of Firewalls, and strict security protocols is highly recommended. You will understand this better when we start looking at some practical examples with Shodan.

## How does Shodan Work?

To understand how Shodan works, let's first look at how regular search engines like Google and Yahoo operate. Google uses automated programs called crawlers that crawl the world wide web looking for any new or updated pages. It captures the page URLs (page addresses) and stores them in a list where it will look up for them later when a user makes a search request.

Shodan works similarly to Google. It crawls the internet using a global network of computers and servers requesting connections to every IP address that appears on the internet. It indexes all the pieces of information received from these IPs. Of course, not all IP addresses will return relevant information. Still, most of them respond with banners that contain metadata information about the devices using these IPs to connect to the internet.

Some of the information includes:

- Device name: refers to the device's name (it's set as Hostname)—for example, Cisco router or Samsung Galaxy A32.
- IP address: This is a unique code used to identify a device on the internet. For example, 206.189.189.202
- Location: The country, city, or any other geographical identifier where this device is located.
- Organization: This refers to who owns the "IP Space."
- Ports:

Other additional information that you can find include:

- Default login and password
- Services and Software running on the device
- Make and model
- Web technologies

## Getting Started with Shodan

There are two main ways you can use the Shodan search engine:

- The Browser
- The Command-line

This post will give you a detailed guide on using both methods.

## 1. Using Shodan on the Browser

That is far one of the most utilized options by security professionals. To get started, launch your favorite browser and enter the URL [shodan.io](https://www.shodan.io/).

bash

https://www.shodan.io/

You should see a window similar to the image below. Like Google, you can type anything you want to look upon the Search Box above.

[![Shodan](https://www.golinuxcloud.com/wp-content/uploads/Shodan.png "Complete Shodan Tutorial | The Search Engine for Hackers")](https://www.golinuxcloud.com/wp-content/uploads/Shodan.png)

Let's do a simple search like "webcams" and see what Shodan will give us.

[![Webcams](https://www.golinuxcloud.com/wp-content/uploads/Webcams.png "Complete Shodan Tutorial | The Search Engine for Hackers")](https://www.golinuxcloud.com/wp-content/uploads/Webcams.png)

We got 181 results from different locations from the image above, with the United States having the highest number. You will also notice that the search results are not similar to that with Google or Yahoo, where you get the domains and page URLs. With Shodan, you will get an IP of that particular device.

On the left-hand side, you will see information like the top geographical location of these webcams, the top ports running on these IPs, a list of Services and Software running on the devices, etc. You can access any of these webcams by clicking on any IPs listed.

We were lucky enough to get a camera doing a live stream in our case. See the image below.

[![Live Stream Camera](https://www.golinuxcloud.com/wp-content/uploads/Live-Stream-Camera.png "Complete Shodan Tutorial | The Search Engine for Hackers")](https://www.golinuxcloud.com/wp-content/uploads/Live-Stream-Camera.png)

After clicking on this IP, we saw that it has services running on two ports - 7777 and 9000. When we tried accessing these services on the web, `[the_ip]:7777` it gave us a login interface which I believe is access to the control panel of the camera while `[the_ip]:9000` enabling us to view the live stream taken by the camera.

Up to this point, you can now see how much critical information you can get with Shodan. Shodan is a powerful utility used by security professionals to ensure no essential information is put to the public internet. Another exciting search we can perform is _"Default password."_

[![Default password](https://www.golinuxcloud.com/wp-content/uploads/Default-password.png "Complete Shodan Tutorial | The Search Engine for Hackers")](https://www.golinuxcloud.com/wp-content/uploads/Default-password.png)

From the image above, we can see some devices still use the default username and password like:

- Username= "cisco"
- Password: "cisco"
- Username: "admin"
- Password: "1234"

### Using Filters

NOTE:

You will need to create an account with Shodan to use search filters.

Like Google, Shodan also enables us to use filters to get targeted results. For example, if we only wanted to get Webcams located in the United States, we can use the search filter below.

bash

webcams country:"US"

[![Search Filters](https://www.golinuxcloud.com/wp-content/uploads/Search-Filters.png "Complete Shodan Tutorial | The Search Engine for Hackers")](https://www.golinuxcloud.com/wp-content/uploads/Search-Filters.png)

Other basic Search filters you can use include:

- City: Get results in a particular city.
- Country: Get results in a specific country.
- Hostname: Get values matching a particular hostname.
- Geo: You can also use coordinates targeted results.
- Net: Get results based on IP or CIDR
- OS: Get results of devices running a particular OS.
- Port: Get results with particular ports open.
- After/ Before: Get the results within a specified timeframe.

Let's look at other search filters we can use:

Find Apache servers in New York

bash

apache city: "New York"

Find Nginx servers in the US

bash

nginx country:“DE”

Find Cisco devices on a particular subnet

bash

cisco net:“216.219.143.0/24”

Up to this point, I believe you now have a good understanding of using Shodan on the browser. Let's now look at how we can use Shodan on the command line.

## 2. Using Shodan Command line

To get started, launch the Terminal and run the command below.

bash

easy_install shodan

**Tip**: If you get an error message like easy_install: command not found, don't panic. Use the commands below to install Shodan.

bash

sudo apt install python3-pip
sudo pip3 install shodan

[![Install Shodan](https://www.golinuxcloud.com/wp-content/uploads/Install-Shodan.png "Complete Shodan Tutorial | The Search Engine for Hackers")](https://www.golinuxcloud.com/wp-content/uploads/Install-Shodan.png)

When done, you need to initialize Shodan by executing the command below.

bash

shodan init YOUR_API_KEY

HINT:

You can get your API key by clicking on your account after logging in. Alternatively, if you are logged in, you can open another tab and type the URL `https://account.shodan.io/`.

[![Initialize Shodan](https://www.golinuxcloud.com/wp-content/uploads/Initialize-Shodan.png "Complete Shodan Tutorial | The Search Engine for Hackers")](https://www.golinuxcloud.com/wp-content/uploads/Initialize-Shodan.png)

To get started with Shodan on the command line, run the -help command as shown below.

bash

shodan --help
or
shodan -h

[![Shodan Help](https://www.golinuxcloud.com/wp-content/uploads/Shodan-Help.png "Complete Shodan Tutorial | The Search Engine for Hackers")](https://www.golinuxcloud.com/wp-content/uploads/Shodan-Help.png)

Unlike using the browser, the CLI method can be pretty technical. However, with regular practice, you will be able to execute commands and search queries without much hustle.

Let's look at some search queries and their syntax.

To view your external IP address:

bash

shodan myip

Get the total number of open port 22 ports in the US.

bash

shodan count port:22 country:US

Get all the information you need about a particular domain.

bash

shodan domain [yourdomain]
e.g
shodan domain example.com

You can read more about using Shodan on the command line on their [official blog](https://cli.shodan.io/).

## Final Thoughts!

Up to this point, we believe you can now comfortably run Shodan on your system and check for vulnerabilities on your IoT devices. If you are h=jsut getting started, we recommend using the browser option until you are well acquainted enough to migrate to the command line. Additionally, it would be great to note that some advanced features on Shodan require a subscription fee. You can learn more about this by visiting their their [Pricing page](https://account.shodan.io/billing).

Do you have any queries or comments regarding this post? If yes! Please don't hesitate to leave a comment below.

![Deepak Prasad](https://www.golinuxcloud.com/wp-content/uploads/1545100445410-150x150.jpg)

Deepak Prasad

He is the founder of GoLinuxCloud and brings over a decade of expertise in Linux, Python, Go, Laravel, DevOps, Kubernetes, Git, Shell scripting, OpenShift, AWS, Networking, and Security. With extensive experience, he excels in various domains, from development to DevOps, Networking, and Security, ensuring robust and efficient solutions for diverse projects. You can connect with him on his [LinkedIn](https://www.linkedin.com/in/deep27ak/) profile.

