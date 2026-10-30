# 🔐 Cybersecurity Lab Environment Setup
### Building an Isolated Virtual Lab for Penetration Testing and Ethical Hacking Practice

---

## 📌 Project Overview

This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using **Oracle VirtualBox and Kali Linux** as part of the Networkwalks Cybersecurity Internship – Week 01.

The main objective is to build a controlled and isolated virtual environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, packet analysis, and other security-testing activities can be performed safely.

The lab uses a private NAT Network to allow multiple virtual machines to communicate with each other while maintaining controlled network connectivity.

This environment will serve as the foundation for future cybersecurity experiments and practical security-testing projects.

## 🎯 Objectives

The main objectives of this project are:

- Install and configure Oracle VirtualBox.
- Download and import Kali Linux as a virtual machine.
- Create a private NAT Network for the cybersecurity lab.
- Configure network connectivity for Kali Linux.
- Assign a consistent IP address to the Kali VM.
- Configure gateway and DNS settings.
- Verify network connectivity and DNS resolution.
- Install and verify essential cybersecurity tools.
- Create a clean VM snapshot for recovery.
- Document the complete laboratory setup process.
- Prepare the environment for future penetration-testing exercises.

## 🛡️ Purpose of the Lab

This laboratory provides a controlled environment for learning and practicing cybersecurity concepts.

It can be used for:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web application security testing
- Penetration-testing practice
- Security-tool experimentation
- Network traffic monitoring

**⚠️ Ethical Use:** This environment is intended strictly for educational purposes and authorized security testing. Testing must only be performed on systems that you own or have explicit permission to assess.

## 🏗️ Lab Architecture

The laboratory consists of:

1. **Host Machine:** Windows operating system.
2. **Hypervisor:** Oracle VirtualBox.
3. **Attacker Machine:** Kali Linux.
4. **Virtual Network:** Private NAT Network.
5. **Future Target Machines:** Additional Linux or Windows virtual machines connected to the same NAT Network.

The architecture allows Kali Linux to perform authorized security testing against other virtual machines inside the laboratory.

## ⚙️ Lab Configuration

| Component | Configuration |
|---|---|
| Host OS | Windows 10 |
| Hypervisor | Oracle VirtualBox 7.2 |
| Security OS | Kali Linux |
| Kali RAM | 2048 MB |
| Virtual Network | NAT Network |
| Network Name | NatNetwork |
| Network Address | 10.0.0.0/24 |
| Kali IP Address | 10.0.0.2/24 |
| Default Gateway | 10.0.0.1 |
| DNS Server | 8.8.8.8 |
| Future VM IP Range | 10.0.0.3 – 10.0.0.99 |

*Note: Confirm these values against your actual VirtualBox and Kali Linux configuration before publishing.*

## 🪜 Lab Setup Procedure

### Step 1: Install 7-Zip

Installed 7-Zip to extract the Kali Linux virtual machine package distributed in compressed archive format.

**Tool:** 7-Zip

### Step 2: Install Oracle VirtualBox

Installed Oracle VirtualBox to create and manage virtual machines.

VirtualBox provides a virtualization environment where multiple operating systems can run independently on a single physical machine.

### Step 3: Create a NAT Network

Created a dedicated NAT Network in VirtualBox.

**Network Configuration:**

- Network Name: `NatNetwork`
- IPv4 Prefix: `10.0.0.0/24`
- DHCP: Enabled
- IPv6: Disabled

A NAT Network allows multiple connected virtual machines to communicate with one another while providing outbound network connectivity.

This configuration is useful for creating an isolated multi-machine cybersecurity laboratory.

### Step 4: Import Kali Linux

Downloaded Kali Linux from its official website and imported the virtual machine into VirtualBox.

**Virtual Machine Configuration:**

- Operating System: Kali Linux
- Memory Allocation: 2048 MB
- Network Adapter: Adapter 1
- Attached To: NAT Network
- Network Name: NatNetwork
- Adapter Type: Intel PRO/1000 MT Desktop

A shared folder was also configured to transfer necessary files between the Windows host and Kali Linux.

### Step 5: Configure Kali Linux Networking

Configured and verified the Kali Linux network settings.

**Example Network Configuration:**

- IP Address: `10.0.0.2`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `10.0.0.1`
- DNS Server: `8.8.8.8`

A consistent IP address makes it easier to identify the attacker machine and configure future target virtual machines.

### Step 6: Create a Clean VM Snapshot

Created a clean snapshot after completing the initial Kali Linux installation and network configuration.

**Snapshot Name:**

`Clean Kali - Network Setup`

The snapshot provides a recovery point that can be restored if future experiments modify or damage the virtual machine configuration.

## 🔎 Lab Verification

The following commands can be used to verify the laboratory configuration.

| Test | Command | Purpose |
|---|---|---|
| Check IP Address | `ip a` | Verify assigned IP address |
| Check Network Interfaces | `ip link` | View network interfaces |
| Test Gateway | `ping 10.0.0.1` | Verify gateway connectivity |
| Test Internet | `ping 8.8.8.8` | Check external connectivity |
| Test DNS | `nslookup networkwalks.com` | Verify DNS resolution |
| Verify Nmap | `nmap --version` | Check Nmap installation |
| Verify Snapshot | Restore snapshot and run `ip a` | Confirm baseline recovery |

### Expected Configuration

```bash
IP Address: 10.0.0.2/24
Gateway:    10.0.0.1
DNS:        8.8.8.8
```

## 🐞 Problems Encountered & Solutions

### Problem 1: Internet Connectivity After Static IP Configuration

After manually configuring IPv4 settings, internet connectivity may fail due to NetworkManager configuration or incorrect network settings.

**Troubleshooting:**

- Verify the network interface configuration.
- Check the assigned IP address.
- Verify the default gateway.
- Check DNS configuration.
- Restart the network connection if required.

Example command:

```bash
sudo systemctl restart NetworkManager
```

The connection name and network configuration may differ between systems.

### Problem 2: VirtualBox VT-x / Virtualization Error

The virtual machine initially may fail to start if hardware virtualization is disabled in BIOS/UEFI.

**Solution:**

1. Restart the computer.
2. Enter BIOS/UEFI settings.
3. Locate Intel VT-x or hardware virtualization settings.
4. Enable virtualization.
5. Save the configuration.
6. Restart the computer.
7. Start the Kali Linux virtual machine again.

## 💡 What I Learned

Through this project, I gained practical knowledge of virtual machine configuration and cybersecurity laboratory setup.

### 1. Virtualization

Learned how virtualization allows multiple operating systems to run on a single physical machine using a hypervisor.

### 2. NAT vs NAT Network

Understood the difference between standard NAT and NAT Network.

A NAT Network allows multiple virtual machines to communicate with one another while providing outbound network connectivity.

### 3. Virtual Machine Networking

Learned how virtual network adapters connect virtual machines and how network configuration affects communication between systems.

### 4. Static IP Configuration

Understood IPv4 addressing, subnet masks, default gateways, and DNS configuration in Kali Linux.

### 5. VM Snapshots

Learned how snapshots provide a recovery point before performing potentially risky cybersecurity experiments.

### 6. Cybersecurity Tools

Prepared the environment for using tools such as Nmap, Wireshark, and other penetration-testing utilities.

### 7. Technical Documentation

Learned the importance of documenting configurations, commands, screenshots, troubleshooting steps, and verification results.

## 🔐 Security & Ethical Use

This laboratory is designed exclusively for educational purposes and authorized cybersecurity testing.

All scanning, vulnerability assessment, and penetration-testing activities must be performed only against systems owned by the user or systems for which explicit authorization has been granted.

## 🔗 Tools & Resources

- [7-Zip](https://www.7-zip.org/)
- [Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Kali Linux Official Website](https://www.kali.org/get-kali/)
- [Nmap Documentation](https://nmap.org/book/)
- [Wireshark Official Website](https://www.wireshark.org/)

## 👤 Author

**Shiva Shankar Somavarapu**

- GitHub: [shiva-shankar-77](https://github.com/shiva-shankar-77)
- LinkedIn: [Shiva Shankar Somavarapu](https://www.linkedin.com/in/shivashankar-somavarapu-07a143388/)

## 📌 Project Information

| Field | Details |
|---|---|
| Program | Cybersecurity Internship |
| Organization | Networkwalks |
| Week | 01 |
| Project | Cybersecurity & Penetration Testing Lab Setup |
| Category | Cybersecurity / Ethical Hacking |
| Environment | VirtualBox + Kali Linux |
| Author | Shiva Shankar Somavarapu |

---

**Learning by Building. Securing by Understanding. 🔐**

*This project is part of my hands-on learning journey during the Networkwalks Cybersecurity Internship.*
