# IL5 SaaS Collector Requirements

This IL5 collector requirements document provides critical collector specifications which are required by the client to successfully deploy an Armis Collector within the Armis Government Cloud (AGC)(IL5) instance.

**Table of Contents**
  * [STIG Deviation](#stig-deviation)
  * [OS & Hardware Requirements](#os--hardware-requirements)
  * [Core OS Dependencies & Packages](#core-os-dependencies-packages)
  * [Container Runtime](#container-runtime)
  * [Packet Capture & Network Libraries](#packet-capture--network-libraries)
  * [Cryptography & Transport](#cryptography--transport)
  * [Utility Packages](#utility-packages)
  * [Collector Network & Port Requirements](#collector-network--port-requirements)
  * [Inbound (Passive Traffic Ingestion)](#inbound-passive-traffic-ingestion)
  * [Outbound (Collector to Cloud Transmission)](#outboun-collector-to-cloud-transmission)
---
## STIG Deviation
RHEL 8 Ver 2 Rel 8 (2026-07-10)

V-230554: This STIG item requires the OS to not allow for network interfaces to be able to be placed within promiscuous mode. A network interface being in promiscuous mode is a requirement for the Armis Government Cloud IL5 collector to ingest mirrored SPAN/TAP traffic without dropping packets. Ensure to inform the client of this as a deviation and acceptance thereof must be documented with their compliance team.


## OS & Hardware Requirements
* OS = RHEL 8.10
* CPU = 8 CPU (min)
* RAM = 16 GB (min)
* Storage = 40 GB SSD (min)


## Core OS Dependencies & Packages
The host os must have the following system utilities, container runtimes and libraries pre-installed or available via package management prior to installing the Armis Collector application (RPM) on the RHEL 8.10 virtual machine.

## Container Runtime
Podman must be installed on the RHEL 8.10 virtual machine provided. Armis collectors run as containerized microservices on the RHEL OS within Podman.

## Packet Capture & Network Libraries
1. libpcap & libpcap-devel: Both of these libraries must be installed as they are crucial for raw network packet sniffing, SPAN/TAP interface monitoring and deep packet inspection.
2. tcpdump & iproute2: Both of these libraries must be installed as they are for network traffic diagnostic verification and route management within the collector.
3. ethtool: This library must be installed for tuning network interface capabilities (such as offloading and promiscuous mode settings).

## Cryptography & Transport
* OpenSSL (v1.1.1 or v3.0+): Must support TLS 1.2 or TLS 1.3 for secure telemetry transport back to the Armis Government Cloud tenant.

## Utility Packages
* curl & wget: These packages must be installed as they are used during installation and automated collector bundle updates from the Armis Government Cloud tenant.
* tar, gzip, unzip: These packages are required for extracting update bundles and diagnostic logs.

## Collector Network & Port Requirements

