---
title: "5. vSAN Capacity"
date: 2021-06-15T20:57:36+10:00
draft: false
weight: 50
---

The **vSAN Capacity** dashboard complements the vSphere **Cluster Capacity** dashboard by showing vSAN related capacity. To manage vSAN capacity, use both dashboards.

As this dashboard is designed to complement the vSphere **Cluster Capacity** dashboard, it shares the same design consideration. It focuses on the storage and vSAN specific metrics, and does not repeat what’s already covered. It does not list non vSAN cluster.

See the Capacity Dashboards page for common design consideration among all the dashboards for capacity management. 

## How to Use

The dashboard is layered, gradually providing details as you work top down in the dashboard.

The first layer shows 2 distribution charts
- Bar charts summarize the clusters based on capacity remaining and time remaining. Just because you are running low on capacity does not mean you are running out of time. 
- The two bar charts work together. The ideal situation is low Capacity Remaining and high Time Remaining. This means your resources are cost effective and working as expected.

The second layer shows a heat map
- The three heat maps are Time Remaining, Capacity Remaining, and VM Remaining.
- The cluster size has been made constant for ease of use. If your cluster sizes are not standardized, consider using the number of ESXi hosts to show the size difference. 

The third layer shows a table, accompanied by other widgets to show details of selected cluster
- Clusters Capacity List. If any cluster needs attention, then select the cluster to view the related details.

## Points to Note

If you find it useful, add a drill-down to the **ESXi Capacity** dashboard. A logical place to initiate this drill down is in the **vSAN Cluster List** widget. Link this widget into the table of ESXi Host in the destination dashboard. 

This releases addresses the discrepancy between capacity values for vSAN Datastore and vSAN Cluster objects. Prior to it, the vSAN Cluster deduped & compressed overhead was not considered.
