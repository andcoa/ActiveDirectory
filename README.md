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

Designed the layout of the network used in the Active Directory project and labeled the flow of data between devices.

![image](https://github.com/user-attachments/assets/9ecf6f58-3901-4449-a195-34d83e0134a2)


