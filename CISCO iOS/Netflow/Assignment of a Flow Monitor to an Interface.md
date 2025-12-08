

Absolutely — this is the key step that actually makes your **Flexible NetFlow monitor** start collecting traffic. On an ISR 4321 (IOS‑XE), the workflow is:

---

## 🛠️ Steps to Apply a Flow Monitor to an Interface

1. **Make sure you already have:**
    
    - A **flow record** (e.g., `RECORD-IPv4`)
    - A **flow exporter** (e.g., `EXPORTER1`)
    - A **flow monitor** that ties them together (e.g., `MONITOR-IPv4`)
    
    Example:
    
    ```bash
    flow record RECORD-IPv4
      match ipv4 source address
      match ipv4 destination address
      match transport source-port
      match transport destination-port
      collect counter bytes
      collect counter packets
    !
    flow exporter EXPORTER1
      destination 192.168.20.2
      source GigabitEthernet0/0/0
      transport udp 2055
      export-protocol netflow-v9
    !
    flow monitor MONITOR-IPv4
      record RECORD-IPv4
      exporter EXPORTER1
    ```
    
2. **Apply the monitor to an interface**
    
    - Go into the interface you want to monitor:
        
        ```bash
        configure terminal
        interface GigabitEthernet0/0/0
          ip flow monitor MONITOR-IPv4 input
          ip flow monitor MONITOR-IPv4 output
        exit
        ```
        
    - `input` means monitor traffic **entering** the interface.
        
    - `output` means monitor traffic **leaving** the interface.
        
    - You can apply one monitor for input and one for output per interface.
        
3. **Verify**
    
    ```bash
    show flow monitor MONITOR-IPv4 cache
    show flow exporter EXPORTER1
    show running-config | section flow
    ```
    
    These commands confirm that the monitor is active and exporting flows.
    

---

## ⚠️ Common Pitfalls

- If you get the error **“Flow Monitor … is in use”** when deleting, it means you forgot to remove it from the interface first (`no ip flow monitor MONITOR-IPv4 input`).
- If you get **“The monitor does not have a valid record”**, it means you created a monitor but didn’t attach a record to it.
- Packet Tracer only supports the _legacy_ `ip flow ingress` style, not full Flexible NetFlow. On real ISR 4321 hardware or CML/GNS3, you’ll have the full `flow monitor` syntax.

---

✅ So the short recipe is: **create record → create exporter → create monitor → apply monitor to interface with `ip flow monitor <name> input/output`.**

---

Do you want me to also show you a **side‑by‑side comparison** of how you’d apply a monitor in **Packet Tracer (legacy NetFlow)** vs. **real ISR 4321 (Flexible NetFlow)**? That way you’ll know exactly what’s possible in each environment.