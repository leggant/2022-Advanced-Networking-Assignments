# Assignment 2 - Timesheet

## Deliverable - Time sheeting

> To ensure accurate billing you have been asked to record the time you spend on each activity,  including date, length of time and a brief description of the activity.

### Documentation Timesheet

| Task                       | Includes                                                     | Date_Started | Completed | Total |
| :------------------------- | ------------------------------------------------------------ | ------------ | --------- | ----- |
| Initial Setup              | creating files for documentation, GNS3 WAN and Packet Tracer LAN. Adding to GitHub Repository. | 28/03/22     | 12/04/22  | 1     |
| Create<br />Timesheet_File | Created in markdown, add items from items in the assignment requirement list for LAN, WAN and submission | 28/03/22     | 17/04/22  | 1.5   |
|                            |                                                              |              |           |       |
| LAN Questions              | Subnetting                                                   | 24/04/22     |           |       |
|                            | Access                                                       |              |           |       |
|                            | Resilience q5-7 + q9 (layer 3 switching)                     |              |           |       |
|                            | Routing                                                      |              |           |       |
|                            | Security                                                     |              |           |       |
| WAN Questions              | ISP IP Addressing                                            |              |           |       |
|                            | BGP                                                          |              |           |       |
|                            | Sites Liverpool and Fulham                                   |              |           |       |
|                            | Routing                                                      |              |           |       |
|                            | Security                                                     |              |           |       |
|                            |                                                              |              |           |       |

### LAN Configuration Timesheet

| Task | Includes | Date_Started | Completed | Total (hrs) |
| ---- | ------------ | --------- | ----------- | ----------- |
| Initial Packet Tracer Set-up | Layout of devices, adding links between devices and  labelling devices | 30/03/22 | 17/04/22 | 1.5 |
| Subnetting |  |  | |  |
|Subnets|divide given IP into required subnets, documenting, and adding to PT notes| 17/04/22 | 25/04/22 | 3 |
|      | Label networks allocated | 24/04/22 | 29/04/22 |  |
| Device Basic Configuration | Access layer device configuration, adding commands to text file (backup), testing layer 3 configurations | 20/04/22 | 25/04/22 | 3.5 |
|      | Access to Distribution Layer | 22/04/22 |           | 2 |
|      | Distribution to Core |              |           |             |
|      | Core to Distribution |              |           |             |
|      | WAN Routers |              |           |             |
| LAN Logical topology diagram (5%) | Access, distribution, core and WAN edge intermediary devices | | | |
| | VLANs / Network addressing                                   | | | |
| | Port numbering for infrastructure links (not access ports).  | | | |
| | Routing domains / Autonomous systems / Areas                 | | | |
| | Default gateways, Virtual IPs                                | | | |
| | Show traffic flows (primary / backup paths) If needed the diagram can be split into multiple parts. The diagram must be separate to the supplied  packet tracer or VIRL configuration (though packet tracer or VIRL can be used as the basis). | | | |
| Deliverable – LAN Working Configuration (15%) |                                                              | | | |

### WAN Configuration Timesheet

| Task | Includes | Date_Started | Completed | Total |
| ---- | ------------ | --------- | ----------- | ----------- |
| Initial GNS3 Set-up | Layout of devices, adding links between devices, and labelling | 18-03-22 |           |             |
|                     |                                                              |              |           |       |
|||              |           |             |
|      |      |              |           |             |
|      |      |              |           |             |
|      |      |              |           |             |
|      |      |              |           |             |
|      |      |              |           |             |
|      |      |              |           |             |
| | ||||

### Deliverable – LAN design (25%)

1. Describe the LAN design, giving a broad overview of how the design works and meets the  customer requirements.
2. Provide detail of how the chosen features work, paying careful attention to answer the  customer questions in red within the customer specifications above. Supply tables and  diagrams as requested.
3. Supporting references. Include in text referencing and a table of references. 

### Deliverable – WAN design (25%) 

1. Describe the WAN design, giving a broad overview of how the design works and meets the  customer requirements.
2. Provide detail of how the chosen features work, paying careful attention to answer the  customer questions in red within the customer specifications above. Supply tables and  diagrams as requested.
3. Supporting references. Include in text referencing and a table of references. 

### Deliverable – LAN Logical topology diagram (5%)

> You are to provide a LAN logical topology diagram that includes the following: 

1. Access, distribution, core and WAN edge intermediary devices
2. VLANs / Network addressing
3. Port numbering for infrastructure links (not access ports).
4. Routing domains / Autonomous systems / Areas 
5. Default gateways, Virtual IPs
6. Show traffic flows (primary / backup paths) If needed the diagram can be split into multiple parts. The diagram must be separate to the supplied  packet tracer or VIRL configuration (though packet tracer or VIRL can be used as the basis). 

### Deliverable – WAN Logical topology diagram (5%)

>You are to provide a WAN logical topology diagram that includes the following: 

1. Distribution layer, WAN edge, Service provider, Liverpool, Fulham
   Interface / port assignment
2. Network addressing 
3. Routing domains / Autonomous systems / Areas
4. Any relevant feature information (e.g. BGP attributes)
5. Show traffic flows (primary / backup paths) If needed the diagram can be split into multiple parts. The diagram must be separate to the supplied packet tracer or VIRL configuration (though packet tracer or VIRL can be used as the basis). 

### Deliverable – LAN Working Configuration (15%)

> You are to provide a working proof of concept lab within packet tracer. 

1. Include all access, distribution and core switches.
2. Include the WAN edge routers, however BGP configuration is not required on these within  Packet Tracer. 
3. Ensure all specified technologies and features (including specified security features) are  configured correctly and working.
4.  Provide testing output as supporting evidence (e.g. output of relevant show commands) for  each feature. Note: Due to the number of devices you are requested to use packet tracer. Due to packet Tracer  limitations, some features may not be available or work as intended. If you have specified any such  features in your design you are to provide the configuration of the feature separately.  

### Deliverable – WAN Working Configuration (15%) 

> You are to provide a working proof of concept lab within GNS3 (portable project) 

1. Include all routers for the HO LAN, Provider edge, Liverpool, Fulham
2. The HO LAN WAN edge distribution switches are to be included (to source the HO LAN  networks) however as GNS3 is resource intensive (CPU, mem) the following option can be implemented to help minimise resource use. HO LAN Can be simulated with a single device that uses loopbacks to source the HO LAN networks as  required. Make sure these match any summary addresses you may already have created  within the HO LAN design. See appendix. 
3. Ensure all specified technologies and features (including specified security features) are  configured correctly and working.
4.  Provide testing output as supporting evidence (e.g. output of relevant show commands) for  each feature.
5. While the service provider core is stated as running MPLS, you do not need to provide any  MPLS configuration. 