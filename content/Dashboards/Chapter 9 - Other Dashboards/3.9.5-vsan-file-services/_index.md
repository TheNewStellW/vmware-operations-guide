---
title: "5. vSAN File Services"
date: 2021-06-16T14:04:20+10:00
draft: false
weight: 50
---

The **vSAN File Services** Dashboard helps VMware administrator monitor the file services running in their vSAN environment.

This dashboard is designed to complement the vSAN file services management provided by vCenter Server. It does not duplicate information already provided, and each tool has their purpose. vCenter is more of an administrative tool, while vRealize Operations is more of an operations tool.

## How to Use

Review the “**File Shares by Used Space and Latency**” heat map

-   It shows all the file shares in your environment.

-   The greater the usage (consumption), the greater the box, so you can easily see the most consumed ones.

-   They are colored by latency. Pay attention to the box with red color.

Review the “**vSAN Clusters with File Services enabled**” table

-   It lists all the vSAN clusters with file services enabled, giving a convenient view to see which clusters have these settings turned on.

Select a vSAN cluster from the table

-   The file servers in the selected vSAN cluster will be automatically shown. Selecting a file server will filter the file shares list to only show the file shares in the selected file server.

-   The file shares in the selected vSAN cluster will be automatically shown. Selecting a file share will display all the relevant KPI on the file share.

#### Points to Note

vSAN File Servers and vSAN File Shares are 2 new objects in vRealize Operations vSAN management pack.