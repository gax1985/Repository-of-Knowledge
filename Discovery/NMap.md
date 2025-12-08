

# Stealth Scan 



>[!command]
>
>``sudo nmap -sS nscc.ca``
>
>![[Pasted image 20240911090913.png]]


![[Pasted image 20240911091003.png]]


### Nmap -sS (Stealth Scan) Explanation

The `-sS` option in Nmap is used to perform a **SYN scan**, also known as a **stealth scan** or **half-open scan**. This type of scan is popular because it is faster and less likely to be detected by firewalls and intrusion detection systems (IDS) compared to a full TCP connect scan.

### How It Works:

1. **SYN Packet**:
    
    - Nmap sends a SYN packet (the first step in the TCP handshake) to the target port.
2. **Response**:
    
    - If the port is open, the target responds with a SYN-ACK packet.
    - If the port is closed, the target responds with an RST packet.
3. **Half-Open**:
    
    - Nmap does not complete the TCP handshake. Instead, it sends an RST packet to tear down the connection after receiving the SYN-ACK.
    - This “half-open” state makes the scan less detectable because it doesn’t establish a full connection.

### Advantages:

- **Stealthy**: Less likely to be logged by the target system.
- **Fast**: Quicker than a full TCP connect scan because it doesn’t complete the handshake.

### Example Command:

```bash
nmap -sS example.com
```

### Use Cases:

- **Penetration Testing**: To discover open ports on a target system without being easily detected.
- **Network Auditing**: To check for open ports and potential vulnerabilities in a network.

### Important Considerations:

- **Permissions**: Ensure you have permission to scan the target network to avoid legal issues.
- **Detection**: While stealthier than a full connect scan, sophisticated IDS/IPS systems can still detect SYN scans.



# Network Sweeping 


### Explanation

The `-sn` option in Nmap is used for **host discovery** without performing a port scan. This is often referred to as a “ping scan” or “network sweep.” It helps identify which hosts are up and running on a network.

### How It Works:

1. **Ping Scan**:
    
    - Nmap sends **ICMP echo requests (ping) to the specified IP addresses**.
    - **It may also send TCP SYN packets to port 443 and TCP ACK packets to port 80 to determine if hosts are up**.
2. **No Port Scan**:
    
    - Unlike other Nmap scans, `-sn` does not scan for open ports. It only checks if the hosts are online.

### Example Command:

```bash
nmap -sn 192.168.4.0/24 -oG hosts.txt
```

### Command Breakdown:

- **192.168.4.0/24**: This specifies the target network range. The `/24` indicates a subnet mask of 255.255.255.0, covering IP addresses from 192.168.4.0 to 192.168.4.255.
- **-oG hosts.txt**: This option outputs the results in a grepable format to the file `hosts.txt`. This format is useful for further processing with other tools or scripts.

### Use Cases:

- **Network Inventory**: Quickly identify all active devices on a network.
- **Pre-Scan**: Determine which hosts are up before performing more detailed scans.
- **Monitoring**: Regularly check which devices are online in a network.

### Important Considerations:

- **Permissions**: Ensure you have permission to scan the network to avoid legal issues.
- **Firewall and IDS**: Some firewalls and intrusion detection systems may block or log ping scans.



## Grepping The Results : 


>[!command]
>
>``cat hosts.txt | grep Up``
>
>![[Pasted image 20240911091514.png]]
>



# Service Enumeration 


>[!command]
>
>``nmap -sV 192.168.4.1``
>
>![[Pasted image 20240911091917.png]]

### Explanation

The `-sV` option in Nmap is used for **version detection**. This command helps identify the versions of services running on open ports of the target host.

### Command Breakdown:

```bash
nmap -sV 192.168.4.1
```

- **nmap**: The tool being used for network scanning.
- **-sV**: This option enables version detection. Nmap will probe open ports to determine what service and version are running.
- **192.168.4.1**: The target IP address to scan.

### How It Works:

1. **Port Scanning**:
    
    - Nmap first performs a port scan to identify open ports on the target host.
2. **Service Probing**:
    
    - For each open port, Nmap sends additional probes to gather information about the service running on that port.
    - It compares the responses to a database of known service signatures to determine the service and its version.
3. **Output**:
    
    - The results include the port number, state (open/closed/filtered), service name, and version information.

### Example Output:

```plaintext
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3
80/tcp   open  http    Apache httpd 2.4.29 ((Ubuntu))
443/tcp  open  https   Apache httpd 2.4.29 ((Ubuntu))
```

### Use Cases:

- **Security Audits**: Identify outdated or vulnerable services running on a network.
- **Network Inventory**: Document the versions of services running on various hosts.
- **Penetration Testing**: Gather detailed information about target services to exploit known vulnerabilities.

### Important Considerations:

- **Permissions**: Ensure you have authorization to scan the target network to avoid legal issues.
- **Firewall and IDS**: Some firewalls and intrusion detection systems may detect and block version detection probes.


# OS Fingerprinting



>[!command]
>
>``nmap -O 192.168.4.1``
>
>![[Pasted image 20240911092014.png]]


### Explanation

The `-O` option in Nmap is used for **operating system detection**. This command helps identify the operating system running on the target host.

### Command Breakdown:

```bash
nmap -O 192.168.4.1
```

- **nmap**: The tool being used for network scanning.
- **-O**: This option enables operating system detection. Nmap will analyze the responses from the target to determine the operating system.
- **192.168.4.1**: The target IP address to scan.

### How It Works:

1. **Port Scanning**:
    
    - Nmap first performs a port scan to identify open ports on the target host.
2. **OS Fingerprinting**:
    
    - Nmap sends a series of TCP and UDP packets to the target.
    - It analyzes the responses to these packets, comparing them to a database of known OS fingerprints.
    - Based on the responses, Nmap attempts to identify the operating system and its version.

### Example Output:

```plaintext
OS details: Linux 2.6.32 - 3.10
Network Distance: 1 hop
```

### Use Cases:

- **Security Audits**: Identify the operating systems running on network devices to assess potential vulnerabilities.
- **Network Inventory**: Document the operating systems in use across a network.
- **Penetration Testing**: Gather detailed information about target systems to exploit known vulnerabilities.

### Important Considerations:

- **Permissions**: Ensure you have authorization to scan the target network to avoid legal issues.
- **Accuracy**: OS detection may not always be 100% accurate, especially if the target uses firewalls or other security measures to obfuscate responses.
