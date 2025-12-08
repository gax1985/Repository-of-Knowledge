

>[!command]
>
>`wapiti -u http://127.0.0.1 --scope folder -m sql' 
>
>>[!eplanation]
>>
>>Wapiti **crawls the web application**, **tests the content for SQL Injection vulnerabilities, and generates a report**!

1. `--scope folder`: This option defines the scope of the scan. The `folder` scope means that Wapiti will scan all URLs within the same directory as the base URL. In other words, it limits the scan to the web pages and resources that are within the same folder level of the provided URL (`http://127.0.0.1`).
    
2. `-m sql`: The `-m` option specifies the type of vulnerability to scan for. In this case, `sql` indicates that Wapiti should specifically check for SQL Injection vulnerabilities. SQL Injection vulnerabilities occur when an attacker can execute arbitrary SQL queries on the database through user input fields, potentially leading to data leakage, data corruption, or other malicious activities.
    

### What Does It Do?

When you run `wapiti -u http://127.0.0.1 --scope folder -m sql`, Wapiti performs the following actions:

1. **Crawling**: Wapiti starts by crawling the web application at `http://127.0.0.1`, collecting all the web pages and resources within the same directory level as the base URL.
    
2. **Testing for SQL Injection Vulnerabilities**: After the crawling phase, Wapiti tests the collected elements (such as forms, inputs, and URLs) for potential SQL Injection vulnerabilities. It attempts to inject various SQL payloads to see if the web application improperly handles user input, potentially allowing malicious SQL queries to be executed on the database.
    
3. **Reporting**: Once the scan is complete, Wapiti generates a report that summarizes the findings, including any identified SQL Injection vulnerabilities, their locations, and suggestions for remediation.
    

### Example Output

An example output from this specific Wapiti scan might look like this:

```
+-------------------------------------------------------------------------------------+
| Summary:                                                                            |
+-------------------------------------------------------------------------------------+
| * URL: http://127.0.0.1                                                             |
| * Scope: folder                                                                     |
+-------------------------------------------------------------------------------------+
| Vulnerabilities discovered:                                                         |
| * SQL Injection in http://127.0.0.1/products?id=1                                   |
| * SQL Injection in http://127.0.0.1/search?q=foo                                    |
+-------------------------------------------------------------------------------------+
```

This output shows a summary of the SQL Injection vulnerabilities discovered during the scan, along with their locations.