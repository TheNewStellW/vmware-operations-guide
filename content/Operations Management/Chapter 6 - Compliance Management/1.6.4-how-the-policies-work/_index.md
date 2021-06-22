---
title: "4. How the Policies Work"
date: 2021-06-14T13:53:48+10:00
draft: false
weight: 40
---

Having covered what is provided in vRealize Operations, let’s discuss how these policies work. What do they do? Underlying all these policies are certain configurations and alert settings. As per the official documentation, “all the compliance standards in vRealize Operations, including any standards that you define, are based on alert definitions. Only alert definitions of the Compliance subtype are counted. Custom score cards can monitor user-defined alerts.”[^1].

For example, “ISO Security Standards” checks for the following among many other points:

- Configure the SSH Service on the ESXi Hosts for Compliance
- Restrict remote access to the host by disabling the SSH service and the shell service and enabling lockdown mode
- Provide complex password in vCenter Server
- Configure lockout in vCenter Server

All these configurations are checked in the environment. Symptoms are defined in the environment against these checks and finally alerts are set against those symptoms.

If any alerts are raised then there is a misconfiguration against the set policy which needs to be corrected.

This also leads to the scope of defining own custom Symptom -> Alerts -> Benchmarks.

[^1]: Source: [VMware Documentation](https://docs.vmware.com/en/vRealize-Operations-Manager/8.3/com.vmware.vcom.config.doc/GUID-A4FBC2C3-6F43-4C45-BD19-72A11110745E.html)