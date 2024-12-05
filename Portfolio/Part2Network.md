![image](https://github.com/user-attachments/assets/2d72bf70-82c7-45a5-b921-e0b1020629bd)


Part 2. Network Scalability Analysis
Recall the e-commerce website scenario we discussed earlier. Given the expected surge in traffic, analyze the provided network topology diagram. Identify potential bottlenecks and areas where scalability might be a concern. Propose specific strategies to improve the network's scalability and performance to ensure a seamless user experience during the peak traffic period. Consider factors such as increased user demand, new applications, and security threats.

![image](https://github.com/user-attachments/assets/90145d59-0b4a-46fc-9808-e8472d3614aa)



This is our proposed design:

![image](https://github.com/user-attachments/assets/e6c00a3c-777f-486d-b9d4-23c38238eec4)






1. Network Analysis
   
Analysis of Potential Bottlenecks:

The multilayer switches (3560-24PS) serve as the backbone, connecting all access switches and servers. These may become bottlenecks under heavy traffic due to limited bandwidth if high-demand services (like file sharing or backups) are used simultaneously by multiple devices.
The single connection to each access switch (2960-24TT) might also limit bandwidth for users during peak usage.

Security Risks:

The use of ASA firewalls ensures a strong perimeter defense, but internal traffic security isn't clearly depicted. Lack of internal VLAN segmentation or access control lists (ACLs) could allow unauthorized communication between devices.
The network’s dependency on servers (MANUAL, BACKUP, etc.) introduces single points of failure if no server redundancy mechanisms are in place.

Capacity Limitations:

End devices rely on a limited number of access switches with fixed port capacities, which could constrain scalability.
Internet bandwidth might also be a limiting factor if not upgraded to meet growing user demands.


2. Scalability Planning
   
Proposed Solutions:

Vertical Scaling: Upgrading existing core switches to higher capacity models (e.g., Cisco Catalyst 9400) with greater bandwidth and processing power.
Horizontal Scaling: Adding more access switches and redistributing devices across them to reduce load per switch.
Cloud Integration: Offloading non-critical workloads (e.g., file storage) to cloud services, reducing server dependency.
Segmenting Network: Implementing VLANs for better traffic segregation, optimizing bandwidth usage, and increasing security.

Potential Drawbacks and Benefits:

Drawbacks: Higher initial cost for new hardware, increased complexity in managing VLANs and maintaining cloud services.
Benefits: Improved reliability, reduced latency, and simplified future expansion.

3. Evaluation of Solutions
   
Hardware Upgrades:

Recommend upgrading the 3560-24PS core switches to models supporting higher throughput and redundancy, like stacked switches with modular capacity.

Replace 2960-24TT switches with PoE-enabled models to support advanced devices like VoIP phones and wireless access points.
Software Configurations:

Implement QoS policies to prioritize critical services (e.g., video calls over file downloads).
Use advanced routing protocols like OSPF or EIGRP for faster convergence in case of network failures.

Network Optimizations:

Add link aggregation (EtherChannel) between access switches and core switches to increase bandwidth and provide redundancy.
Use dual-homed connections to firewalls and ISPs for greater failover resilience.



4. Proposed Design
   
Detailed Design:

Network Diagram: Expand the diagram to include VLANs, redundancies (e.g., EtherChannel links), and additional devices like wireless access points.

Configurations:
Define VLANs (e.g., VLAN 10 for servers, VLAN 20 for office PCs) and inter-VLAN routing on the core switch.
Configure ACLs to restrict communication between sensitive VLANs.

Implementation Plan:

Upgrade core switches during off-hours to minimize disruptions.
Gradually segment devices into VLANs and test inter-VLAN routing.
Implement cloud integration in phases, starting with non-critical data.


5. Evaluation and Justification
   
Cost:

Core switch upgrades are expensive but justified for long-term reliability and scalability.
VLAN implementation has minimal cost but requires skilled network administrators.

Complexity:

VLANs and QoS configurations add complexity but provide significant benefits in terms of security and performance.

Impact:

Proposed solutions address immediate limitations and ensure long-term scalability, making the network more robust and adaptable.
