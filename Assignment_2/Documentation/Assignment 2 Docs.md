# Assignment 2

## Anthony Legg #03007276

Using Packet Tracer and GNS3 Due: Due: by Monday May 23 

Where to hand in: submit to Michael Holtz via Teams 

Late Penalty: 10% per day late 

<img src="image-20220427161149719.png" alt="image-20220427161149719" style="zoom:67%;" />

<img src="image-20220427162032261.png" alt="image-20220427162032261" style="zoom:67%;" />

# Learning Objectives

1. Understand, evaluate and implement designs for facilitating large scale wide area networks. 
2. Plan and deploy mechanisms for secure network information exchange. 
3. Understand, evaluate and implement solutions for network virtualisation. 
4. Design and implement fault tolerant solutions for high availability of local area and wide  area networks. 
5. Adapt the above tasks as required for specific ICT contexts and/or organisational domains.

## Overview 
Tyrell Corp is opening a new head office site. You have been asked to provide a submission for the  network LAN and WAN design as per the following customer specifications. Your predecessor had agreed a base design for both the LAN and WAN, however there are a number  of decisions to be made and full design specification to be supplied including proof of concept  configurations and testing. Refer to the LAN diagram in the appendix. 
### Special Note 
> This assessment has a special emphasis on critical evaluation. This means that where possible you  are to describe why you have chosen the various features / technologies and give consideration for   alternative solutions. Use the customer questions / requirements below in red to guide you. 

## Head Office LAN Network - Customer Specifications

The customer requires a hierarchical design with discrete Access, Distribution and Core layers providing for availability, scalability and security.
You are tasked with designing: 

  - The Core layer
  - WAN edge block
  - User access block

The core design must allow for additional distribution blocks to be added in the future. 

### User Departments 

The user access block will provide for 4 main departments. Each department will exist within its own  subnet. You have been allocated the network range **10.7.0.0/16** to cater for all required subnets  including point to point addressing and management.
  - Admin (12 staff)
  - Sales & Marketing (60 staff)
  - HR (20 staff)
  - Finance (20 staff) 

Growth for each department is not expected to exceed 100%.

### Subnetting

The customer has requested that subnet allocations are easy to summarise, understand and support. 
1. You must describe why this is true for your design.
    I have created the subnets using /24 CIDRs. These are commonly used, have a large number of user IP addresses which can be allocated in future as needed. End user subnets start at the 10.7.1.0/24 and end at 10.7.4.0/24. The 10.7.0.0/24 address space has been allocated to point-to-point connections, this makes it easier to keep track of addresses that are exclusively for the network infrastructure. This also keeps a large address space in reserve for future expansion of the network. An additional subnet has been created for loopback addressing, these addresses are to be allocated as needed for routing and testing purposes. Unused address space has approx. ____ IP addresses unused.
2. You must provide documentation that lists each of the IP Subnets (including L3 links) and what they are used for. 

| Subnet Name | Allocated Size | Address  | Mask | Dec Mask      | Assignable Range      | Broadcast  |
| ----------- | -------------- | -------- | ---- | ------------- | --------------------- | ---------- |
| P2P         | 254            | 10.7.0.0 | /24  | 255.255.255.0 | 10.7.0.1 - 10.7.0.254 | 10.7.0.255 |
| Finance     | 254            | 10.7.1.0 | /24  | 255.255.255.0 | 10.7.1.1 - 10.7.1.254 | 10.7.1.255 |
| Marketing   | 254            | 10.7.2.0 | /24  | 255.255.255.0 | 10.7.2.1 - 10.7.2.254 | 10.7.2.255 |
| Admin       | 254            | 10.7.3.0 | /24  | 255.255.255.0 | 10.7.3.1 - 10.7.3.254 | 10.7.3.255 |
| Sales       | 254            | 10.7.4.0 | /24  | 255.255.255.0 | 10.7.4.1 - 10.7.4.254 | 10.7.4.255 |

**Consider** how device management addressing will be allocated. Ensure some point-to-point /30  networks are set aside for the WAN design. 

| A         | 2    | 2    | 10.7.0.0   | /30  | 255.255.255.252 | 10.7.0.1 - 10.7.0.2     | 10.7.0.3   |
| --------- | ---- | ---- | ---------- | ---- | --------------- | ----------------------- | ---------- |
| B         | 2    | 2    | 10.7.0.4   | /30  | 255.255.255.252 | 10.7.0.5 - 10.7.0.6     | 10.7.0.7   |
| C         | 2    | 2    | 10.7.0.8   | /30  | 255.255.255.252 | 10.7.0.9 - 10.7.0.10    | 10.7.0.11  |
| D         | 2    | 2    | 10.7.0.12  | /30  | 255.255.255.252 | 10.7.0.13 - 10.7.0.14   | 10.7.0.15  |
| E         | 2    | 2    | 10.7.0.16  | /30  | 255.255.255.252 | 10.7.0.17 - 10.7.0.18   | 10.7.0.19  |
| F         | 2    | 2    | 10.7.0.20  | /30  | 255.255.255.252 | 10.7.0.21 - 10.7.0.22   | 10.7.0.23  |
| G         | 2    | 2    | 10.7.0.24  | /30  | 255.255.255.252 | 10.7.0.25 - 10.7.0.26   | 10.7.0.27  |
| H         | 2    | 2    | 10.7.0.28  | /30  | 255.255.255.252 | 10.7.0.29 - 10.7.0.30   | 10.7.0.31  |
| I         | 2    | 2    | 10.7.0.32  | /30  | 255.255.255.252 | 10.7.0.33 - 10.7.0.34   | 10.7.0.35  |
| J         | 2    | 2    | 10.7.0.36  | /30  | 255.255.255.252 | 10.7.0.37 - 10.7.0.38   | 10.7.0.39  |
| K         | 2    | 2    | 10.7.0.40  | /30  | 255.255.255.252 | 10.7.0.41 - 10.7.0.42   | 10.7.0.43  |
| L         | 2    | 2    | 10.7.0.44  | /30  | 255.255.255.252 | 10.7.0.45 - 10.7.0.46   | 10.7.0.47  |
| M         | 2    | 2    | 10.7.0.48  | /30  | 255.255.255.252 | 10.7.0.49 - 10.7.0.50   | 10.7.0.51  |
| N         | 2    | 2    | 10.7.0.52  | /30  | 255.255.255.252 | 10.7.0.53 - 10.7.0.54   | 10.7.0.55  |
| O         | 2    | 2    | 10.7.0.56  | /30  | 255.255.255.252 | 10.7.0.57 - 10.7.0.58   | 10.7.0.59  |
| P         | 2    | 2    | 10.7.0.60  | /30  | 255.255.255.252 | 10.7.0.61 - 10.7.0.62   | 10.7.0.63  |
| Q         | 2    | 2    | 10.7.0.64  | /30  | 255.255.255.252 | 10.7.0.65 - 10.7.0.66   | 10.7.0.67  |
| R         | 2    | 2    | 10.7.0.68  | /30  | 255.255.255.252 | 10.7.0.69 - 10.7.0.70   | 10.7.0.71  |
| S         | 2    | 2    | 10.7.0.72  | /30  | 255.255.255.252 | 10.7.0.73 - 10.7.0.74   | 10.7.0.75  |
| Subnet027 | 2    | 2    | 10.7.0.76  | /30  | 255.255.255.252 | 10.7.0.77 - 10.7.0.78   | 10.7.0.79  |
| Subnet028 | 2    | 2    | 10.7.0.80  | /30  | 255.255.255.252 | 10.7.0.81 - 10.7.0.82   | 10.7.0.83  |
| Subnet029 | 2    | 2    | 10.7.0.84  | /30  | 255.255.255.252 | 10.7.0.85 - 10.7.0.86   | 10.7.0.87  |
| Subnet030 | 2    | 2    | 10.7.0.88  | /30  | 255.255.255.252 | 10.7.0.89 - 10.7.0.90   | 10.7.0.91  |
| Subnet031 | 2    | 2    | 10.7.0.92  | /30  | 255.255.255.252 | 10.7.0.93 - 10.7.0.94   | 10.7.0.95  |
| Subnet032 | 2    | 2    | 10.7.0.96  | /30  | 255.255.255.252 | 10.7.0.97 - 10.7.0.98   | 10.7.0.99  |
| Subnet033 | 2    | 2    | 10.7.0.100 | /30  | 255.255.255.252 | 10.7.0.101 - 10.7.0.102 | 10.7.0.103 |
| Subnet034 | 2    | 2    | 10.7.0.104 | /30  | 255.255.255.252 | 10.7.0.105 - 10.7.0.106 | 10.7.0.107 |
| Subnet035 | 2    | 2    | 10.7.0.108 | /30  | 255.255.255.252 | 10.7.0.109 - 10.7.0.110 | 10.7.0.111 |
| Subnet036 | 2    | 2    | 10.7.0.112 | /30  | 255.255.255.252 | 10.7.0.113 - 10.7.0.114 | 10.7.0.115 |
| Subnet037 | 2    | 2    | 10.7.0.116 | /30  | 255.255.255.252 | 10.7.0.117 - 10.7.0.118 | 10.7.0.119 |
| Subnet038 | 2    | 2    | 10.7.0.120 | /30  | 255.255.255.252 | 10.7.0.121 - 10.7.0.122 | 10.7.0.123 |
| Subnet039 | 2    | 2    | 10.7.0.124 | /30  | 255.255.255.252 | 10.7.0.125 - 10.7.0.126 | 10.7.0.127 |
| Subnet040 | 2    | 2    | 10.7.0.128 | /30  | 255.255.255.252 | 10.7.0.129 - 10.7.0.130 | 10.7.0.131 |
| Subnet041 | 2    | 2    | 10.7.0.132 | /30  | 255.255.255.252 | 10.7.0.133 - 10.7.0.134 | 10.7.0.135 |
| Subnet042 | 2    | 2    | 10.7.0.136 | /30  | 255.255.255.252 | 10.7.0.137 - 10.7.0.138 | 10.7.0.139 |
| Subnet043 | 2    | 2    | 10.7.0.140 | /30  | 255.255.255.252 | 10.7.0.141 - 10.7.0.142 | 10.7.0.143 |
| Subnet044 | 2    | 2    | 10.7.0.144 | /30  | 255.255.255.252 | 10.7.0.145 - 10.7.0.146 | 10.7.0.147 |
| Subnet045 | 2    | 2    | 10.7.0.148 | /30  | 255.255.255.252 | 10.7.0.149 - 10.7.0.150 | 10.7.0.151 |
| Subnet046 | 2    | 2    | 10.7.0.152 | /30  | 255.255.255.252 | 10.7.0.153 - 10.7.0.154 | 10.7.0.155 |
| Subnet047 | 2    | 2    | 10.7.0.156 | /30  | 255.255.255.252 | 10.7.0.157 - 10.7.0.158 | 10.7.0.159 |
| Subnet048 | 2    | 2    | 10.7.0.160 | /30  | 255.255.255.252 | 10.7.0.161 - 10.7.0.162 | 10.7.0.163 |
| Subnet049 | 2    | 2    | 10.7.0.164 | /30  | 255.255.255.252 | 10.7.0.165 - 10.7.0.166 | 10.7.0.167 |
| Subnet050 | 2    | 2    | 10.7.0.168 | /30  | 255.255.255.252 | 10.7.0.169 - 10.7.0.170 | 10.7.0.171 |
| Subnet051 | 2    | 2    | 10.7.0.172 | /30  | 255.255.255.252 | 10.7.0.173 - 10.7.0.174 | 10.7.0.175 |
| Subnet052 | 2    | 2    | 10.7.0.176 | /30  | 255.255.255.252 | 10.7.0.177 - 10.7.0.178 | 10.7.0.179 |
| Subnet053 | 2    | 2    | 10.7.0.180 | /30  | 255.255.255.252 | 10.7.0.181 - 10.7.0.182 | 10.7.0.183 |
| Subnet054 | 2    | 2    | 10.7.0.184 | /30  | 255.255.255.252 | 10.7.0.185 - 10.7.0.186 | 10.7.0.187 |
| Subnet055 | 2    | 2    | 10.7.0.188 | /30  | 255.255.255.252 | 10.7.0.189 - 10.7.0.190 | 10.7.0.191 |
| Subnet056 | 2    | 2    | 10.7.0.192 | /30  | 255.255.255.252 | 10.7.0.193 - 10.7.0.194 | 10.7.0.195 |
| Subnet057 | 2    | 2    | 10.7.0.196 | /30  | 255.255.255.252 | 10.7.0.197 - 10.7.0.198 | 10.7.0.199 |
| Subnet058 | 2    | 2    | 10.7.0.200 | /30  | 255.255.255.252 | 10.7.0.201 - 10.7.0.202 | 10.7.0.203 |
| Subnet059 | 2    | 2    | 10.7.0.204 | /30  | 255.255.255.252 | 10.7.0.205 - 10.7.0.206 | 10.7.0.207 |
| Subnet060 | 2    | 2    | 10.7.0.208 | /30  | 255.255.255.252 | 10.7.0.209 - 10.7.0.210 | 10.7.0.211 |
| Subnet061 | 2    | 2    | 10.7.0.212 | /30  | 255.255.255.252 | 10.7.0.213 - 10.7.0.214 | 10.7.0.215 |
| Subnet062 | 2    | 2    | 10.7.0.216 | /30  | 255.255.255.252 | 10.7.0.217 - 10.7.0.218 | 10.7.0.219 |
| Subnet063 | 2    | 2    | 10.7.0.220 | /30  | 255.255.255.252 | 10.7.0.221 - 10.7.0.222 | 10.7.0.223 |
| Subnet064 | 2    | 2    | 10.7.0.224 | /30  | 255.255.255.252 | 10.7.0.225 - 10.7.0.226 | 10.7.0.227 |
| Subnet065 | 2    | 2    | 10.7.0.228 | /30  | 255.255.255.252 | 10.7.0.229 - 10.7.0.230 | 10.7.0.231 |
| T         | 2    | 2    | 10.7.0.232 | /30  | 255.255.255.252 | 10.7.0.233 - 10.7.0.234 | 10.7.0.235 |
| U         | 2    | 2    | 10.7.0.236 | /30  | 255.255.255.252 | 10.7.0.237 - 10.7.0.238 | 10.7.0.239 |
| V         | 2    | 2    | 10.7.0.240 | /30  | 255.255.255.252 | 10.7.0.241 - 10.7.0.242 | 10.7.0.243 |
| W         | 2    | 2    | 10.7.0.244 | /30  | 255.255.255.252 | 10.7.0.245 - 10.7.0.246 | 10.7.0.247 |
| X         | 2    | 2    | 10.7.0.248 | /30  | 255.255.255.252 | 10.7.0.249 - 10.7.0.250 | 10.7.0.251 |
| Y         | 2    | 2    | 10.7.0.252 | /30  | 255.255.255.252 | 10.7.0.253 - 10.7.0.254 | 10.7.0.255 |


### Access

The company’s existing LAN deployments utilise L2 VLANS and STP from the distribution layer to the  access layer, however the company will consider layer 3 to the access layer.

3. You are to decide if the access to distribution will be layer2 or layer3 and provide an argument that considers both pros and cons of your decision. 

    The access to distribution will be layer 3. 

    **Cons of Layer 3:**

    - Higher cost of access layer hardware

    **Pros of Layer 3:**

    - Faster processing of IP packets

        Layer 3 devices do not use spanning tree, VLANs. This free CPU processing capacity, allowing routing to occuring much faster

    - Routing and switching is handled internally without the need to be transmitted to a router 

    - The many potential advantages of using a Layer 3 access design include the following: • 

    - Improved convergence • 

    - Simplified multicast configuration • 

    - Dynamic traffic load balancing • 

    - Single control plane • 

    - Single set of troubleshooting tools (for example, ping and traceroute)

    - Of these, perhaps the most significant is the improvement in network convergence times possible when using a routed access design configured with EIGRP or OSPF as the routing protocol. Comparing the convergence times for an optimal Layer 2 access design (either with a spanning tree loop or without a loop) against that of the Layer 3 access design, you can obtain a four-fold improvement in convergence times, from 800–900msec for the Layer 2 design to less than 200 msec for the Layer 3 access.

    The additional cost of adding this hardware to the network is  investment 

4. You are to decide if VLANs need to be spanned across access switches or if each access  switch will have a dedicated user VLAN. Why have you made this decision? 

Each switch will have a dedicated user VLAN, this ensures traffic is separated. Layer 3 switches can be divided so that physical connections to the layer 3 can still be made. 

**Note** this decision will influence if the link between the distribution switches is L2 or L3. 

### Resilience

The HO LAN is to provide redundant links and paths where possible while minimising convergence  time. The design needs to consider the impact of a switch failure.

5. The customer requests you describe traffic flow and how it is affected by at least three potential failure scenarios. Use diagrams to indicate primary and alternate traffic paths in  the event of device and or link failures.
6. You are to explain how you are using ether channel and if not why?
7. Explain how have the core to distribution links been designed to minimise convergence? 
8. Alternatively if you are using a layer 3 access then describe how you have done this including  the routing protocol used and how the routing metrics have been configured and why. How  does this impact the ability to have redundant host default gateways? 

### Routing

You must specify an appropriate interior gateway protocol to be used for internal routing within the HO site. The interior routing protocol will be used between the Distribution layer, Core layer and  edge routers.

**OSPF selected**



10. Explain why you have chosen the IGP?
    - With OSPF, there is no limitation on the hop count.
    - The intelligent use of VLSM is very useful in IP address allocation.
    - OSPF uses IP multicast to send link-state updates. This ensures less processing on routers that are not listening to OSPF packets. Also, updates are only sent in case routing changes occur instead of periodically. This ensures a better use of bandwidth.
    - OSPF has better convergence than RIP. This is because routing changes are propagated instantaneously and not periodically.
    - OSPF allows for better load balancing.
    - OSPF allows for a logical definition of networks where routers can be divided into areas. This limits the explosion of link state updates over the whole network. This also provides a mechanism for aggregating routes and cutting down on the unnecessary propagation of subnet information.
    - OSPF allows for routing authentication by using different methods of password authentication.
    - OSPF allows for the transfer and tagging of external routes injected into an Autonomous System. This keeps track of external routes injected by exterior protocols such as BGP.
11. Explain how you have configured the IGP including methods you have employed to minimise  convergence time, optimise traffic flow and limit the wasting of bandwidth and CPU calculations. 

### Security

The customer has asked you to consider security.
12. Are there any security features that should be deployed within the new HO LAN? Explain  your choices. 

## Customer Specifications - WAN Connectivity 

### Design 
The WAN core is a service provider managed MPLS service. The HO LAN will connect to the WAN via two separate connections. The WAN links to the provider are 100Mb Ethernet. Ensure to design the WAN connectivity and routing as per the customer requirements below. 

Refer to the WAN diagram in the appendix. 

### ISP IP Addressing 
The ISP has allocated two point-to-point networks of 172.16.17.0/30 & 172.16.17.4/30 for the Head  Office’s WAN links to the service provider. 
172.16.17.12/30 has been allocated for the Liverpool WAN link. 172.16.17.16/30 has been allocated for the Fulham WAN link. 
Use 172.16.17.8/30 for the link between the Provider Edge routers. 

### Liverpool Site 
The remote Liverpool site is included for routing testing purposes. The LAN IP address range is 10.8.0.0/16. You will specify this range in any policy, filtering, routing etc  as needed. 

### Fulham Site 
The remote Fulham site is included for routing testing purposes. The LAN IP address range is 10.9.0.0/16. You will specify this range in any policy, filtering, routing etc  as needed. 

### BGP AS Numbering
The MPLS Core BGP AS is 4700 The Head Office has been allocated BGP AS 65007 Liverpool has been allocated BGP AS 65008 Fulham has been allocated BGP AS 65009

### Routing - HO LAN to Service Provider
You are required to use BGP to connect the head office site to the ISP. The company has purchased an active / active service offering from the provider. This means that the company can choose which link to use on a per subnet basis. 
You are to configure BGP policy on the HO LAN WAN Routers such that:
For inbound traffic from the Service Provider (& other attached sites) to the HO LAN networks, Link 1 (see appendix diagram) will be used as the primary path. Traffic will route over Link 2 if the primary path fails. Only a summary route of the Head Office LAN networks is to be advertised to the ISP via the primary and backup paths.

Outbound traffic from the HO LAN network to the Liverpool site will use Link 2 as primary and Link 1 as backup.

Outbound traffic from the HO LAN network to the Fulham site will use Link 1 as primary and Link 2 as backup.

13. You are to specify and describe how BGP will be configured to accomplish the above including detail of which BGP attributes are used and why and how the HO LAN networks are summarised.
14. You are to ensure the Head Office cannot be used as transit between any other Service Provider attached sites. Explain how you have achieved this.
15. You are to ensure end to end connectivity between the HO user VLANs and Liverpool and Fulham sites. Provide evidence of this.

### Security 

The customer has asked you to consider security. 
16. Anti spoof (URPF or ACL) not break Asymmetric traffic 
17. You are to choose at least two additional security features that should be deployed on the  WAN routers (not related to VTY or console passwords)? Explain your choices. 

## Deliverables
Provide the following documents and evidence. Ensure your work adheres to the marking rubric. 

### Deliverable – LAN design (25%)
  - Describe the LAN design, giving a broad overview of how the design works and meets the  customer requirements.
  - Provide detail of how the chosen features work, paying careful attention to answer the  customer questions in red within the customer specifications above. Supply tables and  diagrams as requested.
  - Supporting references. Include in text referencing and a table of references.

### Deliverable – WAN design (25%) 
  - Describe the WAN design, giving a broad overview of how the design works and meets the  customer requirements.
  - Provide detail of how the chosen features work, paying careful attention to answer the  customer questions in red within the customer specifications above. Supply tables and  diagrams as requested.
  - Supporting references. Include in text referencing and a table of references.

### Deliverable – LAN Logical topology diagram (5%) 
  You are to provide a LAN logical topology diagram that includes the following: 
  - Access, distribution, core and WAN edge intermediary devices
  - VLANs / Network addressing
  - Port numbering for infrastructure links (not access ports).
  - Routing domains / Autonomous systems / Areas
  - Default gateways, Virtual IPs
  - Show traffic flows (primary / backup paths) 
    If needed the diagram can be split into multiple parts. The diagram must be separate to the supplied  packet tracer or VIRL configuration (though packet tracer or VIRL can be used as the basis). 

### Deliverable – WAN Logical topology diagram (5%) 
  You are to provide a WAN logical topology diagram that includes the following:
  - Distribution layer, WAN edge, Service provider, Liverpool, Fulham
  - Interface / port assignment
  - Network addressing
  - Routing domains / Autonomous systems / Areas
  - Any relevant feature information (e.g. BGP attributes)
  - Show traffic flows (primary / backup paths) 
    If needed the diagram can be split into multiple parts. The diagram must be separate to the supplied  packet tracer or VIRL configuration (though packet tracer or VIRL can be used as the basis).

### Deliverable – LAN Working Configuration (15%) 
  You are to provide a working proof of concept lab within packet tracer. 
  - Include all access, distribution and core switches.
  - Include the WAN edge routers, however BGP configuration is not required on these within Packet Tracer.
  - Ensure all specified technologies and features (including specified security features) are  configured correctly and working.
  - Provide testing output as supporting evidence (e.g. output of relevant show commands) for  each feature. Note: Due to the number of devices you are requested to use packet tracer. Due to packet Tracer limitations, some features may not be available or work as intended. If you have specified any such features in your design you are to provide the configuration of the feature separately.  

### Deliverable – WAN Working Configuration (15%) 
You are to provide a working proof of concept lab within GNS3 (portable project) 
- Include all routers for the HO LAN, Provider edge, Liverpool, Fulham
- The HO LAN WAN edge distribution switches are to be included (to source the HO LAN  networks) however as GNS3 is resource intensive (CPU, mem) the following option can be  implemented to help minimise resource use. HO LAN Can be simulated with a single device that uses loopbacks to source the HO LAN networks as  required. Make sure these match any summary addresses you may already have created  within the HO LAN design. See appendix.
- Ensure all specified technologies and features (including specified security features) are  configured correctly and working.
- Provide testing output as supporting evidence (e.g. output of relevant show commands) for  each feature.
- While the service provider core is stated as running MPLS, you do not need to provide any  MPLS configuration.

### Deliverable - Time sheeting
To ensure accurate billing you have been asked to record the time you spend on each activity,  including date, length of time and a brief description of the activity. 

###  Deliverable – Grade your work
You are to review the marking rubric against your work and provide a grade on a scale from F to A+  for each item.





## Notes

he hierarchical campus design has used a full mesh equal-cost path routing design leveraging Layer 3  switching in the core and between distribution layers of the network for many years. The current  generation of Cisco switches can “route” or switch voice and data packets using Layer 3 and Layer 4  information with neither an increase in latency nor loss of capacity in comparison with a pure Layer 2  switch. Because in current hardware, Layer 2 switching and Layer 3 routing perform with equal speed,  Cisco recommends a routed network core in all cases. Routed cores have numerous advantages,  including the following:  • High availability – Deterministic convergence times for any link or node failure in an equal-cost path Layer 3  design of less than 200 msec – No potential for Layer 2 Spanning Tree loops • Scalability and flexibility – Dynamic traffic load balancing with optimal path selection – Structured routing permits for use of modular design and ease of growth • Simplified management and troubleshooting – Simplified routing design eases operational support – Removal of the need to troubleshoot L2/L3 interactions in the core The many advantages of Layer 3 routing in the campus derive from the inherent behavior of the routing  protocols combined with the flexibility and performance of Layer 3 hardware switching. The increased  scalability and resilience of the Layer 3 distribution/core design has proven itself in many customer  networks over the years and continues to be the best practice recommendation for campus design.

## Routing to the Edge  Advantages, 

Yes in the Right Environment Advantages:  • Ease of implementation, less to get right • No matching of STP/HSRP/GLBP priority • No L2/L3 Multicast topology inconsistencies • Single Control Plane and well known tool set • traceroute, show ip route, show ip eigrp neighbour, etc.… • Most Catalysts support L3 Switching today • EIGRP converges in <200 msec • OSPF with sub-second tuning converges in <200 msec • RPVST+ convergence times dependent on GLBP / HSRP tuning Considerations:  • Do you have any Layer 2 VLAN adjacency requirements between access switches? • IP addressing—Do you have enough address space and the allocation plan to support a routed access design?