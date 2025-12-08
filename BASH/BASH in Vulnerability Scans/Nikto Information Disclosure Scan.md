


### Command 2: Nikto Information Disclosure Scan
```python
elif web_application_choice == "5":

    print("\n\nCertainly! Your Wish is My Command! One Nikto Information Disclosure Scan coming right up!\n\n")
    print("\n\n")
    print("Please Wait! I appreciate your patience")
    print("[*     ]")
    time.sleep(1)
    print("[**   ]")
    time.sleep(1)
    print("[***  ]")
    time.sleep(1)
    print("[**** ]")
    time.sleep(1)
    print("[*****]")

    nikto_information_disclosure_command = subprocess.run(["nikto", "-Tuning=3", "-host=http://" + ip_address])
    nikto_information_disclosure_command_output = nikto_information_disclosure_command.stdout
```

#### Explanation:
- **`-Tuning=3`**: This option tells Nikto to run tests related to **information disclosure** vulnerabilities. These tests check if the web application leaks sensitive information that could be useful to attackers.
- **`-host=http://` + `ip_address`**: Specifies the target host for the scan. The `ip_address` variable holds the IP address of the target.

