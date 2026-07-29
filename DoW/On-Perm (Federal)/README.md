# On Perm Federal Central Manager & Collector Requirements
# Application Based Install *RPM*

This on perm federal central manager & collector requirements document provides critical specifications which are required by the client to successfully deploy Armis on perm.

**Table of Contents**
  * [STIG Deviation](#stig-deviation)
  * [Central Manager OS & Hardware Requirements](#central-manager-os--hardware-requirements)
  * [Edge Collector OS & Hardware Requirements](#edge-collector-os--hardware-requirements)
  * [Core OS Dependencies & Packages](#core-os-dependencies--packages)
  * [Container Runtime](#container-runtime)
  * [Packet Capture & Network Libraries](#packet-capture--network-libraries)
  * [Utility Packages](#utility-packages)
  * [Network & Port Requirements](#network--port-requirements)
---
## STIG Deviation
RHEL 8 Ver 2 Rel 8 (2026-07-10)

V-230554: This STIG item requires the OS to not allow for network interfaces to be able to be placed within promiscuous mode. A network interface being in promiscuous mode is a requirement for the Armis Government Cloud IL5 collector to ingest mirrored SPAN/TAP traffic without dropping packets. Ensure to inform the client of this as a deviation and acceptance thereof must be documented with their compliance team.


## Central Manager OS & Hardware Requirements
* OS = RHEL 8.10
* CPU = 8 CPU (min) / 16 CPU (recommended)
* RAM = 32 GB (min) / 64 GB (recommended)
* Storage = 500 GB SSD (min) / 1 TB (recommended)
* Network = 1 Gbps (min) / 10 Gbps (recommended)
* NICs = 2 (1 Management) (1 collector aggregation) 


## Edge Collector OS & Hardware Requirements
* OS = RHEL 8.10
* CPU = 8 CPU (min & recommended)
* RAM = 16 GB (without SPAN) / 32 GB (recommended)
* Storage = 300 GB (min & recommended)
* Network = 1 Gbps (min) / 10 Gbps (recommended)
* NICs = 2 (1 management) (1 Promiscuous SPAN/TAP)

## Core OS Dependencies & Packages:

## Container Runtime
Podman must be installed on the RHEL 8.10 virtual machine provided. Armis collectors run as containerized microservices on the RHEL OS within Podman.

## Packet Capture & Network Libraries
1. libpcap & libpcap-devel: Both of these libraries must be installed as they are crucial for raw network packet sniffing, SPAN/TAP interface monitoring and deep packet inspection.
2. ethtool & iproute2: Both of these libraries must be installed as they are for network traffic diagnostic verification and route management within the collector.
3. tcpdump & wireshark-cli (tshark): These libraries must be installed as they are important for diagnostic utilities for verifying traffic flow on SPAN/TAP interfaces.


## Utility Packages
* curl & wget: These packages must be installed as they are used for troubleshooting purposes.
* coreutils, tar, gzip, unzip: These packages are required for extracting update bundles and diagnostic logs.
* chrony: Clock drift across Central Manage and Edge Collectors must remain under 5 seconds for accurate log correlation and TLS validation. 

## Network & Port Requirements
## Central Manager
* Port 8080 route to Edge Collector
* Port 8081 for GUI access

## Edge Collector
* Port 8080 for route to Central Manager
* Port 8081 for GUI access
* Port 8099 Route to OTM

## IP Configuration
* A static IPv4 or IPv6 address with DNS and NTP access is required.
