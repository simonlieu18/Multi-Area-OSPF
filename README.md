<p align="center">
<img width="55%" alt="image" src="https://github.com/user-attachments/assets/2c483fc3-6203-4816-885f-a98225324a50" />



</p>

<h1>Multi-Area OSPF Lab</h1>
Multi-area OSPF lab configured in Cisco Packet Tracer featuring Area 0 backbone, ABR inter-area routing, and ASBR external route redistribution to a simulated ISP."<br />



<h2>Environments and Technologies Used</h2>

- Cisco Packet Tracer
- Cisco IOS CLI
- OSPF (Open Shortest Path First)

<h2>Operating Systems Used </h2>

- Cisco IOS (Routers)

<h2>High-Level Steps</h2>

- Configure multi-area OSPF across three areas with loopback router IDs
- Designate ABR and ASBR roles across the topology
- Redistribute external default route into OSPF via ASBR
- Verify full adjacency and route propagation with show commands

<h2>Configuration Steps</h2>

<img width="60%" height="380" alt="image" src="https://github.com/user-attachments/assets/356c072c-1216-40b2-b392-db06d703ce86" />



<p>
This lab consists of 3 OSPF areas, with Area 0 serving as the backbone, connected to a simulated ISP router to represent external network connectivity. Each router has OSPF enabled and advertises its directly connected networks within its respective area. Loopback interfaces are configured on each router to ensure a stable router ID.
</p>
<br />

<img width="35%" height="351" alt="image" src="https://github.com/user-attachments/assets/2821b6b4-a969-414e-b901-b2392a1d4cf1" />
<img width="50%" height="336" alt="image" src="https://github.com/user-attachments/assets/d038fa04-dd95-4493-8dd3-b1b55dcc22a7" />


<p>
Each router is configured with a loopback interface and assigned an IP address, which OSPF uses as the stable router ID. Once OSPF is enabled, the network command with wildcard masks is used to advertise each router's directly connected networks within their respective area. The loopback interface is then added to the passive interfaces list to prevent unnecessary OSPF Hello packets from being sent out of it.
</p>
<br />

<img width="45%" height="298" alt="image" src="https://github.com/user-attachments/assets/5ba3ca05-7075-44e4-a74a-4471909d6e0b" />
<img width="45%" height="364" alt="image" src="https://github.com/user-attachments/assets/1d8a6d85-ae69-48a6-bf77-65dd254d91ed" />


<p>
R2 and R3 serve as ABRs, connecting their respective areas to the Area 0 backbone. When configuring OSPF, each interface must be advertised under its correct area — interfaces facing Area 0 are placed in Area 0, while interfaces facing non-backbone areas are placed in their respective area.
</p>
<br />

<img width="45%" alt="image" src="https://github.com/user-attachments/assets/1e615af8-2bb9-47cd-aa34-c6c1bb346fdf" />
<img width="45%"  alt="image" src="https://github.com/user-attachments/assets/c6471fd1-141b-4c9d-907c-eb72991b5f12" />

<p>R6 acts as the ASBR, sitting at the edge of the OSPF network and connecting to the simulated ISP router. A static default route is configured on R6 pointing to the ISP, and the 'default-information originate' command is used to advertise that route into OSPF. This allows all internal routers to automatically learn the gateway of last resort without needing individual static routes configured on each one.
</p>
<br />

<img width="40%" height="394" alt="image" src="https://github.com/user-attachments/assets/027ac817-5d22-44ef-957a-6d6deec42a49" />

<p> 
Finally, use the 'show ip route' command to verify that all OSPF routes are learned across all areas and that the ASBR's default route is being shared with all internal routers.
</p>
<br />
