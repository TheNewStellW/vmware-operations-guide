---
title: "5. Regulatory Benchmarks"
date: 2021-06-14T13:57:58+10:00
draft: false
weight: 50
---

Let's talk about out-of-box regulatory benchmarks. As mentioned earlier, vRealize Operations provides the following mentioned benchmarks:

- Center for Internet Security (CIS) security standards
- Defense Information Systems Agency (DISA) security standards
- Federal Information Security Management Act (FISMA) security standards
- Health Insurance Portability and Accountability Act 1996 (HIPAA) Compliance
- ISO security standards
- Payment Card Industry (PCI) security standards

One interesting point to note, all of these benchmarks apply and work on the same set of objects, mostly vCenter, ESXi, VMs, Distributed Port Groups and Distributed Virtual Switch. You may ask if they work on the same environment with a similar security setting, then how are they different?

These regulatory benchmarks are developed and certified by regulatory authorities aiming for specific use cases. Assume an ESXi host has 100 configurations to make. One of the benchmarks may need 60 of them to be configured, another may need another combination of 60 requirements. For example, assume one benchmark only requires the "root" password needs to be set with an expiry time. But another requires password complexity needs to be also set as per defined criteria.

You can apply all of the suggestions from all of the benchmarks and comply to all of them. The purpose of the compliance check is to certify to a regulatory benchmark so that everyone can be sure that the requirements are met. Without the compliance and certification only word of mouth needs to be trusted. The compliance to the benchmark provides the trust and authenticity.

## CIS Security Standards

Center for Internet Security (CIS) Controls and CIS Benchmarks provide global standards for internet security and are a recognized global standard for securing IT systems and data against attacks. vRealize Operations provides Alerts, Policies, and Reports to validate the vSphere resources against the CIS hardening guide[^1]. The following resources are validated using this content:

- ESXi Host
- VM

The CIS standards provides two different areas of suggestions, manual and automated. The following are examples of configuration checked by CIS Security Standards that can be automated:

- Ensure the default value of individual salt per VM is configured. By default, salting is enabled (Mem.ShareForceSalting = 2) and each VM has a different salt. This means page sharing does not occur across the VMs (inter VM TPS) and only happens inside a VM (intra VM).
- Ensure NTP time synchronization is configured properly.
- Ensure the ESXi host firewall is configured to restrict access to services running on the host.
- Ensure Managed Object Browser (MOB) is disabled: The MOB is meant to be used primarily for debugging the vSphere SDK. Because there are no access controls, the MOB could also be used as a method to obtain information about a host being targeted for unauthorized access.
- Ensure default self-signed certificate for ESXi communication is not used.
- Ensure SNMP is configured properly: If SNMP is not properly configured, monitoring data containing sensitive information can be sent to a malicious host and used to help exploit the host.
- Ensure dvfilter API is not configured if not used: If the dvfilter network API is enabled in the future and it is already configured, an attacker might attempt to connect a VM to it, thereby potentially providing access to the network of other VMs on the host.
- Ensure vSphere Authentication Proxy is used when adding hosts to Active Directory: If you configure your host to join an Active Directory domain using Host Profiles the Active Directory credentials are saved in the host profile and are transmitted over the network. To avoid having to save Active Directory credentials in the Host Profile and to avoid transmitting Active Directory credentials over the network use the vSphere Authentication Proxy.
- Ensure VDS health check is disabled: vSphere Distributed switch health check once enabled, collects packets that contain information on host#, vds# port#, which an attacker would find useful.

There are many more such checks performed by CIS Security Standards, for a detailed list download the benchmark from their [website](https://www.cisecurity.org/benchmark/vmware/).

## DISA Security Standards

DISA is a part of the Department of Defense (DoD), and is a combat support agency. Failure to stay compliant with guidelines issued by DISA can result in an organization being denied access to DoD networks. This compliance pack validates the compliance of the following resources:

- vCenter
- ESXi Host
- VM
- Distributed Port Group
- Distributed Virtual Switch

Source: [VMware Marketplace](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-disa?slug=true)

## FISMA Security Standards

FISMA is United States legislation that defines a comprehensive framework to protect government information, operations and assets against natural or man-made threats. This compliance pack validates the compliance of the following resources:

- vCenter
- ESXi Host
- VM
- Distributed Port Group
- Distributed Virtual Switch

Source: [VMware Marketplace](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-fisma?slug=true)

## HIPAA Compliance

HIPAA provides data privacy and security provisions for safeguarding medical information. The vRealize Operations Compliance Pack for HIPAA extends the SDDC compliance capabilities of vRealize Operations. This compliance pack validates the compliance of the following resources:

- vCenter
- ESXi Host
- VM
- Distributed Port Group
- Distributed Virtual Switch

Source: [VMware Marketplace](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-hipaa?slug=true)

## ISO Security Standards

ISO/IEC 27001 is the best-known standard in the ISO/IEC 27000 family of standards providing requirements for an information security management system (ISMS). This compliance pack validates the compliance of the following resources:

- vCenter
- ESXi Host
- VM
- Distributed Port Group
- Distributed Virtual Switch

Source: [VMware Marketplace](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-iso?slug=true)

## PCI Security Standards

The PCI security standards hardening guide addresses the growing threat to consumer payment information. PCI is important to companies that accept, process, or receive payments to prevent, detect and respond to cyber-attacks that can lead to breaches. This compliance pack validates the compliance of the following resources:

- vCenter
- ESXi Host
- VM
- Distributed Port Group
- Distributed Virtual Switch

Source: [VMware Marketplace](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-pci?slug=true)

[^1]: Source: [VMware Marketplace](https://marketplace.cloud.vmware.com/services/details/vrealize-operations-compliance-pack-for-cis/?slug=true#compliance)