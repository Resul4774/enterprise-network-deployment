# Network Address Translation (NAT/PAT) & Security Configuration on Cisco IOS

This repository contains a Cisco Packet Tracer lab project demonstrating the implementation, validation, and security rule enforcement of Network Address Translation (NAT) and Port Address Translation (PAT) on an enterprise edge router (`R1-Edge`).

## Project Overview

The primary objective of this project is to simulate a realistic network environment where internal private IP addresses are dynamically translated to a public IP address via PAT (Overload). Additionally, security policies using Access Control Lists (ACLs) are integrated to govern traffic flow.

### Network Architecture & Specifications
* **Router:** Cisco ISR (`R1-Edge`)
* **Internal Interface (`GigabitEthernet0/0/0`):** Connected to the internal private LAN (`10.0.0.0/8`), configured as `ip nat inside`.
* **External Interface (`GigabitEthernet0/0/1`):** Connected to the external WAN/Cloud, configured as `ip nat outside` with a static public IP (`203.0.113.2`).
* **Routing:** Static default route (`0.0.0.0/0`) directed toward the external gateway.
* **Access Control:** Standard ACL enforcing authorized subnet translation and traffic boundaries.

---

Configuration Summary
Core configuration snippet applied on R1-Edge:

Plaintext
configure terminal
!
interface GigabitEthernet0/0/0
 ip address 10.0.0.1 255.255.255.0
 ip nat inside
 no shutdown
!
interface GigabitEthernet0/0/1
 ip address 203.0.113.2 255.255.255.0
 ip nat outside
 no shutdown
!
access-list 1 permit 10.0.0.0 0.255.255.255
ip nat inside source list 1 interface GigabitEthernet0/0/1 overload
ip route 0.0.0.0 0.0.0.0 GigabitEthernet0/0/1
end
Verification & Screenshots
1. Network Topology Overview
2. Connectivity & Security Testing (Ping Verification)
(Note: Successful pings demonstrate valid external connectivity through PAT, while filtered or unsuccessful test pings confirm that the configured security/ACL policies are actively restricting unauthorized or unintended traffic paths.)

3. NAT Translation Table
Active translation entries captured during real-time traffic flow:

4. Access List & NAT Rules
Usage Instructions
Download and open R1-Edge_NAT_PAT_Configuration.pkt using Cisco Packet Tracer.

Review the router running configuration and active ACL/NAT bindings.

Test communication flows from internal hosts to external destinations.
