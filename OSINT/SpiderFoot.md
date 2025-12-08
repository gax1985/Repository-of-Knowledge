

```
usage: sf.py [-h] [-d] [-l IP:port] [-m mod1,mod2,...] [-M] [-C scanID] [-s TARGET] [-t type1,type2,...]
             [-u {all,footprint,investigate,passive}] [-T] [-o {tab,csv,json}] [-H] [-n] [-r] [-S LENGTH] [-D DELIMITER] [-f]
             [-F type1,type2,...] [-x] [-q] [-V] [-max-threads MAX_THREADS]

SpiderFoot 4.0.0: Open Source Intelligence Automation.

options:
  -h, --help            show this help message and exit
  -d, --debug           Enable debug output.
  -l IP:port            IP and port to listen on.
  -m mod1,mod2,...      Modules to enable.
  -M, --modules         List available modules.
  -C scanID, --correlate scanID
                        Run correlation rules against a scan ID.
  -s TARGET             Target for the scan.
  -t type1,type2,...    Event types to collect (modules selected automatically).
  -u {all,footprint,investigate,passive}
                        Select modules automatically by use case
  -T, --types           List available event types.
  -o {tab,csv,json}     Output format. Tab is default.
  -H                    Don't print field headers, just data.
  -n                    Strip newlines from data.
  -r                    Include the source data field in tab/csv output.
  -S LENGTH             Maximum data length to display. By default, all data is shown.
  -D DELIMITER          Delimiter to use for CSV output. Default is ,.
  -f                    Filter out other event types that weren't requested with -t.
  -F type1,type2,...    Show only a set of event types, comma-separated.
  -x                    STRICT MODE. Will only enable modules that can directly consume your target, and if -t was specified only
                        those events will be consumed by modules. This overrides -t and -m options.
  -q                    Disable logging. This will also hide errors!
  -V, --version         Display the version of SpiderFoot and exit.
  -max-threads MAX_THREADS
                        Max number of modules to run concurrently.

```


# Modules 


```
sfp_abstractapi            Look up domain, phone and IP address information from AbstractAPI.
sfp_abusech                Check if a host/domain, IP address or netblock is malicious according to Abuse.ch.
sfp_abuseipdb              Check if an IP address is malicious according to AbuseIPDB.com blacklist.
sfp_abusix                 Check if a netblock or IP address is in the Abusix Mail Intelligence blacklist.
sfp_accounts               Look for possible associated accounts on nearly 200 websites like Ebay, Slashdot, reddit, etc.
sfp_adblock                Check if linked pages would be blocked by AdBlock Plus.
sfp_adguard_dns            Check if a host would be blocked by AdGuard DNS.
sfp_ahmia                  Search Tor 'Ahmia' search engine for mentions of the target.
sfp_alienvault             Obtain information from AlienVault Open Threat Exchange (OTX)
sfp_alienvaultiprep        Check if an IP or netblock is malicious according to the AlienVault IP Reputation database.
sfp_apple_itunes           Search Apple iTunes for mobile apps.
sfp_archiveorg             Identifies historic versions of interesting files/pages from the Wayback Machine.
sfp_arin                   Queries ARIN registry for contact information.
sfp_azureblobstorage       Search for potential Azure blobs associated with the target and attempt to list their contents.
sfp_badpackets             Obtain information about any malicious activities involving IP addresses found
sfp_base64                 Identify Base64-encoded strings in URLs, often revealing interesting hidden information.
sfp_bgpview                Obtain network information from BGPView API.
sfp_binaryedge             Obtain information from BinaryEdge.io Internet scanning systems, including breaches, vulnerabilities, torrents and passive DNS.
sfp_bingsearch             Obtain information from bing to identify sub-domains and links.
sfp_bingsharedip           Search Bing for hosts sharing the same IP.
sfp_binstring              Attempt to identify strings in binary content.
sfp_bitcoin                Identify bitcoin addresses in scraped webpages.
sfp_bitcoinabuse           Check Bitcoin addresses against the bitcoinabuse.com database of suspect/malicious addresses.
sfp_bitcoinwhoswho         Check for Bitcoin addresses against the Bitcoin Who's Who database of suspect/malicious addresses.
sfp_blockchain             Queries blockchain.info to find the balance of identified bitcoin wallet addresses.
sfp_blocklistde            Check if a netblock or IP is malicious according to blocklist.de.
sfp_botscout               Searches BotScout.com's database of spam-bot IP addresses and e-mail addresses.
sfp_botvrij                Check if a domain is malicious according to botvrij.eu.
sfp_builtwith              Query BuiltWith.com's Domain API for information about your target's web technology stack, e-mail addresses and more.
sfp_c99                    Queries the C99 API which offers various data (geo location, proxy detection, phone lookup, etc).
sfp_callername             Lookup US phone number location and reputation information.
sfp_censys                 Obtain host information from Censys.io.
sfp_certspotter            Gather information about SSL certificates from SSLMate CertSpotter API.
sfp_cinsscore              Check if a netblock or IP address is malicious according to Collective Intelligence Network Security (CINS) Army list.
sfp_circllu                Obtain information from CIRCL.LU's Passive DNS and Passive SSL databases.
sfp_citadel                Searches Leak-Lookup.com's database of breaches.
sfp_cleanbrowsing          Check if a host would be blocked by CleanBrowsing.org DNS content filters.
sfp_cleantalk              Check if a netblock or IP address is on CleanTalk.org's spam IP list.
sfp_clearbit               Check for names, addresses, domains and more based on lookups of e-mail addresses on clearbit.com.
sfp_cloudflaredns          Check if a host would be blocked by CloudFlare DNS.
sfp_coinblocker            Check if a domain appears on CoinBlocker lists.
sfp_commoncrawl            Searches for URLs found through CommonCrawl.org.
sfp_comodo                 Check if a host would be blocked by Comodo Secure DNS.
sfp_company                Identify company names in any obtained data.
sfp_cookie                 Extract Cookies from HTTP headers.
sfp_countryname            Identify country names in any obtained data.
sfp_creditcard             Identify Credit Card Numbers in any data
sfp_crobat_api             Search Crobat API for subdomains.
sfp_crossref               Identify whether other domains are associated ('Affiliates') of the target by looking for links back to the target site(s).
sfp_crt                    Gather hostnames from historical certificates in crt.sh.
sfp_crxcavator             Search CRXcavator for Chrome extensions.
sfp_customfeed             Check if a host/domain, netblock, ASN or IP is malicious according to your custom feed.
sfp_cybercrimetracker      Check if a host/domain or IP address is malicious according to CyberCrime-Tracker.net.
sfp_darksearch             Search the Darksearch.io Tor search engine for mentions of the target domain.
sfp_debounce               Check whether an email is disposable
sfp_dehashed               Gather breach data from Dehashed API.
sfp_digitaloceanspace      Search for potential Digital Ocean Spaces associated with the target and attempt to list their contents.
sfp_dns_for_family         Check if a host would be blocked by DNS for Family.
sfp_dnsbrute               Attempts to identify hostnames through brute-forcing common names and iterations.
sfp_dnscommonsrv           Attempts to identify hostnames through brute-forcing common DNS SRV records.
sfp_dnsdb                  Query FarSight's DNSDB for historical and passive DNS data.
sfp_dnsdumpster            Passive subdomain enumeration using HackerTarget's DNSDumpster
sfp_dnsgrep                Obtain Passive DNS information from Rapid7 Sonar Project using DNSGrep API.
sfp_dnsneighbor            Attempt to reverse-resolve the IP addresses next to your target to see if they are related.
sfp_dnsraw                 Retrieves raw DNS records such as MX, TXT and others.
sfp_dnsresolve             Resolves hosts and IP addresses identified, also extracted from raw content.
sfp_dnszonexfer            Attempts to perform a full DNS zone transfer.
sfp_dronebl                Query the DroneBL database for open relays, open proxies, vulnerable servers, etc.
sfp_duckduckgo             Query DuckDuckGo's API for descriptive information about your target.
sfp_email                  Identify e-mail addresses in any obtained data.
sfp_emailcrawlr            Search EmailCrawlr for email addresses and phone numbers associated with a domain.
sfp_emailformat            Look up e-mail addresses on email-format.com.
sfp_emailrep               Search EmailRep.io for email address reputation.
sfp_emergingthreats        Check if a netblock or IP address is malicious according to EmergingThreats.net.
sfp_errors                 Identify common error messages in content like SQL errors, etc.
sfp_ethereum               Identify ethereum addresses in scraped webpages.
sfp_etherscan              Queries etherscan.io to find the balance of identified ethereum wallet addresses.
sfp_filemeta               Extracts meta data from documents and images.
sfp_flickr                 Search Flickr for domains, URLs and emails related to the specified domain.
sfp_focsec                 Look up IP address information from Focsec.
sfp_fortinet               Check if an IP address is malicious according to FortiGuard Antispam.
sfp_fraudguard             Obtain threat information from Fraudguard.io
sfp_fsecure_riddler        Obtain network information from F-Secure Riddler.io API.
sfp_fullcontact            Gather domain and e-mail information from FullContact.com API.
sfp_fullhunt               Identify domain attack surface using FullHunt API.
sfp_github                 Identify associated public code repositories on Github.
sfp_gleif                  Look up company information from Global Legal Entity Identifier Foundation (GLEIF).
sfp_googlemaps             Identifies potential physical addresses and latitude/longitude coordinates.
sfp_googleobjectstorage    Search for potential Google Object Storage buckets associated with the target and attempt to list their contents.
sfp_googlesafebrowsing     Check if the URL is included on any of the Safe Browsing lists.
sfp_googlesearch           Obtain information from the Google Custom Search API to identify sub-domains and links.
sfp_gravatar               Retrieve user information from Gravatar API.
sfp_grayhatwarfare         Find bucket names matching the keyword extracted from a domain from Grayhat API.
sfp_greensnow              Check if a netblock or IP address is malicious according to greensnow.co.
sfp_grep_app               Search grep.app API for links and emails related to the specified domain.
sfp_greynoise              Obtain IP enrichment data from GreyNoise
sfp_h1nobbdde              Check external vulnerability scanning/reporting service h1.nobbd.de to see if the target is listed.
sfp_hackertarget           Search HackerTarget.com for hosts sharing the same IP.
sfp_hashes                 Identify MD5 and SHA hashes in web content, files and more.
sfp_haveibeenpwned         Check HaveIBeenPwned.com for hacked e-mail addresses identified in breaches.
sfp_honeypot               Query the Project Honey Pot database for IP addresses.
sfp_hosting                Find out if any IP addresses identified fall within known 3rd party hosting ranges, e.g. Amazon, Azure, etc.
sfp_hostio                 Obtain information about domain names from host.io.
sfp_hunter                 Check for e-mail addresses and names on hunter.io.
sfp_hybrid_analysis        Search Hybrid Analysis for domains and URLs related to the target.
sfp_iban                   Identify International Bank Account Numbers (IBANs) in any data.
sfp_iknowwhatyoudownload   Check iknowwhatyoudownload.com for IP addresses that have been using torrents.
sfp_instagram              Gather information from Instagram profiles.
sfp_intelx                 Obtain information from IntelligenceX about identified IP addresses, domains, e-mail addresses and phone numbers.
sfp_intfiles               Identifies potential files of interest, e.g. office documents, zip files.
sfp_ipapico                Queries ipapi.co to identify geolocation of IP Addresses using ipapi.co API
sfp_ipapicom               Queries ipapi.com to identify geolocation of IP Addresses using ipapi.com API
sfp_ipinfo                 Identifies the physical location of IP addresses identified using ipinfo.io.
sfp_ipqualityscore         Determine if target is malicious using IPQualityScore API
sfp_ipregistry             Query the ipregistry.co database for reputation and geo-location.
sfp_ipstack                Identifies the physical location of IP addresses identified using ipstack.com.
sfp_isc                    Check if an IP address is malicious according to SANS ISC.
sfp_jsonwhoiscom           Search JsonWHOIS.com for WHOIS records associated with a domain.
sfp_junkfiles              Looks for old/temporary and other similar files.
sfp_keybase                Obtain additional information about domain names and identified usernames.
sfp_koodous                Search Koodous for mobile apps.
sfp_leakix                 Search LeakIX for host data leaks, open ports, software and geoip.
sfp_maltiverse             Obtain information about any malicious activities involving IP addresses
sfp_malwarepatrol          Searches malwarepatrol.net's database of malicious URLs/IPs.
sfp_metadefender           Search MetaDefender API for IP address and domain IP reputation.
sfp_mnemonic               Obtain Passive DNS information from PassiveDNS.mnemonic.no.
sfp_multiproxy             Check if an IP address is an open proxy according to multiproxy.org open proxy list.
sfp_myspace                Gather username and location from MySpace.com profiles.
sfp_nameapi                Check whether an email is disposable
sfp_names                  Attempt to identify human names in fetched content.
sfp_networksdb             Search NetworksDB.io API for IP address and domain information.
sfp_neutrinoapi            Search NeutrinoAPI for phone location information, IP address information, and host reputation.
sfp_numverify              Lookup phone number location and carrier information from numverify.com.
sfp_onioncity              Search Tor 'Onion City' search engine for mentions of the target domain using Google Custom Search.
sfp_onionsearchengine      Search Tor onionsearchengine.com for mentions of the target domain.
sfp_onyphe                 Check Onyphe data (threat list, geo-location, pastries, vulnerabilities)  about a given IP.
sfp_open_passive_dns_database  Obtain passive DNS information from pdns.daloo.de Open passive DNS database.
sfp_openbugbounty          Check external vulnerability scanning/reporting service openbugbounty.org to see if the target is listed.
sfp_opencorporates         Look up company information from OpenCorporates.
sfp_opendns                Check if a host would be blocked by OpenDNS.
sfp_opennic                Resolves host names in the OpenNIC alternative DNS system.
sfp_openphish              Check if a host/domain is malicious according to OpenPhish.com.
sfp_openstreetmap          Retrieves latitude/longitude coordinates for physical addresses from OpenStreetMap API.
sfp_pageinfo               Obtain information about web pages (do they take passwords, do they contain forms, etc.)
sfp_pastebin               PasteBin search (via Google Search API) to identify related content.
sfp_pgp                    Look up e-mail addresses in PGP public key servers.
sfp_phishstats             Check if a netblock or IP address is malicious according to PhishStats.
sfp_phishtank              Check if a host/domain is malicious according to PhishTank.
sfp_phone                  Identify phone numbers in scraped webpages.
sfp_portscan_tcp           Scans for commonly open TCP ports on Internet-facing systems.
sfp_projectdiscovery       Search for hosts/subdomains using chaos.projectdiscovery.io
sfp_psbdmp                 Check psbdmp.cc (PasteBin Dump) for potentially hacked e-mails and domains.
sfp_pulsedive              Obtain information from Pulsedive's API.
sfp_punkspider             Check the QOMPLX punkspider.io service to see if the target is listed as vulnerable.
sfp_quad9                  Check if a host would be blocked by Quad9 DNS.
sfp_recondev               Search Recon.dev for subdomains.
sfp_reversewhois           Reverse Whois lookups using reversewhois.io.
sfp_ripe                   Queries the RIPE registry (includes ARIN data) to identify netblocks and other info.
sfp_riskiq                 Obtain information from RiskIQ's (formerly PassiveTotal) Passive DNS and Passive SSL databases.
sfp_robtex                 Search Robtex.com for hosts sharing the same IP.
sfp_s3bucket               Search for potential Amazon S3 buckets associated with the target and attempt to list their contents.
sfp_scylla                 Gather breach data from Scylla API.
sfp_searchcode             Search searchcode for code repositories mentioning the target domain.
sfp_securitytrails         Obtain Passive DNS and other information from SecurityTrails
sfp_seon                   Queries seon.io to gather intelligence about IP Addresses, email addresses, and phone numbers
sfp_shodan                 Obtain information from SHODAN about identified IP addresses.
sfp_similar                Search various sources to identify similar looking domain names, for instance squatted domains.
sfp_skymem                 Look up e-mail addresses on Skymem.
sfp_slideshare             Gather name and location from SlideShare profiles.
sfp_snov                   Gather available email IDs from identified domains
sfp_social                 Identify presence on social media networks such as LinkedIn, Twitter and others.
sfp_sociallinks            Queries SocialLinks.io to gather intelligence from social media platforms and dark web.
sfp_socialprofiles         Tries to discover the social media profiles for human names identified.
sfp_sorbs                  Query the SORBS database for open relays, open proxies, vulnerable servers, etc.
sfp_spamcop                Check if a netblock or IP address is in the SpamCop database.
sfp_spamhaus               Check if a netblock or IP address is in the Spamhaus Zen database.
sfp_spider                 Spidering of web-pages to extract content for searching.
sfp_spur                   Obtain information about any malicious activities involving IP addresses found
sfp_spyonweb               Search SpyOnWeb for hosts sharing the same IP address, Google Analytics code, or Google Adsense code.
sfp_spyse                  Search Spyse.com Internet assets registry for information about domains, IP addresses, host info, potential vulnerabilities, passive DNS, etc.
sfp_sslcert                Gather information about SSL certificates used by the target's HTTPS sites.
sfp_stackoverflow          Search StackOverflow for any mentions of a target domain. Returns potentially related information.
sfp_stevenblack_hosts      Check if a domain is malicious (malware or adware) according to Steven Black Hosts list.
sfp_strangeheaders         Obtain non-standard HTTP headers returned by web servers.
sfp_subdomain_takeover     Check if affiliated subdomains are vulnerable to takeover.
sfp_sublist3r              Passive subdomain enumeration using Sublist3r's API
sfp_surbl                  Check if a netblock, IP address or domain is in the SURBL blacklist.
sfp_talosintel             Check if a netblock or IP address is malicious according to TalosIntelligence.
sfp_textmagic              Obtain phone number type from TextMagic API
sfp_threatcrowd            Obtain information from ThreatCrowd about identified IP addresses, domains and e-mail addresses.
sfp_threatfox              Check if an IP address is malicious according to ThreatFox.
sfp_threatminer            Obtain information from ThreatMiner's database for passive DNS and threat intelligence.
sfp_tldsearch              Search all Internet TLDs for domains with the same name as the target (this can be very slow.)
sfp_tool_cmseek            Identify what Content Management System (CMS) might be used.
sfp_tool_dnstwist          Identify bit-squatting, typo and other similar domains to the target using a local DNSTwist installation.
sfp_tool_nbtscan           Scans for open NETBIOS nameservers on your target's network.
sfp_tool_nmap              Identify what Operating System might be used.
sfp_tool_nuclei            Fast and customisable vulnerability scanner.
sfp_tool_onesixtyone       Fast scanner to find publicly exposed SNMP services.
sfp_tool_retirejs          Scanner detecting the use of JavaScript libraries with known vulnerabilities
sfp_tool_snallygaster      Finds file leaks and other security problems on HTTP servers.
sfp_tool_testsslsh         Identify various TLS/SSL weaknesses, including Heartbleed, CRIME and ROBOT.
sfp_tool_trufflehog        Searches through git repositories for high entropy strings and secrets, digging deep into commit history.
sfp_tool_wafw00f           Identify what web application firewall (WAF) is in use on the specified website.
sfp_tool_wappalyzer        Wappalyzer indentifies technologies on websites.
sfp_tool_whatweb           Identify what software is in use on the specified website.
sfp_torch                  Search Tor 'TORCH' search engine for mentions of the target domain.
sfp_torexits               Check if an IP adddress or netblock appears on the Tor Metrics exit node list.
sfp_trashpanda             Queries Trashpanda to gather intelligence about mentions of target in pastesites
sfp_trumail                Check whether an email is disposable
sfp_twilio                 Obtain information from Twilio about phone numbers. Ensure you have the Caller Name add-on installed in Twilio.
sfp_twitter                Gather name and location from Twitter profiles.
sfp_uceprotect             Check if a netblock or IP address is in the UCEPROTECT database.
sfp_urlscan                Search URLScan.io cache for domain information.
sfp_venmo                  Gather user information from Venmo API.
sfp_viewdns                Identify co-hosted websites and perform reverse Whois lookups using ViewDNS.info.
sfp_virustotal             Obtain information from VirusTotal about identified IP addresses.
sfp_voipbl                 Check if an IP address or netblock is malicious according to VoIP Blacklist (VoIPBL).
sfp_vxvault                Check if a domain or IP address is malicious according to VXVault.net.
sfp_webanalytics           Identify web analytics IDs in scraped webpages and DNS TXT records.
sfp_webframework           Identify the usage of popular web frameworks like jQuery, YUI and others.
sfp_webserver              Obtain web server banners to identify versions of web servers being used.
sfp_whatcms                Check web technology using WhatCMS.org API.
sfp_whois                  Perform a WHOIS look-up on domain names and owned netblocks.
sfp_whoisology             Reverse Whois lookups using Whoisology.com.
sfp_whoxy                  Reverse Whois lookups using Whoxy.com.
sfp_wigle                  Query WiGLE to identify nearby WiFi access points.
sfp_wikileaks              Search Wikileaks for mentions of domain names and e-mail addresses.
sfp_wikipediaedits         Identify edits to Wikipedia articles made from a given IP address or username.
sfp_xforce                 Obtain IP reputation and passive DNS information from IBM X-Force Exchange.
sfp_yandexdns              Check if a host would be blocked by Yandex DNS.
sfp_zetalytics             Query the Zetalytics database for hosts on your target domain(s).
sfp_zoneh                  Check if a hostname/domain appears on the zone-h.org 'special defacements' RSS feed.
```