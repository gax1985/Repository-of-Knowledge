




We have two types of **Information Gathering** :



## Passive Recon

>[!question]
>
>What is **Passive Reconnaissance**?
>
>>[!answer]
>>
>>**Passive reconnaissance** involves gathering information about a target without directly interacting with the target system. This means that the attacker does not leave any trace or alert the target of their activities. The goal is to collect as much information as possible without being detected.
>>

**Examples of Passive Reconnaissance:**

1. **WHOIS Lookup:** Checking domain registration details to find information about the domain owner, contact information, and server details.
   


>[!link]
>
>https://www.whois.com/whois/

### Example of a WHOIS Inquiry
# nscc.ns.ca

``
Updated 4 days ago

Domain Information

Domain:

nscc.ns.ca

Registrar:

Bell Canada

Registered On:

2000-10-31

Expires On:

2025-01-25

Updated On:

2024-03-10

Status:

ok

Name Servers:

dns-nb00.aliant.net  
dns-nb01.aliant.net  
dns-ns00.aliant.net  
dns-on01.aliant.net  
dns-qc02.aliant.net

Registrant Contact

Name:

Nova Scotia Community College

Street:

29 Acadia Ave

City:

Stellarton

State:

NS

Postal Code:

B0K1S0

Country:

CA

Phone:

+1.9024916701

Fax:

+1.9024914825

Email:

![email](https://www.whois.com/eimg/f/16/f16d9c64267110a9a2cd395db6dc098e53581cb2.png)@nscc.ca

Administrative Contact

Name:

Graham MacDougall

Organization:

Nova Scotia Community College

Street:

Nova Scotia Community College, 29 Acadia Avenue

City:

Stellarton

State:

NS

Postal Code:

B0K1S0

Country:

CA

Phone:

+1.9024916701

Fax:

+1.9024914825

Email:

![email](https://www.whois.com/eimg/f/16/f16d9c64267110a9a2cd395db6dc098e53581cb2.png)@nscc.ca

Technical Contact

Name:

Adrian Cassidy

Organization:

Nova Scotia Community College

Street:

Nova Scotia Community College, 5685 Leeds Street

City:

Halifax

State:

NS

Postal Code:

B3J2X1

Country:

CA

Phone:

+1.9024916725

Fax:

+1.9024914831

Email:

![email](https://www.whois.com/eimg/f/93/f93d6eedaf1c66e37283063443540b1a6ad238ce.png)@nscc.ca

Raw Whois Data

Domain Name: nscc.ns.ca
Registry Domain ID: D24858-CIRA
Registrar WHOIS Server: whois.ca.fury.ca
Registrar URL: www.bellaliant.net
Updated Date: 2024-03-10T05:23:02Z
Creation Date: 2000-10-31T03:22:49Z
Registry Expiry Date: 2025-01-25T05:00:00Z
Registrar: Bell Canada
Registrar IANA ID: not applicable
Registrar Abuse Contact Email: ![email](https://www.whois.com/eimg/9/12/912856881c68d1fc0af0f6c5eab70c59da3f3b8a.png)@bell.ca
Registrar Abuse Contact Phone: +1.4163531106
Domain Status: ok https://icann.org/epp#ok
Registry Registrant ID: R22198-CIRA
Registrant Name: Nova Scotia Community College
Registrant Organization:
Registrant Street: 29 Acadia Ave
Registrant City: Stellarton
Registrant State/Province: NS
Registrant Postal Code: B0K1S0
Registrant Country: CA
Registrant Phone: +1.9024916701
Registrant Phone Ext:
Registrant Fax: +1.9024914825
Registrant Fax Ext:
Registrant Email: ![email](https://www.whois.com/eimg/f/16/f16d9c64267110a9a2cd395db6dc098e53581cb2.png)@nscc.ca
Registry Admin ID: C885051-CIRA
Admin Name: Graham MacDougall
Admin Organization: Nova Scotia Community College
Admin Street: Nova Scotia Community College, 29 Acadia Avenue
Admin City: Stellarton
Admin State/Province: NS
Admin Postal Code: B0K1S0
Admin Country: CA
Admin Phone: +1.9024916701
Admin Phone Ext:
Admin Fax: +1.9024914825
Admin Fax Ext:
Admin Email: ![email](https://www.whois.com/eimg/f/16/f16d9c64267110a9a2cd395db6dc098e53581cb2.png)@nscc.ca
Registry Tech ID: C885052-CIRA
Tech Name: Adrian Cassidy
Tech Organization: Nova Scotia Community College
Tech Street: Nova Scotia Community College, 5685 Leeds Street 
Tech City: Halifax
Tech State/Province: NS
Tech Postal Code: B3J2X1
Tech Country: CA
Tech Phone: +1.9024916725
Tech Phone Ext:
Tech Fax: +1.9024914831
Tech Fax Ext:
Tech Email: ![email](https://www.whois.com/eimg/f/93/f93d6eedaf1c66e37283063443540b1a6ad238ce.png)@nscc.ca
Registry Billing ID:
Billing Name:
Billing Organization:
Billing Street:
Billing City:
Billing State/Province:
Billing Postal Code:
Billing Country:
Billing Phone:
Billing Phone Ext:
Billing Fax:
Billing Fax Ext:
Billing Email:
Name Server: dns-nb00.aliant.net
Name Server: dns-nb01.aliant.net
Name Server: dns-ns00.aliant.net
Name Server: dns-on01.aliant.net
Name Server: dns-qc02.aliant.net
DNSSEC: unsigned
URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/
>>> Last update of WHOIS database: 2024-09-04T09:59:57Z <<<

For more information on Whois status codes, please visit https://icann.org/epp

%
% Use of CIRA's WHOIS service is governed by the Terms of Use in its Legal
% Notice, available at http://www.cira.ca/legal-notice/?lang=en
%
% (c) 2024 Canadian Internet Registration Authority, (http://www.cira.ca/)
``


2. **Social Media Profiling:** Gathering information about employees, company structure, and other details from social media platforms like LinkedIn, Facebook, and Twitter.
3. **Public Records and Databases:** Searching for information in public records, databases, and online directories.
4. **Google Dorking:** Using advanced search operators to find sensitive information indexed by search engines.
   
   >[!example]
   >
   >intext:"index of" 
   >
   >``This syntax is used for finding browsable directories!``
>
>filetype:log
>
>``This syntax is used for finding .log files``
>
>ext:pdf
>
>``This syntax is used for finding .PDF files!``


## Active Recon


>[!question]
>
>What is **Active Reconnaissance**?
>
>>[!answer]
>>
>>**Active reconnaissance** **Active reconnaissance** involves directly interacting with the target system to gather information. This type of recon is more intrusive and can be detected by the target. The goal is to probe the target system to identify vulnerabilities and gather detailed information.
>>


**Examples of Active Reconnaissance:**

1. **Port Scanning:** Using tools like ``Nmap`` to scan the target system’s open ports and services.
   
   >[!example]
   >
   >``
   >nmap -sV  # Version Scan (to identify the versions of running services)
   >``
   >or 
   >
   >``
   >nmap --script=smb*
   >``
   
   
   
2. **Network Mapping:** Identifying the network topology, devices, and their configurations using tools like ``traceroute`` or network discovery tools.
3. **Vulnerability Scanning:** Running automated tools like ``Nessus`` or ``OpenVAS`` to identify known vulnerabilities in the target system.
4. **Banner Grabbing:** Sending requests to services running on open ports to gather information about the software and versions in use.


