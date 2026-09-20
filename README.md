# Distributed Linux File Sharing System

## Overview

A small distributed file-sharing environment built and tested using Oracle VM VirtualBox, Ubuntu Desktop, and Ubuntu Server.

Two virtual machines were connected through a VirtualBox host-only network using static IP addresses. SSH was used for remote administration, while SCP was used to securely transfer files between the machines.

The project also included network fault simulation to test connectivity failure and recovery.

## Environment

* Oracle VM VirtualBox
* Ubuntu Desktop
* Ubuntu Server
* VirtualBox Host-Only Network
* Static IPv4 addressing
* OpenSSH
* SCP

## Network Configuration

| Machine        | IP Address          | Interface |
| -------------- | ------------------- | --------- |
| Ubuntu Desktop | `192.168.56.101/24` | `enp0s3`  |
| Ubuntu Server  | `192.168.56.102/24` | `enp0s3`  |

**Network:** `192.168.56.0/24`

**Subnet Mask:** `255.255.255.0`

## Objectives

* Configure two Ubuntu virtual machines
* Connect the machines through a virtual network
* Configure static IP addresses
* Test connectivity using `ping`
* Configure SSH for remote administration
* Transfer files using SCP
* Practice Linux networking and administration commands
* Simulate and recover from a network failure

## SSH Remote Access

OpenSSH Server was installed and configured on the Ubuntu Server.

The Ubuntu Desktop was then used to establish an SSH connection to the Ubuntu Server using its static IP address.

```bash
ssh Wang@192.168.56.102
```

## File Transfer

SCP was used to transfer files between the Ubuntu Desktop and Ubuntu Server.

### Ubuntu Desktop → Ubuntu Server

```bash
scp file.txt Wang@192.168.56.102:/home/Wang/
```

### Ubuntu Server → Ubuntu Desktop

```bash
scp Wang@192.168.56.102:/home/Wang/file.txt .
```

File transfers were successfully tested in both directions.

## Linux Commands Practiced

```text
ip addr
ip route
hostname
whoami
pwd
ls
cat
ping
ssh
scp
systemctl status ssh
```

These commands were used for network configuration, system identification, connectivity testing, remote access, file management, and service verification.

## Network Fault Simulation

A network failure was deliberately simulated by disabling the `enp0s3` interface on the Ubuntu Server.

Connectivity was then tested from the Ubuntu Desktop using `ping`.

While the interface was disabled, communication between the two machines failed.

The interface was then restored, and connectivity was successfully re-established.

This demonstrated basic network troubleshooting and fault recovery.

## Problems Encountered

The Ubuntu Server initially had no Internet access through the host-only network, which prevented OpenSSH from being installed.

A second VirtualBox adapter using NAT was configured to provide Internet access while the host-only adapter remained responsible for communication between the project machines.

The virtual machines also required reduced RAM allocation because the available physical memory caused the host computer to become slow.

## Skills Demonstrated

* Linux Administration
* Linux Networking
* Virtual Machine Networking
* Static IP Configuration
* SSH
* SCP
* Network Troubleshooting
* Fault Detection and Recovery
* Client-Server Communication
* Oracle VM VirtualBox

## Documentation

The complete project report, including screenshots and testing evidence, is available in:

[View Project Documentation](./Distributed%20Linux%20File%20Sharing%20System.pdf)

## Project Status

**Completed and tested successfully.**

