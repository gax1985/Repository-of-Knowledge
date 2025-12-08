

## **1. Privileged EXEC Mode & Global Config Basics**

| Command              | Explanation                                                       | Significance                                                                          |
| -------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `enable`             | Switches from user EXEC mode (`>`) to privileged EXEC mode (`#`). | Required before making configuration changes or running advanced show/debug commands. |
| `configure terminal` | Enters global configuration mode.                                 | The starting point for all configuration tasks in IOS.                                |

## **2. Flow Record Configuration**

| Command                                                            | Explanation                                                | Significance                                                               |                                                                |                                             |
| ------------------------------------------------------------------ | ---------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------- | ------------------------------------------- |
| `flow record <record-name>`                                        | Creates or edits a Flexible NetFlow flow record.           | Defines the key (match) and non-key (collect) fields for traffic analysis. |                                                                |                                             |
| `description <text>`                                               | Adds a description to the record.                          | Helps document the purpose of the record for future reference.             |                                                                |                                             |
| `match {ip                                                         | ipv6} {destination                                         | source} address`                                                           | Sets IP/IPv6 source or destination address as a **key field**. | Keys define what constitutes a unique flow. |
| `match flow cts {source                                            | destination} group-tag`                                    | Matches Cisco TrustSec (CTS) group tags as key fields.                     | Useful for security policy and segmentation analysis.          |                                             |
| `match interface {input                                            | output}`                                                   | Uses the ingress or egress interface as a key field.                       | Allows per-interface flow differentiation.                     |                                             |
| `match ipv4 tos` / `match ipv6 traffic-class`                      | Matches ToS (IPv4) or Traffic Class (IPv6) as a key field. | Enables QoS and class-of-service analysis.                                 |                                                                |                                             |
| `match ipv4 protocol` / `match ipv6 protocol`                      | Matches L3 protocol number.                                | Differentiates flows by protocol (TCP, UDP, ICMP, etc.).                   |                                                                |                                             |
| `match transport source-port` / `match transport destination-port` | Matches TCP/UDP source/destination ports.                  | Enables application-level flow tracking.                                   |                                                                |                                             |
| `collect interface {input                                          | output}`                                                   | Adds ingress/egress interface as a **non-key field**.                      | Provides context without creating new flows.                   |                                             |
| `collect counter bytes [long]` / `collect counter packets [long]`  | Collects byte/packet counters for the flow.                | Essential for traffic volume measurement.                                  |                                                                |                                             |
| `collect timestamp sys-uptime {first                               | last}`                                                     | Records system uptime when first/last packet was seen.                     | Useful for flow timing and duration analysis.                  |                                             |
| `collect timestamp absolute {first                                 | last}`                                                     | Records absolute time for first/last packet.                               | Useful for correlating with external logs.                     |                                             |

## **3. Flow Monitor Configuration**

| Command                                                               | Explanation                             | Significance                                                  |                                          |
| --------------------------------------------------------------------- | --------------------------------------- | ------------------------------------------------------------- | ---------------------------------------- |
| `flow monitor <monitor-name>`                                         | Creates or edits a flow monitor.        | Ties together a flow record, cache, and optionally exporters. |                                          |
| `record <record-name>`                                                | Assigns a flow record to the monitor.   | Defines what data the monitor will collect.                   |                                          |
| `record netflow {ipv4                                                 | ipv6} original-input`                   | Uses predefined NetFlow record for ingress traffic.           | Quick deployment without custom records. |
| `cache type normal` / `cache type permanent`                          | Sets cache aging behavior.              | Controls how long flows are kept before export/removal.       |                                          |
| `cache timeout active <seconds>` / `cache timeout inactive <seconds>` | Sets active/inactive flow aging timers. | Balances freshness of data vs. processing load.               |                                          |
| `cache entries <number>`                                              | Sets maximum number of cache entries.   | Prevents memory exhaustion.                                   |                                          |
| `exporter <exporter-name>`                                            | Links a flow exporter to the monitor.   | Enables sending collected data to external collectors.        |                                          |

## **4. Flow Exporter Configuration**

| Command                         | Explanation                               | Significance                                       |                           |                                                 |
| ------------------------------- | ----------------------------------------- | -------------------------------------------------- | ------------------------- | ----------------------------------------------- |
| `flow exporter <exporter-name>` | Creates or edits a flow exporter.         | Defines where and how flow data is sent.           |                           |                                                 |
| `destination {hostname          | ip-address} [vrf <vrf-name>]`             | Sets the collector’s IP/hostname and optional VRF. | Determines export target. |                                                 |
| `export-protocol {netflow-v5    | netflow-v9                                | ipfix}`                                            | Chooses export format.    | v9/IPFIX allow flexible templates; v5 is fixed. |
| `transport udp <port>`          | Sets UDP port for export.                 | Must match collector’s listening port.             |                           |                                                 |
| `source <interface>`            | Sets source interface for export packets. | Ensures correct routing and NAT behavior.          |                           |                                                 |

## **5. Applying Flow Monitors to Interfaces**

| Command                     | Explanation                              | Significance                   |                                                                      |                                               |
| --------------------------- | ---------------------------------------- | ------------------------------ | -------------------------------------------------------------------- | --------------------------------------------- |
| `interface <type> <number>` | Enters interface configuration mode.     | Needed to apply flow monitors. |                                                                      |                                               |
| `{ip                        | ipv6} flow monitor <monitor-name> {input | output}`                       | Activates a flow monitor on an interface for ingress/egress traffic. | Without this, the monitor won’t collect data. |

## **6. Show & Verification Commands**

| Command                                                      | Explanation                                  | Significance                           |                                            |                                         |
| ------------------------------------------------------------ | -------------------------------------------- | -------------------------------------- | ------------------------------------------ | --------------------------------------- |
| `show flow record [<record-name>]`                           | Displays flow record details.                | Verifies match/collect fields.         |                                            |                                         |
| `show running-config flow record [<record-name>]`            | Shows config for a specific flow record.     | Confirms saved configuration.          |                                            |                                         |
| `show flow monitor [name] <monitor-name> [cache [format {csv | record                                       | table}] [statistics]]`                 | Displays monitor status, cache, and stats. | Key for troubleshooting and validation. |
| `show running-config flow monitor <monitor-name>`            | Shows config for a specific flow monitor.    | Confirms saved configuration.          |                                            |                                         |
| `show flow exporter <exporter-name>`                         | Displays exporter status.                    | Verifies export settings and counters. |                                            |                                         |
| `show running-config flow exporter <exporter-name>`          | Shows exporter configuration.                | Confirms saved configuration.          |                                            |                                         |
| `show flow interface <type> <number>`                        | Shows if NetFlow is enabled on an interface. | Quick operational check.               |                                            |                                         |

## **7. Related Supporting Commands**

| Command                             | Explanation                                     | Significance                                        |
| ----------------------------------- | ----------------------------------------------- | --------------------------------------------------- |
| `ip cef` / `ipv6 cef`               | Enables Cisco Express Forwarding for IPv4/IPv6. | Required for NetFlow to operate efficiently.        |
| `no ip flow monitor <monitor-name>` | Removes a flow monitor from an interface.       | Needed before modifying certain monitor parameters. |
