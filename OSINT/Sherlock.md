
```
$ sherlock -h
usage: sherlock [-h] [--version] [--verbose] [--folderoutput FOLDEROUTPUT]
                [--output OUTPUT] [--tor] [--unique-tor] [--csv] [--xlsx]
                [--site SITE_NAME] [--proxy PROXY_URL] [--dump-response]
                [--json JSON_FILE] [--timeout TIMEOUT] [--print-all]
                [--print-found] [--no-color] [--browse] [--local] [--nsfw]
                USERNAMES [USERNAMES ...]

Sherlock: Find Usernames Across Social Networks (Version 0.15.0)

positional arguments:
  USERNAMES             One or more usernames to check with social
                        networks. Check similar usernames using {?}
                        (replace to '_', '-', '.').

options:
  -h, --help            show this help message and exit
  --version             Display version information and dependencies.
  --verbose, -v, -d, --debug
                        Display extra debugging information and metrics.
  --folderoutput FOLDEROUTPUT, -fo FOLDEROUTPUT
                        If using multiple usernames, the output of the
                        results will be saved to this folder.
  --output OUTPUT, -o OUTPUT
                        If using single username, the output of the result
                        will be saved to this file.
  --tor, -t             Make requests over Tor; increases runtime; requires
                        Tor to be installed and in system path.
  --unique-tor, -u      Make requests over Tor with new Tor circuit after
                        each request; increases runtime; requires Tor to be
                        installed and in system path.
  --csv                 Create Comma-Separated Values (CSV) File.
  --xlsx                Create the standard file for the modern Microsoft
                        Excel spreadsheet (xlsx).
  --site SITE_NAME      Limit analysis to just the listed sites. Add
                        multiple options to specify more than one site.
  --proxy PROXY_URL, -p PROXY_URL
                        Make requests over a proxy. e.g.
                        socks5://127.0.0.1:1080
  --dump-response       Dump the HTTP response to stdout for targeted
                        debugging.
  --json JSON_FILE, -j JSON_FILE
                        Load data from a JSON file or an online, valid,
                        JSON file.
  --timeout TIMEOUT     Time (in seconds) to wait for response to requests
                        (Default: 60)
  --print-all           Output sites where the username was not found.
  --print-found         Output sites where the username was found (also if
                        exported as file).
  --no-color            Don't color terminal output
  --browse, -b          Browse to all results on default browser.
  --local, -l           Force the use of the local data.json file.
  --nsfw                Include checking of NSFW sites from default list.
```



The **Sherlock** OSINT tool is designed to track down social media accounts by searching for a specific username across hundreds of platforms. Here's a demonstration of its capabilities:

>[!video] 
>>[(61) find social media accounts with Sherlock (in 5 MIN) - YouTube](https://www.youtube.com/watch?v=KdZvxxLsN3E&t=1s)


### **Basic Usage**

To search for a username, you simply need to provide the username as an argument:

bash

```
sherlock user123
```

### **Searching Multiple Usernames**

You can search for multiple usernames at once:

bash

```
sherlock user1 user2 user3
```

### **Searching on Specific Sites**

If you want to search for a username on a specific site, you can specify the site name:

bash

```
sherlock --site twitch user123
```

### **Searching for Similar Usernames**

Sherlock can also search for usernames that are similar to the one provided by replacing characters with hyphens, underscores, or periods:

bash

```
sherlock user?123
```

### **Using a Proxy**

To remain anonymous while searching, you can route your queries through a proxy:

bash

```
sherlock --proxy http://proxy.example.com user123
```

### **Output Options**

Sherlock provides various output options, such as saving results to a CSV file, an Excel file, or a folder:

bash

```
sherlock --csv user123
sherlock --xlsx user123
sherlock --folderoutput results user123
```

### **Additional Features**

- **Verbose Output:** Display extra debugging information and metrics.
    
- **Tor Support:** Make requests over Tor for increased anonymity.
    
- **Timeout Settings:** Adjust the timeout for queries.
    
- **Print All Output:** Print all the social networks queried and the reasons for not finding the username.
    
- **Browse Results:** View the job result page in a browser.
    
- **Search NSFW Sites:** Include NSFW sites in the search.
    

Sherlock is a powerful tool for gathering intelligence on a target by leveraging the design features of social media sites to provide URLs with usernames. It's lightweight, simple to use, and perfect for ethical hackers and researchers.