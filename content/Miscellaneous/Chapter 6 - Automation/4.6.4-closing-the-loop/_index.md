---
title: "4. Closing the Loop"
date: 2021-06-16T22:30:24+10:00
draft: true
weight: 40
---

Now with the ability to connect back to vRealize Operations to either retrieve data or push custom information, we can finally close the loop to achieve a fully featured closed-control loop. The next picture represents our closed-loop control system including all concepts we have learned in the previous sections of this chapter.

If you compare the next picture to figure 16, you will notice that now we have a continuous and closed-loop between the entity executing our automated actions and the entity collecting the data which reflect the behavior of objects we control. We are no longer limited to the “fire and forget, until the sensors do something” method. With the possibility to execute callbacks to the REST API, vRealize Operations becomes an integral part of an automated SDDC solution.

![](4.6.4-fig-1.png "Closed-loop control with vRealize Operations")

Let us now come back to our initial use case: “If a VM (the OS) crashes, this VM should be hard-reset”. How could we expand that use case and have a sophisticated and automated remediation using all the concepts I have presented in this chapter. We will examine the next picture and extract the possible components of the automation.

![](4.6.4-fig-2.png "Full automation using vRealize Operations")

The central control point is of course vRealize Operation itself.

-   The vCenter Adapter instance is continuously collecting metrics which describes the current behavior of our SDDC, including the behavior of our VMs.

-   Within vRealize Operations we have an Alert Definition that utilizes certain symptoms to fire an alarm when the symptoms indicate that something is wrong, in our use case a VM probably crashed. “Probably” because we are evaluating symptoms, and symptoms do not necessarily point directly to a root cause.

-   As soon as the alarm has been raised, the configured Notification:

    -   Creates a problem ticket in ServiceNow

    -   Sends a notification email to the admin team

-   At the same time, the Action configured within the Recommendation starts a vRealize Orchestrator Workflow. The workflow itself may (this is just an example):

    -   Tries to connect to the VM via RDP or SSH

    -   Executes ping or TCP connect checks

    -   Reset the VM if the configured checks underpin the initial assumption

    -   Checks the availability of the VM

    -   Checks the alert status in vRealize Operations and updates it if required

    -   Push additional properties (like e.g., count of vRealize Orchestrator initiated rest events) to the VM object

-   As soon as the alarm status changes, the configured Notification:

    -   Updates the problem ticket in ServiceNow

    -   Sends another notification email to the admin team

With vRealize Operations, its comprehensive REST API, the wide range of Management Packs, integrated Notification Plugins and the capability to run Actions using vRealize Orchestrator you have wide possibilities to automate your SDDC management and level it up to become Self-Driving SDDC.