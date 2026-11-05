# packet-tracer-enterprise-network
Summary of a university project: multi-floor enterprise network designed and simulated in Cisco Packet Tracer.
# Enterprise Network Design (Cisco Packet Tracer)

A summary of a multi-floor enterprise network I designed and simulated in Cisco Packet Tracer for a university assignment (Network Essentials). The full assessed work is not published here.

![Network topology] <img width="786" height="663" alt="image" src="https://github.com/user-attachments/assets/4d4c0b66-95c6-457d-9eb3-81171def0c42" />


## Design

- **Topology:** star-bus hybrid. Each floor is its own star, with a switch connecting its devices, and the floor switches connect to a central company router. This keeps problems contained to one floor and makes troubleshooting simpler.
- **Floors:** ground (graphics and reception), first (game programming), second (story and music) and third (management and finance). Each floor has a data server, web server, DHCP server, wireless access point and workstations.
- **Equipment:** 2960 switches for fast local traffic and 2911 routers for routing between floors.
- **Cabling:** a central comms room on each floor keeps cable runs within the 100m copper limit for a 50m x 50m floor.

## Addressing plan

Each floor has its own /24 subnet (192.168.1.0 to 192.168.4.0), laid out the same way:

| Address | Use |
| --- | --- |
| .1 | Router (default gateway) |
| .2 / .3 | Data server / web server |
| .11 onwards | Fixed workstations |
| .150 to .249 | Wireless DHCP pool (100 devices) |

A default route sends traffic for unknown destinations to a simulated ISP router. Spare addresses on each floor leave room to grow without re-addressing. DHCP was set up for wireless devices, and basic connectivity was tested using ping.

## Security analysis

I analysed weaknesses in the design and proposed countermeasures. These were not implemented in the simulation:

- **Open routing between floors:** add access controls to limit access to data by role.
- **Unlocked wall outlets and switch ports:** enable port security so each port only accepts authorised devices.
- **Shared Wi-Fi password:** use individual logins with separate encryption for each user.

## What I learned

- Subnetting and planning an IP addressing scheme
- Configuring DHCP and a router default route
- Identifying network security risks and countermeasures

## Future improvements

- Add NAT configuration
- Implement the proposed security controls, such as port security and access lists
