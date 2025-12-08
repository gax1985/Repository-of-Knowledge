di

### Steps to Perform a DNS Zone Transfer with `dig`

1. **Find the Authoritative Name Servers**: First, you need to find the authoritative name servers for the domain. You can do this with the following command:
    
    ```bash
    dig ns nscc.ca
    ```
    
    or :
    
>
>``host -t ns nscc.ca``



1. **Perform the Zone Transfer**: Once you have the authoritative name servers, you can attempt a zone transfer. Use the `AXFR` query type to request the transfer. For example, if `ns1.nscc.ca` is an authoritative name server, you would use:
    
    ```bash
    dig @ns1.nscc.ca nscc.ca axfr
    ```
    

### Example:

Here’s a complete example assuming `ns1.nscc.ca` is an authoritative server:

```bash
# Step 1: Find the authoritative name servers
dig ns nscc.ca

# Step 2: Perform the zone transfer
dig @ns1.nscc.ca nscc.ca axfr
```

