---
title: "7. VM Reclamation"
date: 2021-06-15T21:07:00+10:00
draft: true
weight: 70
---

The VM Reclamation dashboard helps you managing various types of reclamation that can be done on VMs. It is designed for both the Capacity team and the Operations team.

## How to Use

The dashboard is divided into 2 sections.
- The upper section provides summary, giving you overall picture of reclamation.
- The lower section provides details, giving you the actual VM name to reclaim.
![](3.3.7-fig-1.png)
 
Select a data center from the table. 
- The summary information will be automatically shown. To show from all clusters, select vSphere World. This object covers all clusters. Take note that the charts will take longer due to refresh due to higher amount of data.
- The reclamation potentials are presented as 3 bar charts, each corresponds to an area you can reclaim:
  - Snapshot. Especially those more than a few days old as snapshot is meant to be temporary.
  - Powered off VM. Assuming they are already backed up, it’s safe to delete them from vSphere.
  - Idle VM. You get to reclaim memory, not CPU. Idle VM memory still occupies ESXi physical memory.
- The Idle VM does not display any CPU as there is practically nothing to reclaim as the overhead of idle CPU is being used. The primary benefit for CPU is capacity, especially the overcommit ratio.
- Memory reclamation is based on the memory footprint at the parent ESXi. The value inside the Guest is not what is being reclaimed, and so it is irrelevant. That’s why the VM consumed memory is chosen.
- Adjust the bucket size in the charts to suit your operational requirements.
Review each of the 3 tables
- They are sorted by the largest reclamation opportunities. 
- Select any of the VM row to see its trend over time. The trend chart is placed in the same page, so you can review without changing context (e.g. open a new screen) and quickly toggle between VMs.
- If the snapshot is expanding rapidly, ensure that the VM disk is large (relative to the underlying datastore) as it can fill up the datastore.

## Points to Note

If your environment is large, change the dashboard filter to a functional filter. Group by the class of services such as Gold, silver, and bronze and default the selection to the least critical environment. In this way, you can be active in reclamation.

If reclaiming is a long drawn manual process in your organization, add a filter by department or VM owners. One way to do this is to create a vRealize Operations custom group.

If the VM name in your environment does not provide sufficient business context, add more information in the table to give context to the VM. Information such as VM Owner, clusters where the VM is running, and datastores where the VM files are stored can be useful in the analysis. 

Disk cannot be reclaimed immediately. They have to be in the powered-off stage at least for a week.

You should enhance this to include [Trim and Unmap](https://en.wikipedia.org/wiki/Trim_(computing)). Happy to collaborate and make this into the product. We need to check on only the thin provisioned disk. We should also check at the array level, using the TVS adapter.