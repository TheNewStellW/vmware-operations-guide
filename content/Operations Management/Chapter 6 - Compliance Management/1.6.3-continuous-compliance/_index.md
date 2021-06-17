---
title: "3. Continuous Compliance"
date: 2021-06-14T13:48:19+10:00
draft: false
weight: 30
---

While configuring an environment according to the security guidelines is very important, that is just the starting point. Maintaining the same level of configuration on an ongoing basis is of utmost importance. With time configurations drifts occur. How do we make sure the changed environment is still compliant to the set policies? In every organization a compliance test is done on a regular interval, say once a week. What about the status between the checks? Consider the following situation where an organization scheduled a compliance check every week on Sunday at 10 p.m. So, the check catches any drift in between and reported accordingly.

![](1.6.3-fig-1.png)

In the above example, between 1st and 2nd week the configuration drift was unreported for days and between 3rd and 4th week it went unreported for days. This may lead to serious security lapse or concerns.

vRealize Operations provides alerts, policies, and reports to validate the vSphere resources against these benchmarks, delivering a **continuous compliance** checking every 5 minute with alerts. It provides multiple ways to check compliance against a defined benchmark. This includes VMware recommended suggestions, benchmarks from regulatory organizations and even enables you the ability to define a custom policy. Note, these are three different categories of benchmarks available in vRealize Operations with no interdependence. These are listed below in the order they merely appear in the page rather than a preference. Their details are provided below:

##### VMware SDDC Benchmarks

These are pre-defined VMware benchmarks which monitors the environment against various VMware defined security recommendations. These are further categorized into the following three sub-categories:

- vSphere Security Configuration Guide
- vSAN Security Configuration Guide 
- NSX-T Security Configuration Guide

##### Custom Benchmarks

Build your own custom benchmarking policies and check the environment against those custom defined policies.

##### Regulatory Benchmarks

Out of the box regulatory compliances, specifically the following:
- CIS Security Standards
- DISA Security Standards
- FISMA Security Standards
- HIPAA Compliance
- ISO Security Standards
- PCI Security Standards

While VMware SDDC benchmarks provide guidance for securely configuring the virtualized environment, the regulatory benchmarks serve a different purpose. Both the regulatory benchmarks and VMware benchmarks provide similar guidance on the same objects but the regulatory bodies certify the requirements.

For example, assume I am a consumer from health industry. Hence I have specific security requirements. How do I know whether the provider I am considering has the necessary security in place? This is where the regulatory benchmarks come in handy. These are tried and tested guidelines aiming for specific industry and requirement. So, if a provider complies to HIPAA benchmark I can be assured that this provider will cater to my security requirement.

Now imagine taking the HIPAA benchmark guideline and its hundreds of recommendations, implementing it and constantly checking to make sure the environment is compliant. This would require a great deal of work on an ongoing basis. Next consider implementing vRealize Operations and enabling the HIPAA benchmark. You get a dashboard card showing what the compliance status is. For variance you know exactly what needs to be fixed and you can fix it in a jiffy. Just share the report with the customer at any time to prove you are compliant to the requirement.

Note: by default all these policies not activated. For the VMware SDDC benchmarks you can enable them from the same page. But for the regulatory benchmarks you need to enable them from the repository.

These benchmarks are enabled per defined “policies” in vRealize Operations. That means you can check different environments for different benchmarks. For example,  consider an organization consisting of two different environments. The first environment needs to be HIPAA compliant and the second one needs to be PCI compliant. So, create two different policies for these two environments and then enable benchmarks accordingly to these environments and respective policies. As an example, consider a hospital. In hospitals they store patient information which requires a HIPAA compliant environment. At the same time they accept online payments for the services they provide. This requires an environment which needs to be PCI compliant. One solution to this may be to build a virtualized environment managed by a vCenter server and set up two different clusters catering to the above requirements. With the vRealize Operations integration, we can apply two different policies for these two clusters and apply two different benchmarks to these respectively. This will ensure the required HIPAA and PCI compliance for the environments.