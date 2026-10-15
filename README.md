# Network Address Translation (NAT/PAT) Configuration on Cisco IOS

This repository contains a Cisco Packet Tracer lab project demonstrating the configuration and verification of Network Address Translation (NAT) and Port Address Translation (PAT) on an edge router (`R1-Edge`).

## Project Overview

The goal of this project is to simulate an enterprise network environment where internal private IP addresses are translated to a single public IP address using PAT (Overload) to communicate with external networks.

### Network Architecture
* **Router:** Cisco ISR (R1-Edge)
* **Internal Interface (`GigabitEthernet0/0/0`):** Connected to the internal LAN (`10.0.0.0/8`). Configured as `ip nat inside`.
* **External Interface (`GigabitEthernet0/0/1`):** Connected to the external segment/Cloud. Configured as `ip nat outside` with a static public IP (`203.0.113.2`).
* **Routing:** Default route (`0.0.0.0/0`) pointed toward the external interface.
