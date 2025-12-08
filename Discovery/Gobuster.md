

To **Brute-Force** our way into a **Domain's Directories** : 


>[!command]
>
>``gobuster dir -u nscc.ca -w directories.txt``



#### Explanation 



- **gobuster**: This is the tool being used. Gobuster is a tool used to brute-force URIs (directories and files) in web sites and DNS subdomains (with wildcard support).
    
- **dir**: This specifies the mode Gobuster is running in. The `dir` mode is used for directory brute-forcing.
    
- **-u nscc.ca**: The `-u` flag specifies the URL to target. In this case, it’s `nscc.ca`.
    
- **-w directories.txt**: The `-w` flag specifies the wordlist to use. Here, `directories.txt` is the file containing a list of directory names to brute-force.
    

### Other Gobuster Modules:

Gobuster has several modules that can be used for different types of brute-forcing:

 **VHOST**:
    
    - **Command**: `gobuster vhost -u http://example.com -w wordlist.txt`
    - **Description**: This mode is used to brute-force virtual host names on a target web server.
 **S3**:
    
    - **Command**: `gobuster s3 -b examplebucket -w wordlist.txt`
    - **Description**: This mode is used to brute-force S3 bucket names.
 **Fuzz**:
    
    - **Command**: `gobuster fuzz -u http://example.com/FUZZ -w wordlist.txt`
    - **Description**: This mode is used for general fuzzing of URLs.
 **DNS**:
    
    - **Command**: `gobuster dns -d example.com -w wordlist.txt`
    - **Description**: This mode is used to brute-force DNS subdomains.

![[Pasted image 20240911085046.png]]
 **TFTP**:
    
    - **Command**: `gobuster tftp -u tftp://example.com -w wordlist.txt`
    - **Description**: This mode is used to brute-force TFTP servers.

Each module is designed for a specific type of brute-forcing, making Gobuster a versatile tool for penetration testing and security assessments.



