---
title: "8 Distribution Chart Limitation"
date: 2021-06-15T14:44:26+10:00
draft: false
weight: 80
---

There are 2 types of distribution charts: 
- **Relative distribution**: pie chart and donut chart
- **Absolute distribution**: bar chart

They have the following limitations:
- `“No data to display”` does not imply that there is something wrong with vRealize Operations data collection process. It might signify that none of the objects meets the filtering criteria of the widget, hence there is really nothing to display. 
- To see the content of a slice in a pie-chart or a bucket in a bar-chart, simply click on it. Note that the list cannot be exported. You can however click on the object name, which will take you to the object summary page. The page provides key configuration information, alongside other summary information.
- The pie-chart and bar-chart cannot drive other widgets. For example, you cannot select one of the pie-slices or buckets, and expect it to act as a filter to a list or a table.
- You can apply a specific color in a pie chart or distribution chart for a specific numeric value, but not string value. For example, you can’t apply a red color to the value “Not Installed”.