---
title: "1. Log Analysis Platform"
date: 2021-09-06
draft: false
weight: 10
---

To balance the cost and benefit, you need to design so that majority of logs are not stored for longer than necessary.

- Minimize sending logs over WAN, especially costly WAN link. The main reason is log is local by nature and 99% of them are not even useful to begin with. This means you need to manually forward only the items you need. You complement this by sampling. For example, if there are only 25 VMs on that remote site, then forward the full logs for only 1 VM, to act as sample. Yes, that means you need to pick the VM correctly. By doing this, you save roughly 96%.
- Different purpose, different retention period. For performance, 1 month is more than enough. For audit and compliance, you likely need multiple years. For additional security, keep access to this audit log limited.
The platform should deliver the following benefits
- Preserve logs. Logs are typically rotated, so you lose the old version. Another example is ESXi hits a PSOD and it has no log. That's the end of troubleshooting as there is nothing you can do.
- Only upload to vendor if necessary. This is a big time saving, as uploading GB of data is not easy. Your vendor Support Engineer is able to WebEx or do other remote session. If you are busy attending other matters, the remote session can be delegated to another colleague, as all that is needed is to facilitate the screen sharing session. You can even record it for learning for your broader team.
- Faster analysis. The platform basically acts as the documentation of the product logs. Log Insight comes with hundreds of built-in query for vSphere, SRM, NSX, and vSAN. If you set up alert, you can be informed before the situation degenerates.

With that, let's cover a few practical use cases.