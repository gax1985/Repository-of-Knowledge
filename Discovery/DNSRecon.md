

Scan a domain (`-d example.com`), use a dictionary to brute force hostnames (`-D /usr/share/wordlists/dnsmap.txt)`, do a standard scan (`-t std`), and save the output to a file (`–xml dnsrecon.xml`):

```console
root@kali:~# dnsrecon -d example.com -D /usr/share/wordlists/dnsmap.txt -t std --xml dnsrecon.xml
[*] Performing General Enumeration of Domain:example.com
[*] DNSSEC is configured for example.com
[*] DNSKEYs:
```

DNSRecon is a Python script that provides the ability to perform:

- Check all NS Records for Zone Transfers.
- Enumerate General DNS Records for a given Domain (MX, SOA, NS, A, AAAA, SPF and TXT).
- Perform common SRV Record Enumeration.
- Top Level Domain (TLD) Expansion.
- Check for Wildcard Resolution.
- Brute Force subdomain and host A and AAAA records given a domain and a wordlist.
- Perform a PTR Record lookup for a given IP Range or CIDR.
- Check a DNS Server Cached records for A, AAAA and CNAME
- Records provided a list of host records in a text file to check.
- Enumerate Hosts and Subdomains using Google
  
  
>[!info]
>
>### DNSRecon Features Explained

1. **Check all NS Records for Zone Transfers**:
    
    - **NS Records**: Name Server records that specify the authoritative DNS servers for a domain.
    - **Zone Transfers**: The process of copying DNS records from one DNS server to another. This feature checks if any of the NS records allow zone transfers, which can reveal all DNS records for the domain.
2. **Enumerate General DNS Records for a given Domain (MX, SOA, NS, A, AAAA, SPF, and TXT)**:
    
    - **MX**: Mail Exchange records, which specify mail servers for the domain.
    - **SOA**: Start of Authority records, which provide information about the DNS zone and its primary DNS server.
    - **NS**: Name Server records, as mentioned above.
    - **A**: Address records, which map domain names to IPv4 addresses.
    - **AAAA**: Address records, which map domain names to IPv6 addresses.
    - **SPF**: Sender Policy Framework records, which help prevent email spoofing.
    - **TXT**: Text records, which can contain arbitrary text data, often used for SPF, DKIM, etc.
3. **Perform common SRV Record Enumeration**:
    
    - **SRV Records**: Service records used to define the location of servers for specified services.
4. **Top Level Domain (TLD) Expansion**:
    
    - **TLD**: The last part of a domain name, such as `.com`, `.org`, `.net`. This feature expands the search to include all possible TLDs for a given domain name.
5. **Check for Wildcard Resolution**:
    
    - **Wildcard Resolution**: A DNS configuration where a wildcard DNS record (e.g., `*.example.com`) resolves to a specific IP address. This feature checks if wildcard DNS records are in use.
6. **Brute Force subdomain and host A and AAAA records given a domain and a wordlist**:
    
    - **Brute Force**: A method of systematically trying all possible combinations to find valid subdomains and hostnames.
    - **Wordlist**: A list of potential subdomains and hostnames used for brute-forcing.
7. **Perform a PTR Record lookup for a given IP Range or CIDR**:
    
    - **PTR Records**: Pointer records used for reverse DNS lookups, mapping IP addresses back to domain names.
    - **IP Range or CIDR**: Specifies the range of IP addresses to perform the reverse lookup on.
8. **Check a DNS Server Cached records for A, AAAA, and CNAME**:
    
    - **Cached Records**: DNS records stored temporarily by a DNS server to speed up subsequent queries.
    - **CNAME**: Canonical Name records, which alias one domain name to another.
9. **Records provided a list of host records in a text file to check**:
    
    - This feature allows you to provide a list of hostnames in a text file, and DNSRecon will check the DNS records for each hostname.
10. **Enumerate Hosts and Subdomains using Google**:
    
    - This feature uses Google search queries (Google Dorks) to find indexed subdomains and hosts related to the target domain.
  
  
  
Here is the output for dnsrecon -h :

```console
root@kali:~# dnsrecon -h
usage: dnsrecon [-h] [-d DOMAIN] [-n NS_SERVER] [-r RANGE] [-D DICTIONARY]
                [-f] [-a] [-s] [-b] [-y] [-k] [-w] [-z] [--threads THREADS]
                [--lifetime LIFETIME] [--tcp] [--db DB] [-x XML] [-c CSV]
                [-j JSON] [--iw] [--disable_check_recursion]
                [--disable_check_bindversion] [-V] [-v] [-t TYPE]

options:
  -h, --help            show this help message and exit
  -d DOMAIN, --domain DOMAIN
                        Target domain.
  -n NS_SERVER, --name_server NS_SERVER
                        Domain server to use. If none is given, the SOA of the target will be used. Multiple servers can be specified using a comma separated list.
  -r RANGE, --range RANGE
                        IP range for reverse lookup brute force in formats   (first-last) or in (range/bitmask).
  -D DICTIONARY, --dictionary DICTIONARY
                        Dictionary file of subdomain and hostnames to use for brute force.
  -f                    Filter out of brute force domain lookup, records that resolve to the wildcard defined IP address when saving records.
  -a                    Perform AXFR with standard enumeration.
  -s                    Perform a reverse lookup of IPv4 ranges in the SPF record with standard enumeration.
  -b                    Perform Bing enumeration with standard enumeration.
  -y                    Perform Yandex enumeration with standard enumeration.
  -k                    Perform crt.sh enumeration with standard enumeration.
  -w                    Perform deep whois record analysis and reverse lookup of IP ranges found through Whois when doing a standard enumeration.
  -z                    Performs a DNSSEC zone walk with standard enumeration.
  --threads THREADS     Number of threads to use in reverse lookups, forward lookups, brute force and SRV record enumeration.
  --lifetime LIFETIME   Time to wait for a server to respond to a query. default is 3.0
  --tcp                 Use TCP protocol to make queries.
  --db DB               SQLite 3 file to save found records.
  -x XML, --xml XML     XML file to save found records.
  -c CSV, --csv CSV     Save output to a comma separated value file.
  -j JSON, --json JSON  save output to a JSON file.
  --iw                  Continue brute forcing a domain even if a wildcard record is discovered.
  --disable_check_recursion
                        Disables check for recursion on name servers
  --disable_check_bindversion
                        Disables check for BIND version on name servers
  -V, --version         Show DNSrecon version
  -v, --verbose         Enable verbose
  -t TYPE, --type TYPE  Type of enumeration to perform.
                        Possible types:
                            std:      SOA, NS, A, AAAA, MX and SRV.
                            rvl:      Reverse lookup of a given CIDR or IP range.
                            brt:      Brute force domains and hosts using a given dictionary.
                            srv:      SRV records.
                            axfr:     Test all NS servers for a zone transfer.
                            bing:     Perform Bing search for subdomains and hosts.
                            yand:     Perform Yandex search for subdomains and hosts.
                            crt:      Perform crt.sh search for subdomains and hosts.
                            snoop:    Perform cache snooping against all NS servers for a given domain, testing
                                      all with file containing the domains, file given with -D option.
                        
                            tld:      Remove the TLD of given domain and test against all TLDs registered in IANA.
                            zonewalk: Perform a DNSSEC zone walk using NSEC records.
```