

>[!command]
>
>`wapiti -u http://127.0.0.1 --scope folder -m xss' 
>
>>[!eplanation]
>>
>>Wapiti **crawls the web application**, **tests the content for Cross-Site Scripting vulnerabilities, and generates a report**!


1. **Crawling**: Wapiti starts by crawling the web application at `http://localhost`, collecting all the web pages and resources within the same directory level as the base URL.
    
2. **Testing for XSS Vulnerabilities**: After the crawling phase, Wapiti tests the collected elements (such as forms, inputs, and URLs) for potential XSS vulnerabilities. It attempts to inject various payloads to see if the web application improperly handles user input, potentially leading to the execution of malicious scripts.
    
3. **Reporting**: Once the scan is complete, Wapiti generates a report that summarizes the findings, including any identified XSS vulnerabilities, their locations, and suggestions for remediation.


### Example Output

An example output from this specific Wapiti scan might look like this:

```
+-------------------------------------------------------------------------------------+
| Summary:                                                                            |
+-------------------------------------------------------------------------------------+
| * URL: http://localhost                                                             |
| * Scope: folder                                                                     |
+-------------------------------------------------------------------------------------+
| Vulnerabilities discovered:                                                         |
| * XSS in http://localhost/search?q=<script>alert('XSS')</script>                    |
| * XSS in http://localhost/comments?name=<script>alert('XSS')</script>               |
+-------------------------------------------------------------------------------------+
```