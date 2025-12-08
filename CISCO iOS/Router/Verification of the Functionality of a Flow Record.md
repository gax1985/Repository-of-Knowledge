

Verifying NetFlow is enabled on an interface is an important step, and the exact commands differ depending on whether you’re on **legacy NetFlow (Packet Tracer)** or **Flexible NetFlow (real ISR 4321 / IOS‑XE)**. Here’s how you can check:

---

## 🛠 On a Real ISR 4321 (IOS‑XE, Flexible NetFlow)

1. **Check interface configuration**
    
    ```bash
    show running-config | section interface
    ```
    
    Look for lines like:
    
    ```
    ip flow monitor MONITOR-IPv4 input
    ip flow monitor MONITOR-IPv4 output
    ```
    
    That confirms the monitor is applied.
    
2. **Check all interfaces with NetFlow applied**
    
    ```bash
    show flow interface
    ```
    
    This lists which interfaces have monitors attached and whether they’re input/output.
    
3. **Check the monitor cache**
    
    ```bash
    show flow monitor MONITOR-IPv4 cache
    ```
    
    If you see active flow entries (source/destination IPs, ports, counters), NetFlow is running.
    
4. **Check exporter status**
    
    ```bash
    show flow exporter EXPORTER1
    ```
    
    Confirms packets are being exported to the collector.
    

---

## 🛠 On Packet Tracer (Legacy NetFlow)

Packet Tracer doesn’t support full Flexible NetFlow, so you verify with the older commands:

1. **Check interface NetFlow status**
    
    ```bash
    show ip flow interface
    ```
    
    This shows which interfaces have `ip flow ingress` enabled.
    
2. **Check the flow cache**
    
    ```bash
    show ip cache flow
    ```
    
    Displays active flows being tracked.
    
3. **Check exporter configuration**
    
    ```bash
    show ip flow export
    ```
    
    Confirms the destination IP/port and export version.
    

---

## ✅ Quick Checklist

- **IOS‑XE (real 4321):** `show flow interface`, `show flow monitor <name> cache`, `show flow exporter <name>`.
- **Packet Tracer:** `show ip flow interface`, `show ip cache flow`, `show ip flow export`.

---

## 🔍 NetFlow Verification Cheat Sheet

|Task|Packet Tracer (Legacy NetFlow)|Real ISR 4321 (IOS‑XE, Flexible NetFlow)|
|---|---|---|
|**Check if NetFlow is applied to an interface**|`show ip flow interface` → lists interfaces with `ip flow ingress`enabled|`show flow interface` → shows which interfaces have monitors applied (input/output)|
|**Check active flows**|`show ip cache flow` → displays current flow cache entries (source/dest IP, ports, counters)|`show flow monitor MONITOR-IPv4 cache` → shows flow records being collected by the monitor|
|**Check exporter configuration**|`show ip flow export` → shows destination IP, port, and version|`show flow exporter EXPORTER1` → shows exporter status, packets sent, destination, protocol|
|**Check running config**|`show running-config|include ip flow`|`show running-config|include flow monitor`(or`section flow`)|
|**Confirm traffic is being exported**|Look for incrementing packet counters in `show ip flow export`|Look for incrementing packet counters in `show flow exporter EXPORTER1`|

---

## ✅ Quick Workflow

1. **Start with interface check** (`show ip flow interface` or `show flow interface`).
2. **Look at the cache** (`show ip cache flow` or `show flow monitor <name> cache`).
3. **Confirm exporter is active** (`show ip flow export` or `show flow exporter <name>`).
4. **Generate traffic** (ping, HTTP, etc.) and re‑run the commands — counters should increase if NetFlow is working.

---

👉 Mohammed, would you like me to also create a **“lab verification script”** — a short sequence of commands you can run in order (both PT and real ISR) — so you don’t have to remember which ones to type each time? That way you can just copy‑paste and check NetFlow in seconds.