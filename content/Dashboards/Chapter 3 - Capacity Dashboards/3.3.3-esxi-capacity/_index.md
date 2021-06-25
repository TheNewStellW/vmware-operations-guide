---
title: "3. ESXi Capacity"
date: 2021-06-15T20:31:50+10:00
draft: false
weight: 30
---

The ESXi Capacity dashboard supports the **Cluster Capacity** dashboard by providing the next level of details. It is also required for the non-clustered ESXi. 

See the Capacity Dashboards page for common design consideration among all the dashboards for capacity management. 

## How to Use

The **Summary** heat map provides an overall view of ESXi Hosts capacity, grouped by their clusters. 
 
- Each ESXi Host is represented by a box, showing their capacity remaining. 
- The ESXi host size has been made constant for ease of use. If your ESXi sizes are not standardized, consider using the number of physical cores or Total CPU GHz to show the size difference. Check that the smallest ESXi does not become too small.

About the ESXi Hosts Capacity table 
- The table lists all the ESXi hosts in your environment, grouped by their parent cluster. Standalone ESXi will be shown at the bottom under “No Group” 
- In a large environment with many data centers, you can zoom into specific vCenter or Data center. You can also filter or search for specific ESXi hosts matching certain names. 
- The 99th percentile Performance column takes the 99th percentile value of the ESXi Performance (%) metric. The reason we're not taking the worst performance (which is equivalent to 100thpercentile) is to rule out outlier. In addition, the performance threshold has been set to be stringent.

Select one of the ESXi
- All the 3 line charts will automatically show the trend of selected ESXi Host. 
- Both total and usable utilization in terms of memory and CPU are displayed
- Utilization displayed for three months and not one week. The daily average is displayed and not the hourly average and the focus is on memory consumed and not memory active. Note that memory consumed includes the total memory consumed, so it includes memory consumed by VMkernel.

## Points to Note
- If you find it useful, add a drill-down to the VM Capacity dashboard. A logical place to initiate this drill down is in the ESXi Hosts Capacity widget. Link this widget into the table of ESXi Host in the destination dashboard. 
- A technology refresh is often used to address capacity shortage. Consider adding a property widget that shows the hardware model and specification to help you determine the age of the hardware. 