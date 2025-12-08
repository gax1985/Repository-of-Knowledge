


## Github Page : 



## What is this?

[](https://github.com/laramies/theHarvester#what-is-this)

theHarvester is a simple to use, yet powerful tool designed to be used during the reconnaissance stage of a red  
team assessment or penetration test. It performs open source intelligence (OSINT) gathering to help determine  
a domain's external threat landscape. The tool gathers names, emails, IPs, subdomains, and URLs by using  
multiple public resources that include:  

## Passive modules:

[](https://github.com/laramies/theHarvester#passive-modules)

- anubis: Anubis-DB - [https://github.com/jonluca/anubis](https://github.com/jonluca/anubis)
    
- bevigil: CloudSEK BeVigil scans mobile application for OSINT assets (Requires an API key, see below.) - [https://bevigil.com/osint-api](https://bevigil.com/osint-api)
    
- baidu: Baidu search engine - [www.baidu.com](http://www.baidu.com/)
    
- binaryedge: List of known subdomains (Requires an API key, see below.) - [https://www.binaryedge.io](https://www.binaryedge.io/)
    
- bing: Microsoft search engine - [https://www.bing.com](https://www.bing.com/)
    
- bingapi: Microsoft search engine, through the API (Requires an API key, see below.)
    
- brave: Brave search engine - [https://search.brave.com/](https://search.brave.com/)
    
- bufferoverun: (Requires an API key, see below.) [https://tls.bufferover.run](https://tls.bufferover.run/)
    
- censys: [Censys search engine](https://search.censys.io/) will use certificates searches to enumerate subdomains and gather emails  
    (Requires an API key, see below.) [https://censys.io](https://censys.io/)
    
- certspotter: Cert Spotter monitors Certificate Transparency logs - [https://sslmate.com/certspotter/](https://sslmate.com/certspotter/)
    
- criminalip: Specialized Cyber Threat Intelligence (CTI) search engine (Requires an API key, see below.) - [https://www.criminalip.io](https://www.criminalip.io/)
    
- crtsh: Comodo Certificate search - [https://crt.sh](https://crt.sh/)
    
- dnsdumpster: DNSdumpster search engine - [https://dnsdumpster.com](https://dnsdumpster.com/)
    
- duckduckgo: DuckDuckGo search engine - [https://duckduckgo.com](https://duckduckgo.com/)
    
- fullhunt: Next-generation attack surface security platform (Requires an API key, see below.) - [https://fullhunt.io](https://fullhunt.io/)
    
- github-code: GitHub code search engine (Requires a GitHub Personal Access Token, see below.) - [www.github.com](http://www.github.com/)
    
- hackertarget: Online vulnerability scanners and network intelligence to help organizations - [https://hackertarget.com](https://hackertarget.com/)
    
- hunter: Hunter search engine (Requires an API key, see below.) - [https://hunter.io](https://hunter.io/)
    
- hunterhow: Internet search engines for security researchers (Requires an API key, see below.) - [https://hunter.how](https://hunter.how/)
    
- intelx: Intelx search engine (Requires an API key, see below.) - [http://intelx.io](http://intelx.io/)
    
- netlas: A Shodan or Censys competitor (Requires an API key, see below.) - [https://app.netlas.io](https://app.netlas.io/)
    
- onyphe: Cyber defense search engine (Requires an API key, see below.) - [https://www.onyphe.io/](https://www.onyphe.io/)
    
- otx: AlienVault open threat exchange - [https://otx.alienvault.com](https://otx.alienvault.com/)
    
- pentestTools: Cloud-based toolkit for offensive security testing, focused on web applications and network penetration  
    testing (Requires an API key, see below.) - [https://pentest-tools.com/](https://pentest-tools.com/)
    
- projecDiscovery: We actively collect and maintain internet-wide assets data, to enhance research and analyse changes around  
    DNS for better insights (Requires an API key, see below.) - [https://chaos.projectdiscovery.io](https://chaos.projectdiscovery.io/)
    
- rapiddns: DNS query tool which make querying subdomains or sites of a same IP easy! [https://rapiddns.io](https://rapiddns.io/)
    
- rocketreach: Access real-time verified personal/professional emails, phone numbers, and social media links (Requires an API key,  
    see below.) - [https://rocketreach.co](https://rocketreach.co/)
    
- securityTrails: Security Trails search engine, the world's largest repository of historical DNS data (Requires an API key, see  
    below.) - [https://securitytrails.com](https://securitytrails.com/)
    
- -s, --shodan: Shodan search engine will search for ports and banners from discovered hosts (Requires an API key, see below.)  
    [https://shodan.io](https://shodan.io/)
    
- sitedossier: Find available information on a site - [http://www.sitedossier.com](http://www.sitedossier.com/)
    
- subdomaincenter: A subdomain finder tool used to find subdomains of a given domain - [https://www.subdomain.center/](https://www.subdomain.center/)
    
- subdomainfinderc99: A subdomain finder is a tool used to find the subdomains of a given domain - [https://subdomainfinder.c99.nl](https://subdomainfinder.c99.nl/)
    
- threatminer: Data mining for threat intelligence - [https://www.threatminer.org/](https://www.threatminer.org/)
    
- tomba: Tomba search engine (Requires an API key, see below.) - [https://tomba.io](https://tomba.io/)
    
- urlscan: A sandbox for the web that is a URL and website scanner - [https://urlscan.io](https://urlscan.io/)
    
- vhost: Bing virtual hosts search
    
- virustotal: Domain search (Requires an API key, see below.) - [https://www.virustotal.com](https://www.virustotal.com/)
    
- yahoo: Yahoo search engine
    
- zoomeye: China's version of Shodan (Requires an API key, see below.) - [https://www.zoomeye.org](https://www.zoomeye.org/)
    

## Active modules:

[](https://github.com/laramies/theHarvester#active-modules)

- DNS brute force: dictionary brute force enumeration
- Screenshots: Take screenshots of subdomains that were found

## Modules that require an API key:

[](https://github.com/laramies/theHarvester#modules-that-require-an-api-key)

Documentation to setup API keys can be found at - [https://github.com/laramies/theHarvester/wiki/Installation#api-keys](https://github.com/laramies/theHarvester/wiki/Installation#api-keys)

- bevigil - Free upto 50 queries. Pricing can be found here: [https://bevigil.com/pricing/osint](https://bevigil.com/pricing/osint)
- binaryedge - $10/month
- bing
- bufferoverun - uses the free API
- censys - API keys are required and can be retrieved from your [Censys account](https://search.censys.io/account/api).
- criminalip
- fullhunt
- github
- hunter - limited to 10 on the free plan, so you will need to do -l 10 switch
- hunterhow
- intelx
- netlas - $
- onyphe -$
- pentestTools - $
- projecDiscovery - invite only for now
- rocketreach - $
- securityTrails
- shodan - $
- tomba - Free up to 50 search.
- zoomeye

## Install and dependencies:

[](https://github.com/laramies/theHarvester#install-and-dependencies)

- Python 3.10+
- [https://github.com/laramies/theHarvester/wiki/Installation](https://github.com/laramies/theHarvester/wiki/Installation)

## Comments, bugs, and requests:

[](https://github.com/laramies/theHarvester#comments-bugs-and-requests)

- [![Twitter Follow](https://camo.githubusercontent.com/40b7208719681b06186b721d47670c0bd0261e1b4dde4673510a0729b7d1affe/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f6c6172616d6965732e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/laramies) Christian Martorella @laramies [cmartorella@edge-security.com](mailto:cmartorella@edge-security.com)
- [![Twitter Follow](https://camo.githubusercontent.com/45e348908392a2ab62e84928c47ee709e1032caf52f5460128e171625823b931/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f4e6f746f72696f7573526562656c312e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/NotoriousRebel1) Matthew Brown @NotoriousRebel1
- [![Twitter Follow](https://camo.githubusercontent.com/82be2d344fe2e480adf91bc339531d3e1dc89c51565ed9f45d021b3ce7dba6cc/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f6a61795f746f776e73656e64312e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/jay_townsend1) Jay "L1ghtn1ng" Townsend @jay_townsend1

## Main contributors:

[](https://github.com/laramies/theHarvester#main-contributors)

- [![Twitter Follow](https://camo.githubusercontent.com/45e348908392a2ab62e84928c47ee709e1032caf52f5460128e171625823b931/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f4e6f746f72696f7573526562656c312e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/NotoriousRebel1) Matthew Brown @NotoriousRebel1
- [![Twitter Follow](https://camo.githubusercontent.com/82be2d344fe2e480adf91bc339531d3e1dc89c51565ed9f45d021b3ce7dba6cc/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f6a61795f746f776e73656e64312e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/jay_townsend1) Jay "L1ghtn1ng" Townsend @jay_townsend1
- [![Twitter Follow](https://camo.githubusercontent.com/36c5e75e52e0ed018396bf1e36dfe1a2a936c85b309a3bd671dff888f7f2fdf3/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f646973636f766572736372697074732e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)](https://twitter.com/discoverscripts) Lee Baird @discoverscripts

## Thanks:

[](https://github.com/laramies/theHarvester#thanks)

- John Matherly - Shodan project
- Ahmed Aboul Ela - subdomain names dictionaries (big and small)


--------------------------------------------------------------------


[Sohvaxus](https://sohvaxus.github.io/index.html)

General

- [HOME](https://sohvaxus.github.io/index.html)
- [README.TXT](https://sohvaxus.github.io/readme.html)

# TheHarvester

_Information Gathering Tool_

---

1. [Home](https://sohvaxus.github.io/index.html)
 3. TheHarvester

|   |   |
|---|---|
|Author:|Christian Martorella|
|License:|GPLv2|
|Software:|TheHarvester|
|Date created:|2011|
|Updated:|Yes|
|GitHub:|[TheHarvester GitHub](https://github.com/laramies/theHarvester)|

Last updated: 21 november 2018

1. ##### Description
    

TheHarvester is an OSINT tool for gathering subdomains, email addresses, open ports, banners, employee names, and much more from different public sources. (Google, Bing, PGP key servers, ...). In order to gather this information it will do active and passive information gathering.

You would want to use this tool when you are curious about the visibility of your company on the internet or for information gathering purposes during a penetration test.

4. ##### Cheatsheet
    
`# Syntax theharvester -d [domain] -l [amount of depthness] -b [search engines] -f [filename]`  
`# Basic scan of the given domain, returns 500 results for each search engine. theharvester -d google.com -l 500 -b all`  
`# Output your scan results to a visual report in HTML format theharvester -d google.com -l 500 -b all -f results.html`  

**-d** : Specifies the domain to scan

**-l** : Specifies how deep the scan should go. More is better but slower! :)

**-b** : Specifies the search engine to search on. (options as of may 2018: google, googleCSE, bing, bingapi, pgp, linkedin, google-profiles, jigsaw, twitter, googleplus, all)

**-f** : Specifies an output file for the found results. This file will be saved in the current directory from your terminal, unless specified otherwise, in the HTML format.

15. ##### Passive gathering sources:
    

- [ThreadCrowd](https://www.threatcrowd.org/): Open source threat intelligence

- [crtsh](https://www.crt.sh/): Comodo certificate search

- [Google](https://www.google.com/): Google search engine

- GoogleCSE: Google custom search engine

- Google-profiles: Google search engine, specified search for Google profiles

- [Bing](https://www.bing.com/): Microsoft search engine

- BingAPI: Microsoft search engine API

- [Dogpile](https://www.dogpile.com/): Dogpile search engine

- PGP: PGP key server

- LinkedIn: Google search engine, specified search for LinkedIn users

- [Shodan](https://www.shodanhq.com/): Shodan search engine, will search for ports and banners of the discovered hosts.

- [Baidu](https://www.baidu.com/): Baidu search engine

- [Yahoo](https://www.yahoo.com/): Yahoo search engine

- vhost: Bing virtual hosts search

- Twitter: Searches for Twitter accounts related to a certain domain, uses Google search

- [Google+](https://plus.google.com/discover): Searches for users that work in the target company, uses Google search

32. ##### Active gathering sources:
    

- Port scanning and takeover options

- DNS bruteforce: A plugin that will run a dictionary brute force enumeration attack.

- DNS reverse lookup: Reverse lookup of discovered IP's to find hostnames.

- DNS TLD (Top-level domain) expansion: TLD dictionary brute force enumeration.

37. ##### Modules that require API keys:
    

- GoogleCSE: You need to create a Google Custom Search engine(CSE), and add your Google API key and CSE ID in the plugin (discovery/googleCSE.py)

- Shodan: You need to provide your API key in discovery/shodansearch.py

**

** For more information, check out the extra links and sources. **

**

##### 50URC35:

- [TheHarvester GitHub](https://github.com/laramies/theHarvester)
- [Information gathering using TheHarvester](https://www.hacking-tutorial.com/tips-and-trick/information-gathering-using-theharvester-in-kali-linux/#sthash.IIH1cA08.dpbs)
- [Information gathering with TheHarvester](https://xeushack.com/information-gathering-with-theharvester/)


-------------------------------------------------------------------


[Skip to content](https://csilinux.com/decoding-theharvester-your-digital-detective-toolkit/#content_skip_link_anchor)[Skip to footer](https://csilinux.com/decoding-theharvester-your-digital-detective-toolkit/#footer_skip_link_anchor)

[![CSI Linux](https://csilinux.com/wp-content/uploads/2023/08/CSILinux-Menu.png)](https://csilinux.com/)

- [Information](https://csilinux.com/posts/)
- [CSI Downloads](https://csilinux.com/csi-linux-downloads/)
- [Academy](https://csilinux.com/academy)
- [The CSI Linux Pro Shop](https://csilinux.com/shop/)
- [My account](https://csilinux.com/my-account/)

0

[](https://csilinux.com/)

- [](https://csilinux.com/posts/)
- [](https://csilinux.com/csi-linux-downloads/)
- [](https://csilinux.com/academy)
- [](https://csilinux.com/shop/)
- [](https://csilinux.com/my-account/)

[Open-Source Intelligence (OSINT)](https://csilinux.com/category/open-source-intelligence-osint/) [Tools](https://csilinux.com/category/tools/)

# Decoding theHarvester: Your Digital Detective Toolkit

[](https://csilinux.com/decoding-theharvester-your-digital-detective-toolkit/#)

In the shado

Meet theHarvester—a command-line ally designed for the modern-day digital spy. This tool isn’t just a program; it’s your gateway into the hidden recesses of the World Wide Web, allowing you to unearth the digital traces left behind by individuals and organizations alike. Imagine you’re the protagonist in a gripping spy thriller. Your mission: to infiltrate the digital landscape and gather intelligence on a multinational corporation. Here, theHarvester steps into the light. It’s not just any tool; it’s a precision instrument in the art of Open Source Intelligence (OSINT) gathering. OSINT involves collecting data from publicly available sources to be used in an analysis, much like collecting puzzle pieces scattered across the internet—from social media platforms to website registrations and beyond.

##### What is theHarvester?

theHarvester is a command-line interface (CLI) tool, which means it operates through text commands inputted into a terminal, rather than graphical buttons and menus. This might sound daunting, but it’s akin to typing search queries into Google—only much more powerful. It allows investigators like you to quickly and efficiently scour the internet for email addresses, domain names, and even individual names associated with a particular company or entity.

##### Why Use theHarvester?

In our fictional narrative, as an investigator, you might need to identify the key players within a corporation, understand its digital footprint, or even predict its future moves based on current data. theHarvester allows you to gather this intelligence quietly and effectively, just like a spy would gather information without alerting the target of their presence.

##### What Evidence Can You Gather?

With theHarvester, the type of information you can compile is vast:

- - **Email Addresses**: Discovering email formats and contact details can help in creating communication profiles and understanding internal company structures.
    - **Domain Names**: Unveiling related domains provides insights into the company’s expansion, cybersecurity posture, and more.
    - **Host Names and Public IP Ranges**: Knowing the infrastructure of a target can reveal the geographical locations of servers, potentially highlighting operational regions and network vulnerabilities.

Each piece of data collected with theHarvester adds a layer of depth to your understanding of the target, providing you with a clearer picture of the digital battlefield. This intelligence is critical, whether you are safeguarding national security, protecting corporate interests, or simply unmasking the digital persona of a competitive entity.

In the game of digital investigations, knowledge is power. And with theHarvester, you are well-equipped to navigate the murky waters of cyberspace, pulling strings from the shadows, one piece of data at a time. So gear up, for your mission is just beginning, and the digital realm awaits your exploration. Stay tuned for the next section where we dive deeper into how you can wield this powerful tool to its full potential.

Before embarking on any mission, preparation is key. In the realm of digital espionage, this means configuring theHarvester to ensure it’s primed to gather the intelligence you need effectively. Setting up involves initializing the tool and integrating various API keys that enhance its capability to probe deeper into the digital domain.

##### Setting Up theHarvester

Once theHarvester is installed on your machine, the next step is configuring it to maximize its data-gathering capabilities. The command-line nature of the tool requires a bit of initial setup through a terminal, which involves preparing the environment and ensuring all dependencies are updated. This setup ensures that the tool runs smoothly and efficiently, ready to comb through digital data with precision.

##### Integrating API Keys

To elevate the functionality of theHarvester and enable access to a broader array of data sources, you need to integrate API keys from various services. API keys act as access tokens that allow theHarvester to query external databases and services such as search engines, social media platforms, and domain registries. Here are a few key APIs that can significantly enhance your intelligence gathering:

1. 1. **Google API Key**: For accessing the wealth of information available through Google searches.
    2. **Bing API Key**: Allows for querying Microsoft’s Bing search engine to gather additional data.
    3. **Hunter API Key**: Specializes in finding email addresses associated with a domain.
    4. **LinkedIn API Key**: Useful for gathering professional profiles and company information.

To integrate these API keys:

Locate the configuration file typically named `api-keys.yaml` or similar in the tool’s installation directory. Open this file with a text editor and insert your API keys next to their respective services. Each entry should look something like:

`google_api_key: 'YOUR_API_KEY_HERE'   `Replace `’YOUR_API_KEY_HERE’` with your actual API key.

This step is crucial as it allows theHarvester to utilize these platforms to fetch information that would otherwise be inaccessible, making your digital investigation more thorough and expansive.

##### Configuring Environment Variables

Some API integrations might require setting environment variables on your operating system to ensure they are recognized globally by theHarvester during its operation:

`echo 'export GOOGLE_API_KEY="your_api_key"' >> ~/.bashrc source ~/.bashrc`

With theHarvester properly configured and API keys integrated, you are now equipped to delve into the digital shadows and extract the information hidden therein. This setup not only streamlines your investigations but also broadens the scope of data you can access, setting the stage for a successful mission.

In our next section, we will demonstrate how to deploy theHarvester in a live scenario, showing you how to navigate its commands and interpret the intelligence you gather. Prepare to harness the full power of your digital espionage toolkit.

##### Deploying theHarvester for Reconnaissance on “google.com”

With theHarvester configured and ready, it’s time to dive into the actual operation. The mission objective is clear: to gather extensive intelligence about “google.com”. This involves using theHarvester to query various data sources, each offering unique insights into the domain’s digital footprint. This section will provide the syntax necessary to conduct this digital investigation effectively.

##### Launching theHarvester

To begin, you need to launch theHarvester from the command line. Ensure you’re in the directory where theHarvester is installed, or that it’s added to your path. The basic command to start your investigation into “google.com” is structured as follows:

`theharvester -d google.com -b all`

Here, `-d` specifies the domain you are investigating, which in this case is “google.com”. The `-b` option tells theHarvester to use all available data sources, maximizing the scope of data collection. However, for more controlled and specific investigations, you may choose to select specific data sources.

##### Specifying Data Sources

If you wish to narrow down the sources and target specific ones such as Google, Bing, or email databases, you can modify the `-b` parameter accordingly. For instance, if you want to focus only on gathering data from Google and Bing, you would use:

`theharvester -d google.com -b google,bing`

This command instructs theHarvester to limit its queries to Google and Bing search engines, which can provide valuable data without the noise from less relevant sources.

##### Advanced Searching with APIs

Integrating API keys allows for deeper searches. For instance, using a Google API key can significantly enhance the depth and relevance of the data gathered. You would typically configure this in the API configuration file as discussed previously, but it directly influences the command’s effectiveness.

`theharvester -d google.com -b google -g your_google_api_key`

In this command, `-g` represents the Google API key parameter, though please note the actual syntax for entering API keys may vary based on theHarvester’s version and configuration settings.

##### Mastering Advanced Options in theHarvester

Having covered the basic operational settings of theHarvester, it’s important to delve into its more sophisticated capabilities. These advanced options enhance the tool’s flexibility, allowing for more targeted and refined searches. Here’s an exploration of these additional features that have not been previously discussed, ensuring you can fully leverage theHarvester in your investigations.

##### Proxy Usage

When conducting sensitive investigations, maintaining anonymity is crucial. theHarvester supports the use of proxies to mask your IP address during searches:

`theharvester -d example.com -b google -p`

This command enables proxy usage, pulling proxy details from a `proxies.yaml` configuration file.

##### Shodan Integration

For a deeper dive into the infrastructure of a domain, integrating Shodan can provide detailed information about discovered hosts:

`theharvester -d example.com -s`

When using the Shodan integration in theHarvester, the expected output centers around the data that Shodan provides about the hosts associated with the domain you are investigating. Shodan collects extensive details about devices connected to the internet, including services running on these devices, their geographic locations, and potential vulnerabilities. Here’s a more detailed breakdown of what you might see:

`Host: 93.184.216.34 Organization:   Example Organization Location: Dallas, Texas, United States   Ports open: 80 (HTTP), 443 (HTTPS)   Services:   - HTTP: Apache httpd 2.4.39   - HTTPS: Apache httpd 2.4.39 (supports SSLv3, TLS 1.0, TLS 1.1, TLS 1.2) Security Issues:   - TLS 1.0 Protocol Detected, Deprecated and Vulnerable   - Server exposes server tokens in its HTTP headers.   Last Update: 2024-04-12`

This output will include:

- - **IP addresses** and possibly **subdomains**: Identified during the reconnaissance phase.
    - **Organizational info**: Which organization owns the IP space.
    - **Location data**: Where the servers are physically located (country, city).
    - **Ports and services**: What services are exposed on these IPs, along with any detected ports.
    - **Security vulnerabilities**: Highlighted issues based on the service configurations and known vulnerabilities.
    - **Timestamps**: When Shodan last scanned these hosts.

This command uses Shodan to query details about the hosts related to the domain.

##### Screenshot Capability

Visual confirmation of web properties can be invaluable. theHarvester offers the option to take screenshots of resolved domains:

`theharvester -d example.com --screenshot output_directory`

For the screenshot functionality, theHarvester typically won’t output much to the console about this operation beyond a confirmation that screenshots are being taken and saved. Instead, the primary output will be the screenshots themselves, stored in the specified directory. Here’s what you might expect to see on your console:

`Starting screenshot capture for resolved domains of example.com... Saving screenshots to output_directory/ Screenshot captured for www.example.com saved as output_directory/www_example_com.png Screenshot captured for mail.example.com saved as output_directory/mail_example_com.png Screenshot process completed successfully.`

In the specified `output_directory`, you would find image files named after the domains they represent, showing the current state of the website as seen in a browser window. These images are particularly useful for visually verifying web properties, checking for defacement, or confirming the active web pages associated with the domain.

Each screenshot file will be named uniquely to avoid overwrites and to ensure that each domain’s visual data is preserved separately. This method provides a quick visual reference for the state of each web domain at the time of the investigation.

This command captures screenshots of websites associated with the domain and saves them to the specified directory.

##### DNS Resolution and Virtual Host Verification

Verifying the existence of domains and exploring associated virtual hosts can yield additional insights:

`theharvester -d example.com -v`

When using the `-v` option with theHarvester for DNS resolution and virtual host verification, the expected output will provide details on the resolved domains and any associated virtual hosts. This output helps in verifying the active hosts and discovering potentially hidden services or mistakenly configured DNS records. Here’s what you might expect to see:

`Resolving DNS for example.com...   DNS Resolution Results:   - Host: www.example.com, IP: 93.184.216.34   - Host: mail.example.com, IP: 93.184.216.35   Virtual Host Verification:   - www.example.com:   - Detected virtual hosts:   - vhost1.example.com   - secure.example.com   - mail.example.com:   - No virtual hosts detected   Verification completed successfully.`

This output includes:

- - **Resolved IP addresses** for given subdomains or hosts.
    - **Virtual hosts** detected under each resolved domain, which could indicate additional web services or alternative content served under different subdomains.

This command verifies hostnames via DNS resolution and searches for associated virtual hosts.

##### Custom DNS Server

Using a specific DNS server for lookups can help bypass local DNS modifications or restrictions:

`theharvester -d example.com -e 8.8.8.8`

When specifying a custom DNS server with the `-e` option, theHarvester uses this DNS server for all domain lookups. This can be particularly useful for bypassing local DNS modifications or for querying DNS information that might be fresher or more reliable from specific DNS providers. The expected output will confirm the usage of the custom DNS server and show the results as per this server’s DNS records:

`Using custom DNS server: 8.8.8.8   Resolving DNS for example.com...   DNS Resolution Results:   - Host: www.example.com, IP: 93.184.216.34   - Host: mail.example.com, IP: 93.184.216.35   DNS resolution completed using Google DNS.`

This output verifies that:

- - The **custom DNS server (Google DNS)** is actively used for queries.
    - The **results** shown are fetched using the specified DNS server, potentially providing different insights compared to default DNS servers.

This command specifies Google’s DNS server (`8.8.8.8`) for all DNS lookups.

##### Takeover Checks

Identifying domains vulnerable to takeovers can prevent potential security threats:

`theharvester -d example.com -t`

The `-t` option enables checking for domains vulnerable to takeovers, which can highlight security threats where domain configurations, such as CNAME records or AWS buckets, are improperly managed. This feature scans for known vulnerabilities that could allow an attacker to claim control over the domain. Here’s the type of output you might see:

`Checking for domain takeovers...   Vulnerability Check Results:   - www.example.com: No vulnerabilities found.   - mail.example.com: Possible takeover threat detected!   - Detail: Misconfigured DNS pointing to unclaimed AWS S3 bucket.   Takeover check completed with warnings.`

This output provides:

- - **Vulnerability status** for each scanned subdomain or host.
    - **Details** on specific configurations that might lead to potential takeovers, such as pointing to unclaimed services (like AWS S3 buckets) or services that have been decommissioned but still have DNS records pointing to them.

This option checks if the discovered domains are vulnerable to takeovers.

##### DNS Resolution Options

For thorough investigations, resolving DNS for subdomains can confirm their operational status:

`theharvester -d example.com -r`

This enables DNS resolution for all discovered subdomains.

##### DNS Lookup and Brute Force

Exploring all DNS records related to a domain provides a comprehensive view of its DNS footprint:

`theharvester -d example.com -n`

This command enables DNS lookups for the domain.

For more aggressive data gathering:

`theharvester -d example.com -c`

This conducts a DNS brute force attack on the domain to uncover additional subdomains.

##### Gathering Specific Types of Information

While gathering a wide range of data can be beneficial, sometimes a more targeted approach is needed. For example, if you are particularly interested in email addresses associated with the domain, you can add specific flags to focus on emails:

`theharvester -d google.com -b all -l 500 -f myresults.xml`

Here, `-l 500` limits the search to the first 500 results, which helps manage the volume of data and focus on the most relevant entries. The `-h` option specifies an HTML file to write the results to, making them easier to review. Similarly, `-f` specifies an XML file, offering another format for data analysis or integration into other tools.

##### Assessing the Output

After running these commands, theHarvester will provide output directly in the terminal or in the specified output files (HTML/XML). The results will include various types of information such as:

- - Domain names and associated subdomains
    - Email addresses found through various sources
    - Employee names or contact information if available through public data
    - IP addresses and possibly geolocations associated with the domain

This syntax and methodical approach empower you to meticulously map out the digital infrastructure and associated elements of “google.com”, giving you insights that can inform further investigations or security assessments.

##### The Mission: Digital Reconnaissance on Facebook.com

In the sprawling world of social media, Facebook stands as a behemoth, wielding significant influence over digital communication. For our case study, we launched an extensive reconnaissance mission on facebook.com using theHarvester, a renowned tool in the arsenal of digital investigators. The objective was clear: unearth a comprehensive view of Facebook’s subdomains to reveal aspects of its vast digital infrastructure.

##### The command for the Operation:

To commence this digital expedition, we deployed theHarvester with a command designed to scrape a broad array of data sources, ensuring no stone was left unturned in our quest for information:

`theHarvester.py -d facebook.com -b all -l 500 -f myresults.xml`

This command set theHarvester to probe all available sources for up to 500 records related to facebook.com, with the results to be saved in an XML file named `myresults.xml`.

##### Prettified XML Output:

The operation harvested a myriad of entries, each a doorway into a lesser-seen facet of Facebook’s operations. Below is the structured and prettified XML output showcasing some of the subdomains associated with facebook.com:

`<?xml version="1.0" encoding="UTF-8"?>   <theHarvester>   <host>edge-c2p-shv-01-fml20.facebook.com</host>   <host>whatsapp-chatd-edge-shv-01-fml20.facebook.com</host>   <host>livestream-edgetee-ws-upload-staging-shv-01-mba1.facebook.com</host>   <host>edge-fblite-tcp-p1-shv-01-fml20.facebook.com</host>   <host>traceroute-fbonly-bgp-01-fml20.facebook.com</host>   <host>livestream-edgetee-ws-upload-shv-01-mba1.facebook.com</host>   <host>synthetic-e2e-elbprod-sli-shv-01-mba1.facebook.com</host>   <host>edge-iglite-p42-shv-01-fml20.facebook.com</host>   <host>edge-iglite-p3-shv-01-fml20.facebook.com</host>   <host>msgin-regional-shv-01-rash0.facebook.com</host>   <host>cmon-checkout-edge-shv-01-fml20.facebook.com</host>   <host>edge-tcp-tunnel-fbonly-shv-01-fml20.facebook.com</host>   <!-- Additional hosts omitted for brevity -->   <host>edge-mqtt-p4-shv-01-mba1.facebook.com</host>   <host>edge-ig-mqtt-p4-shv-01-fml20.facebook.com</host>   <host>edge-recursor002-bgp-01-fml20.facebook.com</host>   <host>edge-secure-shv-01-mba1.facebook.com</host>   <host>edge-turnservice-shv-01-mba1.facebook.com</host>   <host>ondemand-edge-shv-01-mba1.facebook.com</host>   <host>whatsapp-chatd-igd-edge-shv-01-fml20.facebook.com</host>   <host>edge-dgw-p4-shv-01-fml20.facebook.com</host>   <host>edge-iglite-p3-shv-01-mba1.facebook.com</host>   <host>edge-fwdproxy-4-bgp-01-fml20.facebook.com</host>   <host>edge-ig-mqtt-p4-shv-01-mba1.facebook.com</host>   <host>fbcromwelledge-bgp-01-mba1.facebook.com</host>   <host>edge-dgw-shv-01-fml20.facebook.com</host>   <host>edge-recursor001-bgp-01-mba1.facebook.com</host>   <host>whatsapp-chatd-igd-edge-shv-01-mba1.facebook.com</host>   <host>edge-fwdproxy-3-bgp-01-mba1.facebook.com</host>   <host>edge-fwdproxy-5-bgp-01-fml20.facebook.com</host>   <host>edge-rtp-relay-40000-shv-01-mba1.facebook.com</host>   </theHarvester>`

##### Analysis of Findings:

The XML output revealed a diverse array of subdomains, each potentially serving different functions within Facebook’s extensive network. From service-oriented subdomains like `edge-mqtt-p4-shv-01-mba1.facebook.com`, which may deal with messaging protocols, to infrastructure-centric entries such as `edge-fwdproxy-4-b

##### Harnessing the Power of theHarvester in Digital Investigations

From setting up the environment to delving deep into the intricacies of a digital giant like Facebook, theHarvester has proved to be an indispensable tool in the arsenal of a modern digital investigator. Through our journey from understanding the tool’s basics to applying it in a live scenario against facebook.com, we’ve seen how theHarvester makes it possible to illuminate the shadowy corridors of the digital world.

##### The Prowess of OSINT with theHarvester

theHarvester is not just about collecting data—it’s about connecting dots. By revealing email addresses, domain names, and even the expansive network architecture of an entity like Facebook, this tool provides the clarity needed to navigate the complexities of today’s digital environments. It empowers users to unveil hidden connections, assess potential security vulnerabilities, and gain strategic insights that are crucial for both defensive and offensive cybersecurity measures.

##### A Tool for Every Digital Sleuth

Whether you’re a cybersecurity professional tasked with protecting sensitive information, a market analyst gathering competitive intelligence, or an investigative journalist uncovering the story behind the story, theHarvester equips you with the capabilities necessary to achieve your mission. It transforms the solitary act of data gathering into an insightful exploration of the digital landscape.

##### Looking Ahead

As the digital realm continues to expand, tools like theHarvester will become even more critical in the toolkit of those who navigate its depths. With each update and improvement, theHarvester is set to offer even more profound insights into the vast data troves of the internet, making it an invaluable resource for years to come.

Gear up, continue learning, and prepare to dive deeper. The digital realm is vast, and with theHarvester, you’re well-equipped to explore it thoroughly. Let this tool light your way as you uncover the secrets hidden within the web, and use the knowledge gained to make informed decisions that could shape the future of digital interactions. Remember, in the game of digital investigations, knowledge isn’t just power—it’s protection, insight, and above all, advantage.

[CSI Linux](https://csilinux.com/tag/csi-linux/)[DFIR](https://csilinux.com/tag/dfir/)[Internet](https://csilinux.com/tag/internet/)[Online Investigation](https://csilinux.com/tag/online-investigation/)[OSINT](https://csilinux.com/tag/osint/)[recon-ng](https://csilinux.com/tag/recon-ng/)[Reconnaissance](https://csilinux.com/tag/reconnaissance/)

[](https://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fcsilinux.com%2Fdecoding-theharvester-your-digital-detective-toolkit%2F&title=Decoding+theHarvester%3A+Your+Digital+Detective+Toolkit&summary=Meet+theHarvester%E2%80%94a+command-line+ally+designed+for+the+modern-day+digital+spy.+This+tool+isn%27t+just+a+program%3B+it%27s+your+gateway+into+the+hidden+recesses+of+the+World+Wide+Web%2C+allowing+you+to+unearth+the+digital+traces+left+behind+by+individuals+and+organizations+alike.+Imagine+you%27re+the+protagonist+in+a+gripping+spy+thriller.)[](https://twitter.com/intent/tweet?text=Decoding+theHarvester%3A+Your+Digital+Detective+Toolkit&url=https%3A%2F%2Fcsilinux.com%2Fdecoding-theharvester-your-digital-detective-toolkit%2F)[](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fcsilinux.com%2Fdecoding-theharvester-your-digital-detective-toolkit%2F)[](https://wa.me/?text=Decoding+theHarvester%3A+Your+Digital+Detective+Toolkit+https%3A%2F%2Fcsilinux.com%2Fdecoding-theharvester-your-digital-detective-toolkit%2F)[](https://reddit.com/submit?url=https%3A%2F%2Fcsilinux.com%2Fdecoding-theharvester-your-digital-detective-toolkit%2F&title=Decoding+theHarvester%3A+Your+Digital+Detective+Toolkit)[](https://telegram.me/share/url?url=https%3A%2F%2Fcsilinux.com%2Fdecoding-theharvester-your-digital-detective-toolkit%2F&text=Decoding+theHarvester%3A+Your+Digital+Detective+Toolkit)[](mailto:?subject=Decoding%20theHarvester:%20Your%20Digital%20Detective%20Toolkit&body=https%3A%2F%2Fcsilinux.com%2Fdecoding-theharvester-your-digital-detective-toolkit%2F)[](https://csilinux.com/decoding-theharvester-your-digital-detective-toolkit/# "Copy URL to clipboard")

## Post navigation

[Previous

###### Understanding Forensic Data Carving

](https://csilinux.com/understanding-forensic-data-carving/)

[Next

###### Unveiling Recon-ng: The Sleuth’s Digital Toolkit

](https://csilinux.com/unveiling-recon-ng-the-sleuths-digital-toolkit/)

### You May Also Like

![](https://csilinux.com/wp-content/uploads/2024/03/crypto_currency_bitcoin_tracing_for_the_layman-890x664.png)

[](https://csilinux.com/understanding-cryptocurrencies-a-laymans-guide/)

[Computer Forensics and Investigation](https://csilinux.com/category/computer-forensics-and-investigation/), [CSI Linux Academy](https://csilinux.com/category/csi-linux-academy/), [Open-Source Intelligence (OSINT)](https://csilinux.com/category/open-source-intelligence-osint/)

###### [Understanding Cryptocurrencies: A Layman’s Guide](https://csilinux.com/understanding-cryptocurrencies-a-laymans-guide/)

![Lokinet and Oxen cryptocurrency](https://csilinux.com/wp-content/uploads/2024/03/Lokinet_and_Oxen_cryptocurrency-890x664.png)

[](https://csilinux.com/the-synergy-of-lokinet-and-oxen-in-protecting-digital-privacy/)

[Computer Forensics and Investigation](https://csilinux.com/category/computer-forensics-and-investigation/), [CSI Linux](https://csilinux.com/category/csi-linux/), [CSI Linux Academy](https://csilinux.com/category/csi-linux-academy/), [Dark Web](https://csilinux.com/category/dark-web/), [Open-Source Intelligence (OSINT)](https://csilinux.com/category/open-source-intelligence-osint/), [OPSEC](https://csilinux.com/category/opsec/)

###### [The Synergy of Lokinet and Oxen in Protecting Digital Privacy](https://csilinux.com/the-synergy-of-lokinet-and-oxen-in-protecting-digital-privacy/)

[](https://csilinux.com/decoding-theharvester-your-digital-detective-toolkit/#)

## Unleash the Power of CSI Linux: Redefining Digital Investigations

[support@csilinux.com](mailto:support@csilinux.com)

- [Information](https://csilinux.com/posts/)
- [CSI Downloads](https://csilinux.com/csi-linux-downloads/)
- [Academy](https://csilinux.com/academy)
- [The CSI Linux Pro Shop](https://csilinux.com/shop/)
- [My account](https://csilinux.com/my-account/)

CSI Linux © 2024. All Rights Reserved.

[](https://csilinux.com/decoding-theharvester-your-digital-detective-toolkit/# "Scroll to top")