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

Operationalize Your World (OYW) is a program created by Kenon Owens, Sunny Dua and Iwan Rahabok back in 2016. Its purpose built to help large VMware customers derive value from vRealize Operations and Log Insight. While it's designed for existing vRealize customers, it had worked well with potential customers. It comes in the form of a small focused workshop, typically around 10 - 30 technical IT Architect/Administrators and Head of Infrastructure Operations, who have direct responsibilities on day to day operations and capacity management. Ideally the attendees run similar size of operations, as there is a lot of peer discussion & networking in the workshop.

The workshop material:
1. PowerPoint deck. Used to facilitate discussion and for audience to tailor and present back internally to CIO and application teams (take away deck)
1. vRealize Operations kit. A set of dashboards, views, super metrics, and alerts that customers can import. It was built on the latest version of vRealize Operations. They are not tested on earlier versions, so upgrade yours first.
1. A Book. A Microsoft Word document. The documentation of OYW, which customers can adopt and tailor as their internal operations guidebook.
1. The site. What you're reading right now. VMwareOpsGuide site covers more than the book, but the site may lag by a few months as it takes time to manually sync hundreds of pages that evolves every month.

Think of Operationalize Your World as the Pro edition of the plain vRealize Operations. Using analogy from the car industry, it’s like the AMG line of Mercedes. It’s designed for advanced customers who operate large scale Infrastructure, hence need a customized version. Product wise, it requires the Advanced edition or higher.

Traditionally, the customisation eventually made it into the product. I'd port selected contents after they have been proven with customers. So OYW also serves as the alpha version of the content.

## Differences

The difference between OYW and the OOTB vRealize Operations is summarized below. In future, I may add more, such as Kubernetes and Horizon.

| Differences | Why |
| --- | --- |
| It uses the 20-second peak metric instead of the standard 300-second | With 15X sharper visibility, you can see problems that do not sustain for entire 300 seconds. Most issues on disk latency, CPU ready and memory contention do not typically last 300 seconds  |
| It adds Business Application dashboard | Enable you to monitor your business critical applications. Create multi tier business applications. For each of them, add the relevant tiers using custom groups |
| It reduces the alert noise | I deprecates 20 alerts and replaces them with improved alerts and daily proactive check dashboard | 
| It adds Guest OS visibility | Problem closer to application tend to impact the application more. Note this requires Telegraf agent for each Windows or Linux |

{{< downloads folder="operationalize-your-world" boxTitle="Download" />}}

## How to Install

Review the PowerPoint first. At the end of the deck, there is the on-boarding guide. Follow it closely.

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
