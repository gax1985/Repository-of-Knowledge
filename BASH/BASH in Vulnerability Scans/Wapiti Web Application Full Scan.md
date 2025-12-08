


>[!command]
>
>`wapiti -u http://127.0.0.1' 
>
>>[!eplanation]
>>
>>The `-u` is the option to specify the target URL for the scan.

Wapiti performs the following actions:

1. **Initial Analysis**: Wapiti crawls the web application, starting from the root URL (http://localhost), and collects all reachable pages, links, forms, and other inputs that can be interacted with.
    
2. **Vulnerability Checks**: Wapiti then tests these collected elements for various types of vulnerabilities, including but not limited to:
    
    - **Cross-Site Scripting (XSS)**: Identifies if the application is vulnerable to XSS attacks where malicious scripts can be injected into web pages viewed by other users.
        
    - **SQL Injection**: Checks if the application allows malicious SQL queries to be executed in the database.
        
    - **File Handling**: Tests for vulnerabilities related to file uploads and handling.
        
    - **Command Execution**: Identifies if the application allows execution of arbitrary commands.
        
    - **Backup and Source Files**: Searches for publicly accessible backup or source files that shouldn't be exposed.
        
3. **Reporting**: After the scan is complete, Wapiti generates a report that summarizes the findings, including any identified vulnerabilities, their severity levels, and suggestions for remediation.
    

### Example Output

An example output from a Wapiti scan might look like this:

```
+-------------------------------------------------------------------------------------+
| Summary:                                                                            |
+-------------------------------------------------------------------------------------+
| * URL: http://localhost                                                             |
| * Scope: folder                                                                     |
+-------------------------------------------------------------------------------------+
| Vulnerabilities discovered:                                                         |
| * XSS in http://localhost/search?q=foo                                              |
| * SQL Injection in http://localhost/products?id=1                                   |
| * Insecure file upload in http://localhost/upload                                   |
+-------------------------------------------------------------------------------------+
```

This output shows a summary of the vulnerabilities discovered during the scan, along with their locations.

### Customizing the Scan

You can customize the Wapiti scan by adding additional options. For example, to include custom HTTP headers or to specify the scope of the scan, you can use options like:

bash

```
wapiti -u http://localhost -H "Authorization: Bearer <token>" --scope folder
```