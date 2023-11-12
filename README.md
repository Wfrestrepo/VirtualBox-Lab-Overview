# VirtualBox-Lab-Overview

## Introduction

In this lab, we want to install VirtualBox and configure different OS,  create an Active Directory and DNS server, and configure rules on Pfsense.

![VirtualBox](https://github.com/Wfrestrepo/VirtualBox-Lab-Overview/assets/108705302/97a25f6d-ad0a-482f-8eeb-fde84d6404a0)


## Process

First, we need to install a Hypervisor for our lab, in this case, we’ll use VirtualBox 64-bit, and also all the OS and Firewall such as: 

-Kali Linux: 

We will use Kali to explore some vulnerabilities on the Metasplotaible 2 machine. 

-Metaspliotable 2: 

Metasplotaible is a vulnerable machine that we use for penetration testing and learning about how threat actors approach their actions. 

-Windows 10: 

Even if our Host system is Windows, VirtualBox needs to download an image of an OS Windows 10 to install. 

-Pfsense Firewall: 

We will configure basic rules and understand ACLs, using an Implicit Deny rule to implement security. 

-Windows Server 2019: 

We will download the ISO file, in that way, we can install and configure the server from the start. All the OS and services above will be attached to this web server 2019. We will connect the machines to the same Switch, create a DNS server and configure the Active Directory to create users and groups, giving and removing access. 

## Connecting all the machines: 

By default, all the Virtual Machines come attached to NAT, but we want them connected to our Windows Server, and give it access to our Wireless connection, so we will change these: 

![bridge](https://github.com/Wfrestrepo/VirtualBox-Lab-Overview/assets/108705302/dd8bafe6-0069-40bb-adfc-6b9401a4703f)


 Settings >Network  >Adapter 1>Attached to: (here we will modify the “NAT” to “Bridged Adapter”) 

This is the same process for all the VMs in our system. Once we have all our machines connected at the same Switch, we can use the  “ipconfig” for Windows, and “ifconfig” for Linux to check our IP addresses, then we’ll use the Ping command to see if we can listen to the other machines. In the process take notes of all the IP addresses, this comes in handy when you want to know the IP of a specific machine for future use. 
We’ll configure the name of our Windows Server to DC1 and give it Google DNS of “8.8.8.8”. 
Now this is an important part of the process, we need to change the preferred DNS of all the other machines to be the IP address of our Windows Server.  

![Ping server](https://github.com/Wfrestrepo/VirtualBox-Lab-Overview/assets/108705302/7384efa0-9419-4495-93a6-c7d67a501ec8)

Here we can see that all the machines can PING our Windows server IP of 198.168.1.19, and the Domain controller is cyberlab.com.

Installing different roles: 

After adding Active Directory and DNS on our Server 2019, we are going to click to promote this server to a domain controller and give it the name “cyberlab.com” The computer will ask you to reset to apply the changes. Right after you will find a new profile to access, this becomes your new domain controller. Another important point is that these VMs are bridged to our physical network, and if you want to run these machines on a sandbox environment, you will need to press Ctrl > H a new menu will ask you to create the environment. Once is created, you will change the network settings of the machines you want to connect to the sandbox, from Bridge to the Host-only Adapter. 

## Conclusion

Using virtual machines (VMs) is an easy and safe approach to creating, testing, and managing various operating systems simultaneously. At our organization, our top priority is security, and deploying updates in these environments is an essential component of our policies and patch management strategies, without disrupting normal operations and preserving business continuity.
