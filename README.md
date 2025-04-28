# Active Directory

## Objective

To build a fully functional on‑premises Active Directory domain environment from scratch, integrating Splunk for centralized logging and monitoring, and simulating attacker‑victim scenarios using Windows and Kali Linux VMs.

## Skills Learned

- Network & Infrastructure Design: Created logical network diagrams (using draw.io) to map servers, clients, switches, routers, and cloud components, and defined IP addressing schemes for Splunk, AD, and attacker machines.
- Lab Deployment Planning: Determined hardware requirements (RAM, disk space) and selected virtualization platforms (VirtualBox vs. cloud providers) based on host OS compatibility.
- VM Configuration: Set up Windows 10 target and Kali Linux attacker VMs, and planned server roles for Splunk and Active Directory Domain Controller.
- Log Forwarding & Telemetry: Designed log forwarding architecture using Splunk Universal Forwarder and Sysmon across domain controller and endpoints, with dotted‑line flows to central Splunk server.
- Attack Simulation Preparation: Integrated Atomic Red Team tooling for future red‑team exercises and outlined pathways for extending the lab with IDS/EDR and firewall components.

## Tools Used

- draw.io – For rapid creation of network and lab architecture diagrams.
- VirtualBox – To host Ubuntu/Windows/Kali Linux virtual machines.
- Splunk Universal Forwarder & Sysmon – Configured on Windows servers and workstations to collect and forward telemetry logs.
- Atomic Red Team – Deployed on the target VM to generate simulated attack behaviors.

## Steps

Designed the layout of the network labeled the data flow between the VMs.

![image](https://github.com/user-attachments/assets/9ecf6f58-3901-4449-a195-34d83e0134a2)

Set up the Windows 10, Kali Linux, Ubuntu Server and Windows Server 2022 VM environments in VirtualBox.

![image](https://github.com/user-attachments/assets/5e3f7e0b-769b-4741-8385-5b34e11768e4)

Created a NAT Network so the machines can access the Internet while on the same network.

![image](https://github.com/user-attachments/assets/de5cb74e-6327-4ebe-a9ef-a0e1c9069fad)

Updated the Ubuntu Server to prepare it for the Splunk Server installation by running the following command:

![image](https://github.com/user-attachments/assets/72caff2d-e285-4ab6-803b-0ef6d44b0438)

Wrote a YAML script in the Ubuntu Server to assign it the static IP described in the network diagram above.

![image](https://github.com/user-attachments/assets/b4e18c80-e326-4e52-b85d-7c6774dcd73d)

![image](https://github.com/user-attachments/assets/15929736-e585-47ba-92a7-d942539d970c)

Downloaded the Splunk Enterprise .deb file to be installed on the Ubuntu Server.

![image](https://github.com/user-attachments/assets/8b2123a3-bfb7-4cd2-831e-13695ff6dcab)




