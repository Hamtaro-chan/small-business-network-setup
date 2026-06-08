# Simple Small Business Network Design
This project simulates a small company network with 4 departments and a server room for 3 floor buliding, using Cisco Packet Tracer. The setup includes servers - DHCP, DNS, and web-server - routers, switchs, and end-devices.

### scenario
Tabby Music Company, a small music lesson business with 67 employees, teaches live, online video music lessons via its own streaming platform, “https://www.TabbyMusic.com” or "TabbyMusic.com". The network has been divided into 4 departments: the academic, the operational, the financial, and the IT department. 

**Topology:** 
5 switches, 1 multilayer router, 2 routers, 3 servers, and 10 end devices (excluding servers).

The operation department, on the first floor, has a front-PC, an oper-printer, the switch named “Switch-oper-dep”, and 2 supported PC: oper-PC2 and oper-PC1. This department connects to VLAN 10 using the IP subnet: 192.168.10/24.

The academic department has a “cam-acad” and an “acad-PC” connected with the switch “Switch-acad-dep”. This department uses VLAN 20 and IP subnet: 192.168.20.0/24

The finance department has 3 end devices: “finance-PC”, “Printer-finan”, and “finance-PC” connected with the switch “Switch-finan-dep”. The finance department is connected to VLAN 30 and the IP subnet at 192.168.30.0/24

The IT department has the switch named “Switch-IT” connected to the “Player-PC”. This department is connected to VLAN 40 and IP subnet: 192.168.40.24

In the server room, there are 3 servers: “DNS” for locating and storing DNS records, “DHCP” for assigning and managing IP addresses, and “web-server” for storing website files. All servers are connected to the switch named “server-switch”. 

Each department has its own switch for network security and traffic management. If the network in some departments fails, other departments can still work. Because there are many end devices, 1 switch is not enough, and we can also create firewall rules later to improve security. Every switch connects to a multilayer switch before going to the core router because the company has 4 departments + server room, and may add more departments later. I chose to use a multilayer switch, so it won’t have a problem with not enough ports. Also, since Tabby is an online music lesson business, the company needs a certain amount of speed for uploading videos, so it would be better to use a layer 3 switch for inter-VLAN and offload local inter-VLAN routing from the core router. Then, the core router connects to the ISP router, which leads to the WAN. The 3 servers have different 3 duties: DNS, Web Server, and DHCP. I separate them to improve server availability and minimize the risk exposure associated with potential system failures or security breaches.


### Subnet Table

| Subnet / CIDR | Default Gateway | Connected Devices | Purpose | VLAN / Port |
| :--- | :--- | :--- | :--- | :--- |
| *192.168.10.0/24* | `192.168.10.1` | front-PC, oper-PC1, oper-PC2, oper-printer | *Operational Department:* Handles front desk operations, student registrations, and customer support. | VLAN 10 |
| *192.168.20.0/24* | `192.168.20.1` | acad-PC, cam-acad | *Academic Department:* Dedicated to music instructors conducting live, online streaming video lessons. | VLAN 20 |
| *192.168.30.0/24* | `192.168.30.1` | finance-PC, Printer-finan, Finance-PC | *Finance Department:* Manages payroll, tuition transactions, and accounting files. | VLAN 30 |
| *192.168.40.0/24* | `192.168.40.1` | Player-PC (Admin PC) | *IT Department:* Administrative network operations and main management console hub. | VLAN 40 |
| *10.0.1.0/24* | `10.0.1.1` | Server-PT DHCP, Server-PT DNS, Server-PT web-server | *Server Room:* Local center hosting core infrastructure applications and assets. | VLAN 1 |
| *67.67.67.64/30* | `67.67.67.65` | ISP Router | *Internet Edge:* Serial or high-speed uplink interface routing directly to the WAN. | WAN Port |

## How to View
- Download Cisco Packet Tracer from "www.netacad.com/resources/lab-downloads?courseLang=en-US". Then, install the progress and open 'TabbyMusic-Small-business-network-project.pkt'

## Network Design
<img width="2024" height="1060" alt="image" src="https://github.com/user-attachments/assets/6187e390-49cc-434b-af82-f63c599e0415" />
