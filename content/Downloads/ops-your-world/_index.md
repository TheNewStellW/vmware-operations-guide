---
title: "Operationalize Your World"
date: 2021-10-08
disabletoc: false
draft: false
aliases: [
    "/oyw",
    "/opsyourword",
    "/operationalize-your-world"
]
---

![](operationalize-your-world.png)

Operationalize Your World (OYW) is a program created by Kenon Owens back in 2016. Its purpose built to help large VMware customers derive value from vRealize Operations and Log Insight. While it's designed for existing vRealize customers, it had worked well with potential customers. It comes in the form of a small focused workshop, typically around 10 - 30 technical IT Architect/Administrators who have interest on day to day operations and capacity management. Ideally they run similar size of operations.

The workshop material:
1. PowerPoint deck. Used to facilitate discussion and for audience to tailor and present internally.
1. vRealize Operations kit. A set of dashboards, views, super metrics that customers can import. It requires latest version of vRealize Operations.
1. A Book. A Microsoft Word document. The documentation of OYW, which customers can adopt and tailor as their internal operations guidebook.
1. The site. What you're reading right now. VMwareOpsGuide site covers more than the book, but the site may lag by a few months as it takes time to manually sync hundreds of pages that evolves every month.

Think of Operationalize Your World as the Pro edition of the plain vRealize Operations. Using analogy from the car industry, it’s like the AMG line of Mercedes. It’s designed for advanced customers who need customized version. It requires the Advanced edition or higher.

OYW 8.6 is based on vRealize Operations 8.6, meaning it uses this version as the base for customization. vRealize Operations 8.6 sports a set of revamped dashboards, which were ported from OYW after they have been proven with customers. So OYW also serves as the alpha version of the content.

## Differences

The difference between OYW and the OOTB vRealize Operations is summarized below. In future, I may add more, such as Business Application dashboard.

| Differences | Why |
| --- | --- |
| It uses the 20-second peak metric instead of the standard 300-second | With 15X sharper visibility, you can see problems that do not sustain for entire 300 seconds. Most issues on disk latency, CPU ready and memory contention do not typically last 300 seconds  |
| It adds Guest OS contention | Problem closer to application tend to impact the application more. All it needs is VMware Tools. No other agent required |

{{< downloads folder="operationalize-your-world" boxTitle="Download" />}}

## How to Install

1. Login as admin account. It has to be the local admin account as that’s the ID that is used to create the original dashboard.
1. Enable the 12 peak metrics. Go to your default policy, search for “collection cycle”. Enable them all, as shown below:
![](Policy.png)
1. Import the views. Make sure you choose to overwrite existing views. OYW modified 3 views.
1. Import the dashboard. Make sure you choose to overwrite existing dashboard. OYW modifies the VM Performance dashboard.
1. Get a cup of coffee. Wait ~10 minutes for the dashboards to settled. All the "Hour Glass" icons will disappear.

Optional Step: disable the following dashboards as they are redundant:

- VM Contention
- VM Utilization
- Cluster Contention
- Cluster Utilization
- ESXi Contention
- ESXi Utilization
- vSAN Contention
- vSAN Utilization
- ESXi Capacity
