 This documentation walks through creating a multi-VM lab environment using **Oracle VirtualBox**, including:

- **Windows Server 2022**
- **Windows 8.1 Client VM #1**
- **Windows 8.1 Client VM #2**
- (Kali Linux & Metasploitable are mentioned briefly where screenshots exist)



---

## 📌 1. VirtualBox Installed & Opened

After installing VirtualBox, launch it. You should see the main VirtualBox Manager.

![VirtualBox Home](./Screenshot%20(1).png)

---

## 📌 2. Creating the Windows Server 2022 Virtual Machine

### ➡️ Step 1 – Click **New** and start the VM creation wizard

Pick a name for the VM and then proceed to attach the ISO.

![Server VM Wizard – Name & ISO](./Screenshot%20(29).png)

### ➡️ Step 2 – Browse and select the Windows Server ISO

![Server ISO Selection](./Screenshot%20(30).png)

### ➡️ Step 3 – Configure RAM and CPU

Allocate enough resources for the server (for example, 4 GB RAM and 2 vCPUs).

![Server Hardware Settings](./Screenshot%20(31).png)

### ➡️ Step 4 – Create a Virtual Hard Disk

Choose to create a new VDI disk and assign around 50 GB.

![Server Disk Configuration](./Screenshot%20(32).png)

### ➡️ Step 5 – VM Successfully Created

After finishing the wizard, the Windows Server VM appears in the list.

![Server VM Created](./Screenshot%20(33).png)

---

## 📌 3. Installing Windows Server 2022

### ➡️ Step 1 – Start the Server VM

The VM boots from the ISO and you see the Windows setup screen.

![Server Setup Start](./Screenshot%20(38).png)

### ➡️ Step 2 – Windows Setup Language & Preferences

![Language Selection](./Screenshot%20(39).png)

### ➡️ Step 3 – Click **Install Now**

![Install Now](./Screenshot%20(47).png)

### ➡️ Step 4 – Accept the License Agreement

![License Agreement](./Screenshot%20(48).png)





## 📌 4. Creating Windows 8.1 Client VM #1

### ➡️ Step 1 – Create a New VM and Select Windows 8.1 ISO

Use the “New” button again and point to the Windows 8.1 ISO.

![Windows 8.1 ISO Selection](./Screenshot%20(34).png)

### ➡️ Step 2 – OS Auto-Detection

VirtualBox detects the OS type and version based on the ISO.

![Windows 8 OS Detected](./Screenshot%20(35).png)

### ➡️ Step 3 – VM Appears in the List

You have now successfully created your first Windows 8.1 VM,

![Windows 8 VM Created](./Screenshot%20(36).png)

---

## 📌 5. Creating Windows 8.1 Client VM #2

You need to  then repeat the process to create a second Windows 8.1 machine.

### ➡️ Step 1 – New VM Wizard for Second Win8 VM

![Second Win8 VM – Name & Settings](./Screenshot%20(51).png)

### ➡️ Step 2 – Confirm Hardware & Disk Configuration

![Second Win8 VM – Hardware & Disk](./Screenshot%20(52).png)

### ➡️ Step 3 – Select Installation Drive in Setup

During installation, choose the virtual disk where Windows 8.1 will be installed.

![Drive Selection During Install](./Screenshot%20(53).png)

*(You may also use `Screenshot (54).png` here for additional install progress.)*

### ➡️ Step 4 – Windows 8.1 Successfully Installed

After installation completes then the Windows 8.1 Start screen / desktop.

![Windows 8.1 Start Screen](./Screenshot%20(55).png)

![Windows 8.1 Desktop Running](./Screenshot%20(56).png)

---

## 📌 6. Kali Linux & Metasploitable (Brief Mentions )

I also experimented with Kali Linux and Metasploitable. These are **not fully documented** here, but relevant screenshots exist and show partial setup.

### ⚙️ Example – Kali Disk / Boot Error

When Kali could not boot, VirtualBox showed a “no bootable medium” type of message, so, I corrected this by attaching the correct disk.

![Kali Boot / Disk Issue](./Screenshot%20(23).png)

![Kali VDI Selection](./Screenshot%20(24).png)

### ⚙️ Example – Metasploitable Disk / VM Creation

Also a brief intro to configuring a Metasploitable VM:

![Metasploitable VM Creation](./Screenshot%20(37).png)

*(These sections will be expanded in a future README while I'll be  focusing on offensive security testing.)*

---

## 📌 7. Current Virtual Machine Summary

Your lab currently includes:

- **Windows Server 2022 VM**  
  Used as the basis for a future Domain Controller, DNS, and IAM configuration.

- **Windows 8.1 Client #1 (Windows_8_Wizard)**  
  A workstation to later join the domain and test Active Directory logins.

- **Windows 8.1 Client #2 (Wins_8_2)**  
  A second client for simulating multi-user/domain scenarios.

- **Kali Linux (Partially setup)**  
  Intended attacker machine for future penetration testing.

- **Metasploitable 2 (Partially setup)**  
  Intended vulnerable target VM for exploitation practice.

---

## 📌 8. Next Steps / Future Work

You can extend this lab by:

- Promoting Windows Server to a **Domain Controller (AD DS)**  
- Creating a **lab.local** (or similar) domain  
- Joining both Windows 8.1 clients to the domain  
- Configuring **Group Policy, IAM roles, and permissions**  
- Using Kali to scan and test services (e.g. Nmap, Metasploit)  
- Using Metasploitable as the vulnerable target  
- Capturing lab traffic with **Wireshark**

---

## ✅ Summary

This repository documents the full **VirtualBox-based lab environment setup** using:

- Oracle VirtualBox  
- Windows Server 2022  
- Two Windows 8.1 client machines  
- Early steps toward a security testing lab

All screenshots in this README are actual captures from the build process and are stored in this repo as `Screenshot (X).png`.
