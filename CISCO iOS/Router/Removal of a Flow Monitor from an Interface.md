

You can’t delete a **flow monitor** while it’s still applied to an interface. The router is protecting you from breaking the config mid‑stream.

Here’s the safe removal sequence:

---

## 🛠 Step‑by‑Step: Removing a Flow Monitor

1. **Check where the monitor is applied**
    
    ```bash
    show running-config | include flow monitor
    ```
    
    or
    
    ```bash
    show flow monitor
    ```
    
    This will show you which interfaces have `ip flow monitor Flow-Monitor-IPv4 input` or `output`.
    
2. **Go into each interface and detach the monitor** For example, if it’s on `GigabitEthernet0/0/0`:
    
    ```bash
    configure terminal
    interface GigabitEthernet0/0/0
      no ip flow monitor Flow-Monitor-IPv4 input
      no ip flow monitor Flow-Monitor-IPv4 output
    exit
    ```
    
    Repeat for every interface where it’s applied.
    
3. **Verify it’s no longer in use**
    
    ```bash
    show running-config | include flow monitor
    ```
    
    If nothing shows up, you’re clear.
    
4. **Now remove the monitor itself**
    
    ```bash
    no flow monitor Flow-Monitor-IPv4
    ```
    
5. **(Optional) Clean up exporter and record** If you also want to remove the exporter and record:
    
    ```bash
    no flow exporter EXPORTER1
    no flow record RECORD1
    ```
    

---

## ✅ Key Takeaways

- You must **detach first, delete second**.
- The error you saw is IOS‑XE telling you the monitor is still bound to an interface.
- Always check with `show run | include flow monitor` before trying to delete.

---

👉 Mohammed, do you want me to draft you a **“removal checklist”** you can keep handy — so next time you can just follow it step by step without hitting dependency errors?