# IL5 SaaS Collector Requirements

This IL5 collector requirements document provides critical collector specifications which are required by the client to successfully deploy an Armis Collector within the Armis Government Cloud (AGC)(IL5) instance.

**Table of Contents**
  * [STIG Deviation](#stig-deviation)
  * [OS & Hardware Requirements](os-hardware-requirements)
  * [Core OS Dependencies & Packages](core-os-dependencies-packages)
  * [Container Runtime](container-runtime)
  * [Packet Capture & Network Libraries](packet-capture-network-libraries)
  * [Cryptography & Transport](cryptography-transport)
  * [Utility Packages](utility-packages)
  * [Collector Network & Port Requirements](collector-network-port-requirements)
  * [Inbound (Passive Traffic Ingestion)](inbound-passive-traffic-ingestion)
  * [Outbound (Collector to Cloud Transmission)](outboun-collector-to-cloud-transmission)
---
## STIG Deviation
RHEL 8 Ver 2 Rel 8 (2026-07-10)

V-230554: This STIG item requires the OS to not allow for network interfaces to be able to be placed within promiscuous mode. A network interface being in promiscuous mode is a requirement for the Armis Government Cloud IL5 collector to ingest mirrored SPAN/TAP traffic without dropping packets. Ensure to inform the client of this as a deviation and acceptance thereof must be documented with their compliance team.
