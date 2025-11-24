This documentation walks through the complete setup of a multi-VM cybersecurity lab environment using Oracle VirtualBox.
It includes:

Windows Server 2022

Two Windows 8.1 clients

Kali Linux

Metasploitable 2

📌 1. Installing & Opening Oracle VirtualBox

After installing VirtualBox, launch the application.
You should see the VirtualBox Manager interface:

![VirtualBox Home]/Screenshot (1).png)

📌 2. Creating the Windows Server 2022 Virtual Machine

Start by clicking New.

➡️ Selecting VM Name, Folder, and ISO

![Server ISO selection]/Screenshot (30).png)

➡️ Selecting the Server ISO

![Server ISO selection 2]/Screenshot (29).png)

➡️ Virtual Hardware Settings (Memory, CPUs, etc.)

![Hardware]/Screenshot (31).png)

➡️ Creating Virtual Hard Disk (50 GB)

![Disk]/Screenshot (32).png)

➡️ VM Resulting in VirtualBox List

![Server created]/Screenshot (33).png)

📌 3. Creating Windows 8.1 VM (First Client)

Click New, select ISO, and configure settings.

➡️ Selecting Windows 8 ISO

![Win8 ISO]/Screenshot (34).png)

➡️ Automatic OS Detection

![Win8 detected]/Screenshot (35).png)

➡️ Windows 8 VM in List

![Win8 created]/Screenshot (36).png)

📌 4. Creating Kali Linux VM
➡️ Kali VM Creation Window

![Kali creation]/Screenshot (23).png)

➡️ Selecting Existing Kali VDI Disk

![Kali VDI selection]/Screenshot (24).png)

📌 5. Creating Metasploitable VM
➡️ Starting New Metasploitable VM

![Metasploitable start]/Screenshot (37).png)

➡️ Hardware Setup

![Metasploitable hardware]/Screenshot (36).png)

➡️ Selecting 8GB Disk

![Metas disk]/Screenshot (37).png)

📌 6. Example Boot Error (Kali Linux)

You may see this error when booting if no ISO is attached:

![Boot error]/Screenshot (23).png)

To fix:

Go to Settings → Storage

Attach ISO under "Controller: IDE"

Boot again

📌 7. Windows 8 Installation Screen

When installing Windows:

📌 8. Windows Server Login Screen After Installation

📌 9. Windows 8 Completed Setup

📌 10. Lab Summary

Your Virtual Lab now includes:

VM	Purpose
Windows Server 2022	Domain Controller, DNS, DHCP, AD
Windows 8 Client #1	Domain-joined workstation
Windows 8 Client #2	Additional client for testing
Kali Linux	Attacker machine (penetration testing)
Metasploitable 2	Vulnerable target for exploitation
📌 11. Future Enhancements

You can extend this lab by:

Configuring Active Directory

Setting up DHCP + DNS roles

Domain-joining both Windows 8 VMs

Running penetration tests from Kali to Metasploitable

Capturing traffic with Wiresharknm
