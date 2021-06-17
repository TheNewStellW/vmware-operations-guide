---
title: "6. vSAN Configuration"
date: 2021-06-15T21:48:12+10:00
draft: false
weight: 60
---

The dashboard is designed with the same considerations that are common among all the configuration management dashboards. 

## How to Use

The dashboard is organized into 3 sections for ease of use. 

The first section displays 6 pie charts
- There are 5 bar charts that focuses on critical security settings. Their values should match your security policy.
- The last bar chat shows the version of the vSphere Distribution Switch. Aim to keep the version current, or matching your vSphere version.

The second section displays 3 bar charts
- Together, they provide good overview of the vSAN key capacity configuration. By seeing the distribution, you can see if you have capacity configuration that is outside your expectation. 

The last part of the dashboard shows all the vSAN clusters with their key configuration. 
- Some of the columns are color coded to facilitate quick reviews. Adjust their threshold to either reflect your current situation or your desired ideal state
- You can sort the columns and export the result into spreadsheet for further analysis.

## Points to Note

The number of buckets on the pie chart or bar chart are balanced between the available screen estate, ease of use and functionality. Modify the buckets to either reflect your current situation or your desired ideal state.