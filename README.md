This project walks through how I built a **mini enterprise lab** on my local machine using **Oracle VirtualBox**, including:

- 🖥️ **Windows Server 2022** (domain controller / core services)
- 💻 **Two Windows 8.1 clients**  
  - `Windows_8_Wizard`  
  - `Wins_8_2`
- 🐉 **Kali Linux** (attacker box)
- 🎯 **Metasploitable 2** (intentionally vulnerable target)

All VMs run on a single host using **Oracle VirtualBox**.

---

## 🧰 1. Prerequisites

- A machine with:
  - Virtualization enabled in BIOS (Intel VT-x / AMD-V)
  - At least **16 GB RAM** recommended  
- Downloaded ISOs / images:
  - Windows Server 2022 evaluation ISO
  - Windows 8.1 ISO
  - Kali Linux VirtualBox image (`.vdi`) or ISO
  - Metasploitable 2 image (`.vmdk`)
- ✅ Oracle VirtualBox installed

After installing VirtualBox, open it and you should see the main manager window:

![VirtualBox Manager Home](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(1).png)

---

## 📦 2. Creating the Windows Server 2022 Virtual Machine

### Step 1 – Start the VM creation wizard

In VirtualBox, click **New** to create a new virtual machine.

Select the **Server ISO** you downloaded:

![Select Server ISO file](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(29).png)

VirtualBox auto-detects the OS information when you choose the ISO:

![Server VM basic info](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(30).png)

---

### Step 2 – Configure virtual hardware

Assign memory and CPU resources. Here I used:

- **Base Memory**: 2048 MB (2 GB)  
- **Processors**: 1 CPU (you can assign more if your host can handle it)

![Server VM hardware settings](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(31).png)

---

### Step 3 – Create the virtual hard disk

Create a new virtual disk for the server:

- **Disk Type**: VDI (VirtualBox Disk Image)
- **Storage**: Dynamically allocated
- **Size**: ~50 GB

![Server VM virtual disk setup](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(32).png)

After completing the wizard, the new server VM appears in the list:

![Server VM in VirtualBox list](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(33).png)

---

## 🪟 3. Installing Windows Server 2022

Start the **Magic_Windows_Server_02** VM to boot from the ISO.

### Step 1 – Language and keyboard selection

![Server setup – language selection](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(48).png)

Choose your language, time, and keyboard layout, then click **Next**.

---

### Step 2 – Begin installation

Click **Install now** to start the OS installation:

![Server setup – Install now](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(49).png)

---

### Step 3 – Accept license terms

Check the box to accept the Microsoft Software License Terms and click **Next**:

![Server setup – license agreement](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(50).png)

The setup will continue copying files and installing the operating system.

---

## 💻 4. Creating the First Windows 8.1 Client VM,

### Step 1 – Attach the Windows 8.1 ISO and configure the VM

Click **New**, and in the wizard:

1. Give the VM a name E.g (`Windows_8_Wizard`).
2. Select the **Windows 8.1** ISO.

![Attach Windows 8.1 ISO – first client](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(35).png)

---

### Step 2 – Configure RAM and CPU

Assign RAM and CPU (example: 2048 MB RAM, 1 CPU):

![Windows 8.1 client hardware – first VM](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(36).png)

---

### Step 3 – Create the virtual hard disk

Create a new VDI disk for the first client:

![Windows 8.1 client disk – first VM](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(37).png)

After finishing, you should see `Windows_8_Wizard` in the VM list:

![Windows_8_Wizard in VM list](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(34).png)

---

## 💻 5. Creating the Second Windows 8.1 Client VM (`Wins_8_2`)

We now create a **second Windows 8.1 machine** to simulate another client in the same environment.

### Step 1 – New VM wizard for `Wins_8_2`

Click **New** and configure:

- **VM Name**: `Wins_8_2`
- **ISO Image**: Same Windows 8.1 ISO

![New VM – Wins_8_2 basic settings](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(52).png)

---

### Step 2 – Configure hardware

Set RAM and CPU for the second client:

![Wins_8_2 hardware settings](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(53).png)

---

### Step 3 – Create virtual hard disk

Create a new disk for `Wins_8_2` (example: 40 GB):

![Wins_8_2 virtual disk settings](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(54).png)

---

### Step 4 – Verify second client VM

After installation completes, you can see `Wins_8_2` running with the Windows 8 Start screen:

![Wins_8_2 running – Start screen](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(55).png)

---

## 🐉 6. Setting Up Kali Linux

For Kali, I used a **prebuilt VirtualBox disk (.vdi)**.

### Step 1 – Kali VM creation and disk selection

In the storage section, the Kali VDI is attached to the VM:

![Kali Linux VM attached VDI](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(51).png)

If the VM is missing an ISO or OS image at boot, you might see this error:

![Kali VM boot error – no OS found](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(23).png)

To fix this:

1. Power off the VM.  
2. Go to **Settings → Storage**.  
3. Attach the proper Kali ISO/VDI to the controller.  
4. Boot the VM again.

---

## 🎯 7. Creating the Metasploitable 2 VM

Metasploitable is your **intentionally vulnerable** target machine.

### Step 1 – Create the Metasploitable VM shell

Click **New** and configure:

- **VM Name**: `Metas_VM`
- **Type**: Linux
- **Version**: Other Linux (64-bit)

![Metasploitable VM basic settings](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(36).png)

---

### Step 2 – Assign RAM

![Metasploitable VM RAM/CPU](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(35).png)

*(Values can be 512 MB – 1 GB depending on your host resources.)*

---

### Step 3 – Create or attach the virtual disk

For Metasploitable, we use an **existing `.vmdk` disk image** (about 8 GB):

![Metasploitable VM disk setup](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(38).png)

Once the VM is created, it appears in the list powered off:

![Metas_VM in VirtualBox list](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(39).png)

You can also see the attached Metasploitable disk in the **medium selector**:

![Metasploitable .vmdk attached](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(47).png)

---

## 🧩 8. Windows Server Installation Progress (Optional Visuals)

During installation, the server goes through the usual setup phases. Here are some intermediate views for reference:

![Server ISO selection – file dialog](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(24).png)

![Server VM powering up / installing](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(39).png)

---

## 🧷 9. Current Lab Topology

At this point, the VirtualBox Manager shows all the main lab VMs:

- `Magic_Windows_Server_02` (Windows Server 2022)
- `Windows_8_Wizard` (Windows 8.1 client #1)
- `Wins_8_2` (Windows 8.1 client #2)
- `Richard_Kali_Linux_...` (Kali Linux attacker machine)
- `Metas_VM` (Metasploitable 2 target)

Example manager view (with several VMs running):

![VirtualBox Manager with multiple VMs](https://github.com/Aros3205/Complete-Virtual-Lab-Environment-Setup./raw/main/Screenshot%20(48).png)

---

## 🚀 10. Next Steps / Future Enhancements

Now that the lab is built, you can extend it with:

- **Active Directory** on Windows Server
- **DNS and DHCP** roles
- Join both Windows 8.1 machines to the domain
- Use **Kali** to perform:
  - Network scanning (nmap)
  - Vulnerability scanning (e.g., OpenVAS, Metasploit aux modules)
- Attack **Metasploitable 2** from Kali
- Capture traffic with **Wireshark** for analysis

---

## ✅ Summary

This repo documents how I built a **complete home lab** using:

- Oracle VirtualBox  
- Windows Server 2022  
- Two Windows 8.1 client machines  
- Kali Linux  
- Metasploitable 2  

Every major step is backed by screenshots taken directly from my setup process so others can follow along visually.

> 💬 Feedback, issues, or suggestions?  
> Open an **Issue** on this repo or reach out to me on LinkedIn.
