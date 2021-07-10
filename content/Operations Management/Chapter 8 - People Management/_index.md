---
title: "Chapter 8   People Management"
date: 2021-07-10T08:46:50+08:00 ## This is the first published date
draft: true 
weight: 
---
# Why this chapter
When we introduce a new technology into an organization, we often get asked especially during handing over from project team to operations team, who will be managing this new technology? The purpose of this chapter will serving as a guide to heads of infrastructure, network and security in helping them in organizing their teams to operationalize their IaaS or Cloud. 

# Who owns NSX?
This is a very common question ask when customers are adopting Network Virtualization in their organization. The best answer to this question is like asking a consultant anything, you will get an answer, "It depends". Alright, so lets drill down what does "It depends" entils. The dependence boils down to the resources you have, got to do with skillset of your team, culture, budget, timeline, etc. 

## Model 1: New NSX Engineers
I guess this is the easist solution to the problem which is hiring new members to the team. Find someone who is familiar with NSX, hire them to operation NSX. This is of course assume that you have budget and the market has sufficient NSX Engineers available. Realistically speaking, from my experience, this is hardly implementable because NSX is still a relatively new technology and the adoption is still growing. 

## Model 2: Upskill existing engineers to be skilled with NSX
With the limited people resources and budget that you have and at the same time, you need to take over NSX, the best question to ask yourself would be; Who is the best person in my team for the job? Is it someone from Systems/Compute/Infrastructure Team or someone from the Network Team? Again, the answer depends on the experience of the team members you have. To help you to decide who is best person, you need to consider a few factors again, for example, the experience of the engineer, does he have networking knowledge, how much bandwidth does he/she have to learn NSX and does this person have the growth mindset to learn new technologies? 

The following advice came from observations for the last 6 years on companies who have tried upskilling either the systems or network teams to operate NSX. The more chances of success are the companies who upskill their engineers from the network team to operate NSX. 

The reasons for that are its a too deep learning curve for the systems team to pick up the network fundamentals and at the same time NSX. I'm not implying its impossible but I would say it takes time like 2 to 3 years to learn the networking fundamentals. When you are talking about adopting NSX and transiting to operations, I do not think from the management perspective, they have the luxury to wait for 2-3 years. Also, if you look at the features and terminoloy of the NSX platform, its very geared towards the network engineers who are familar with terms like routing, switching, BGP, OSPF, VPN, NAT, Firewalls and DHCP. Its definately easier for a network engineer to learn NSX and in a shorter timeframe as compared with someone from the systems Team. 

# How to operationalize NSX
The how to operationalize NSX would be much simplier question to tackle, once you identified the personnel to manage this new technology. Its more of planning the learning path of the person and what are some of the trainings required for this person. Again the following would be some guidance on how to train up a network engineer to become an NSX engineer.

- vSphere Training - VCP-DCV Certifications
  - This is required because they need to understand virtualization, what is hypervisor, vCenter, vMotion, Storage, etc.
- NSX Training - VCP-NV, VCIX-NV Certifications
  - Install, Configure, Manage (ICM)
  - Troubleshooting Courses