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

### Ubuntu Server Splunk setup
Updated the Ubuntu Server to prepare it for the Splunk Server installation by running the following command:

![image](https://github.com/user-attachments/assets/72caff2d-e285-4ab6-803b-0ef6d44b0438)

Wrote a YAML script in the Ubuntu Server to assign it the static IP described in the network diagram above.

![image](https://github.com/user-attachments/assets/b4e18c80-e326-4e52-b85d-7c6774dcd73d)

![image](https://github.com/user-attachments/assets/15929736-e585-47ba-92a7-d942539d970c)

Downloaded the Splunk Enterprise .deb file to be installed on the Ubuntu Server.

![image](https://github.com/user-attachments/assets/8b2123a3-bfb7-4cd2-831e-13695ff6dcab)

Installed the VirtualBox guest addition addons on the Ubuntu Server.

![image](https://github.com/user-attachments/assets/d49df6e3-dc09-43ae-a14a-789d8ee1f9a1)
![image](https://github.com/user-attachments/assets/d790c469-d2ac-4c13-abe0-b2b91bd15535)


After rebooting the Ubuntu Server VM, the user was added to the VirtualBox SF group.

![image](https://github.com/user-attachments/assets/d9a837d7-01f8-4637-af26-b948fe35fdc7)

Created a new directory named "share" and mounted the shared folder on it.

![image](https://github.com/user-attachments/assets/d2878691-ece8-4d82-993d-be206b5817a9)

![image](https://github.com/user-attachments/assets/e4044225-2a8c-4a7a-81c3-ea1e7e4a80ec)

Installed Splunk by executing the following command, switching to the Splunk user and running the Splunk installer.

![image](https://github.com/user-attachments/assets/7e3c3f29-441d-456d-bf9a-46f7833af07d)

![image](https://github.com/user-attachments/assets/20c6f9e4-25eb-4ada-9e0e-6c12197bee3f)

Ran the following command to ensure Splunk starts up under the user "splunk" every time the Ubuntu Server VM reboots.

![image](https://github.com/user-attachments/assets/df868a0f-0586-435c-beb2-17673a1179f4)


### Windows 10 VM setup
Changed the name of the Windows 10 VM to "target-PC"

![image](https://github.com/user-attachments/assets/318859ae-99fd-42a8-98ec-04cf292e5db2)

Downloaded the Splunk Universal Forwarder .msi file for the Windows 10 VM.

![image](https://github.com/user-attachments/assets/132bdd20-c582-415e-b6b0-e46c6e3f9eaf)

Assigned the Ubuntu Server's IP and default port 9997 to the Receiving Indexer setting.

![image](https://github.com/user-attachments/assets/2078161d-c657-4f7f-9fde-32aec99ded47)

Configured the inputs.conf file under the "local" directory to instruct the Splunk Forwader on what information to send to the Splunk Server.

![image](https://github.com/user-attachments/assets/7b894f2a-a6d9-4bb1-8d88-41552556b774)

The events defined in the inputs.conf file will be displayed under the index "endpoint" in Splunk.

![image](https://github.com/user-attachments/assets/45779b30-738e-472e-8406-07368a85f35f)

Changed the credential settings in Services -> Log On to "Local System account" in order for the Splunk Forwarder to be able to collect logs.

![image](https://github.com/user-attachments/assets/d2eac6f3-07d0-4c28-8671-7a17cbb18e7f)

In Splunk, an index named "endpoint" was created to match the one in the inputs.conf file.

![image](https://github.com/user-attachments/assets/ce6985d4-2bf3-4005-8883-56259802e6d7)

Enabled the Splunk Server to receive data by adding the default port 9997 as the Receiving Port.

![image](https://github.com/user-attachments/assets/3cb24f03-5a37-40c5-a56b-8eada44a8b71)

Confirmed Splunk is correctly set up and data from the target machine is received.

![image](https://github.com/user-attachments/assets/b79285bd-94ae-4147-b372-5e5b8c37f471)

The Windows Server 2022 VM was set up exactly the same way as the Windows 10 VM.

![image](https://github.com/user-attachments/assets/d28a3ac6-9920-46ab-9978-9324a0bb8a33)

## Active Directory configuration

Installed the Active Directory Domain Services (AD DS) on the Windows Server 2022 VM.

![image](https://github.com/user-attachments/assets/2604b6c0-ebf0-4b69-b9bf-f4f73e9a239a)

Promoted the server to a Domain Controller.

![image](https://github.com/user-attachments/assets/1589df73-e814-4ac1-be37-b1995f9d40a9)


