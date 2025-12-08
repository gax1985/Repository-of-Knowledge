


### Command 3: Nikto Super-Deluxe Scan
```python
elif web_application_choice == "6":

    print("\n\nCertainly! Your Wish is My Command! One Nikto Super-Deluxe Scan coming right up!\n\n")
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

    nikto_super_deluxe_command = subprocess.run(["nikto", "-host=http://" + ip_address])
    nikto_super_deluxe_command_output = nikto_super_deluxe_command.stdout
```

#### Explanation:
- **`-host=http://` + `ip_address`**: Specifies the target host for the scan. The `ip_address` variable holds the IP address of the target.
- **No `-Tuning` option**: Running Nikto without the `-Tuning` option performs a comprehensive scan, including all available tests. This is referred to as the "Super-Deluxe" scan in your script, providing a thorough assessment of the target's security.

### Summary
- The `-Tuning=a` option in Command 1 focuses on authentication bypass vulnerabilities.
- The `-Tuning=3` option in Command 2 focuses on information disclosure vulnerabilities.
- Command 3 performs a comprehensive scan, including all tests, by not specifying any tuning options.

These commands allow you to perform targeted and comprehensive scans using Nikto, based on the specific vulnerabilities you want to assess. Does this help clarify the commands and their options?