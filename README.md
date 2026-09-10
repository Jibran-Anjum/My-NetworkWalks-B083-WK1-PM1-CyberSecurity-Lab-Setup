<div align="center">

# Project: Cyber Security Lab Environment Setup

**Building and setting up an isolated virtual lab environment for penetration testing and ethical hacking practices.**

</div>

<p align="center">
    <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
    <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
    <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
    <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
    <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
    <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
    <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
    <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
    <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
    <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
    <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
    <img src="https://img.shields.io/badge/Waqas%20Karim%20CCIE-C00000?style=flat-square" />
</p>

---

## Project Overview

In this project, I had to setup a **virtual environment** that would be used as **cybersecurity and penetration testing laboratory** using VirtualBox and Kali Linux.

The main purpose of this lab was to be able to create a controlled environment or learn how to create a controlled environment where I'll be able to test, use, and learn cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities. It also to have an environment as a safe space for the use of these tools and techniques.

This lab is configured on a private virtual network, so that additional machines can be added later and used as targets for authorized security testing.

---

## Objectives of this Project

The main objectives of this project are listed below;

1. Installation and configuration of VirtualBox.
2. Downloading and importing Kali Linux as a virtual machine in VirtualBox.
3. Creating a private *NAT Network* for the cybersecurity lab.
4. Configuring network connectivity for Kali Linux.
5. Assigning a consistent IP address to the Kali Linux VM.
6. Verify network connectivity and DNS resolution.
7. Take a clean VM snapshot for recovery.
8. Document the complete setup process.
9. Prepare the environment for the future cybersecurity projects.

---

## Purpose of the Lab

This lab will provide us with a safe space and a controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities like;

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practices
- Security-tool experimentation

## Architecture of the Lab

![](architecture.png)

---

## Lab Configuration

| Components      | Configuration              |
| ----------      | -------------              |
| Host OS         | Debian Linux               |
| Host RAM        | 8GB                        |
| Processor       | Intel Core i5 2nd Gen      |
| Hypervisor      | VirtualBox 7.2             |
| Security OS     | Kali Linux                 |
| Kali RAM        | 2048MB                     |
| Virtual Network | NAT Network                |
| Network Address | 10.0.0.0/24                |
| Kali IP Address | 10.0.0.2/24                |
| Default Gateway | 10.0.0.1                   |
| DNS Server      | 8.8.8.8                    |
| Future VM Range | 10.0.0.4 -> 10.0.0.254     |

---

# Lab Setup Procedure

## 1st Step -> Installing 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package (although I didn't needed but it was one of the requirements for the project so I completed it), which may be distributed as a `.7z` archive.

And since I'm using *Debian Linux* so the command that I used to install it is the following;

```bash
sudo apt install p7zip-full

```

**Tool:** 7-Zip

---

## 2nd Step -> Install VirtualBox

I installed VirtualBox as the hypervisor.

---

## 3rd Step -> Create the NAT Network

I created a NAT network that was created in VirtualBox.

**Configuration:**

| Name | Value |
| --- | --- |
| NetworkName: | NATNetwork |
| IPv4 Prefix: | 10.0.0.0/24 |
| DHCP: | Enabled |
| IPv6: | Disabled |

A **NAT Network** was selected because the multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

---

## 4th Step -> Import Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows;

| Name | Value |
| --- | --- |
| Adapter | 1 |
| Attached to | NAT Network |
| Network | NATNetwork |
| Adapter Type | Intel PRO/1000 MT Desktop (82540EM) |

The VM was allocated;

**RAM:** 2048MB

---

## 5th Step -> Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

The configuration;

| Name | Value |
| --- | --- |
| IP Address | 10.0.0.2 |
| Subnet Mask | 255.255.255.0 |
| Gateway | 10.0.0.1 |
| Primary DNS | 8.8.8.8 |

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

---

## 6th Step -> Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

---

# Lab Verification

| Test | Command | Expected Result |
| --- | --- | --- |
| Check IP address | `ip a` | Correct Kali IP displayed |
| Test Gateway | `ping 10.0.0.1` | Successful replies |
| Test Internet Connectivity | `ping 8.8.8.8` | Successful replies |
| Test DNS resolution | `nslookup networkwalks.com` | Domain resolves |
| Verify Nmap | `nmap --version` | Nmap version displayed |
| Verify snapshot | Restore snapshot and run `ip a` | Baseline configuration restored |

---

# Problems Encountered & their Solutions

The problems that I encountered were mainly because that I needed to create **NAT Network** on my laptop since I was on linux. Due to for some reason there wasn't any option to choose in the Network dropdown the showed **NAT Network**.

Also I was using KVM setup before, and for this lab I needed to setup VirtualBox, so that also gave me a headache.

The following phases the problems encountered and their solutions much better;

## Troubleshooting & Issues Encountered

### Topic 1: Host System Driver & Hypervisor Collisions

When setting up VirtualBox on the Debian host, two major system-level blockages prevented virtual machines from starting.

#### Issue A: Missing Kernel Modules (`vboxdrv`)

* **Symptom:** VirtualBox threw an error stating that the `vboxdrv` kernel module was not loaded for the current kernel (`6.12.107+deb13-amd64`).
* **Solution:** Installed the necessary compilation tools and kernel headers, then manually forced VirtualBox to build the missing drivers:
```bash
sudo apt update && sudo apt install -y build-essential dkms linux-headers-$(uname -r)
sudo /sbin/vboxconfig

```



#### Issue B: KVM Hypervisor Exclusive Access Conflict (`VERR_VMX_IN_VMX_ROOT_MODE`)

* **Symptom:** VirtualBox failed to launch the VM because Debian's default KVM virtualization module was occupying the CPU's VT-x extensions.
* **Solution:** Permanently blacklisted the KVM modules at the system level, regenerated the boot image (`initramfs`), and rebooted the host machine:
```bash
echo -e "blacklist kvm_intel\nblacklist kvm\ninstall kvm_intel /bin/false\ninstall kvm /bin/false" | sudo tee /etc/modprobe.d/blacklist-kvm.conf
sudo update-initramfs -u -k all
sudo reboot

```



### Topic 2: Network Subnet Configuration & Troubleshooting

Configuring the internal virtual machine network required administrative setup via the terminal command line interface.

#### Issue A: Configuring the NAT Network Subnet

* **Symptom:** Establishing the `NATNetwork` interface required manual initialization to assign the standard lab subnet range without conflicts.
* **Solution:** Managed VirtualBox NAT network settings to utilize the designated `10.0.0.0/24` subnet:
```bash
vboxmanage natnetwork stop --netname NATNetwork
vboxmanage natnetwork modify --netname NATNetwork --network "10.0.0.0/24" --enable
vboxmanage dhcpserver modify --network=NATNetwork --server-ip=10.0.0.3 --lower-ip=10.0.0.4 --upper-ip=10.0.0.254 --netmask=255.255.255.0 --enable
vboxmanage natnetwork start --netname NATNetwork
sudo systemctl restart NetworkManager

```



#### Issue B: Missing Legacy Networking Tools in Kali Guest VM

* **Symptom:** Commands like `eth0` and `dhclient` threw "device not found" errors inside the modern Kali Linux environment.
* **Solution:** Modern Kali uses predictable network interface names (e.g., `enp0s3`) managed via `NetworkManager`. The connection was brought online by toggling the modern utility:
```bash
sudo ip link set enp0s3 up
sudo nmcli networking off && sudo nmcli networking on

```



---

# What I Learned

The concepts and processes that I learned with this project are mentioned here;

### 1. NAT vs NAT Network

A standard NAT configuration and a NAT Network serve different purposes. A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity. This makes it useful for building a multi-machine cybersecurity laboratory.

### 2. Virtual Machine Networking

I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

### 3. Static IP Configuration

I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

### 4. VM Snapshots

I learned that a clean snapshot should be created **before performing risky or experimental activities**. This provides a known-good recovery point for future cybersecurity exercises.

### 5. Documentation

I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

### 6. Host Kernel Module Management

I learned that VirtualBox relies on host-level kernel modules (`vboxdrv`) to interact directly with hardware. When utilizing a cutting-edge Linux kernel, these modules must be explicitly compiled alongside matching kernel headers and developer tools using utilities like **DKMS** to ensure stability across future system updates.

### 7. Hypervisor Coexistence and Hardware Lockout

I learned that hypervisors require exclusive access to CPU hardware virtualization extensions (Intel VT-x or AMD-V). Running multiple virtualization platforms simultaneously—such as VirtualBox alongside native Linux **KVM** services—causes structural system collisions (`VERR_VMX_IN_VMX_ROOT_MODE`), requiring the administrative blacklisting of conflicting modules.

### 8. Network Subnet Collision and Routing Topology

I learned that virtual networks must exist on dedicated subnets relative to the environment. Configuring virtual network parameters (like `10.0.0.0/24`) requires proper routing architecture definitions to maintain communication across guest environments.

### 9. Modern Linux Network Management

I learned that modern Linux distributions have deprecated legacy tools like `eth0` and `dhclient`. Current operating systems rely on predictable network interface naming conventions (such as `enp0s3`) and manage dynamic IP negotiation exclusively through modern daemons like **NetworkManager** via the `nmcli` command line.

---

# Security & Ethical Use

This laboratory is intended strictly for education purposes only.

---

# 🔗 Tools & Resources

* **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
* **VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
* **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)

---

# Author

**Jibran Anjum Chughtai**

Linkedin: [https://www.linkedin.com/in/jibran-anjum-chughtai-905a47256/](https://www.linkedin.com/in/jibran-anjum-chughtai-905a47256/)

---

## Project Information

**Program Name:** Cybersecurity at Networkwalks

**Week:** 01

**Project:** Cybersecurity & Pentesting Lab Setup

**Repository:** GitHub
