---
title: "3. Examples"
date: 2021-06-16T19:45:41+10:00
draft: false
weight: 30
---

I will provide some examples demonstrating the various features of super metrics [functions and operators](https://docs.vmware.com/en/VMware-vRealize-Operations-Cloud/services/config-guide/GUID-7A557E72-0FD0-4AC9-B778-2F492C121EE9.html). More is covered in the manual.

There are many examples in the [repository](https://code.vmware.com/samples) of super metrics.

## Basic Functions

The maximum, minimum, average and sum functions are simple functions that can quickly summarize a large number of objects.

Maximum CPU Ready (%) among VMs within a group of clusters providing same class of service.

`max( ${ adaptertype=VMWARE, objecttype=VirtualMachine, metric=cpu|readyPct, depth=3 } )`

Maximum Memory Balloon (%) among VMs within a group of clusters providing same class of service.

`max( ${ adaptertype=VMWARE, objecttype=VirtualMachine, metric=mem|balloonPct, depth=3 } )`

**Depth=3** is used since the super metric is applied at a custom group level which is 3 levels up the VM object whose metric is used. The hierarchy is Group -> Cluster -> ESXi Host -> VM.

{{% notice info %}}
Tip: If you use the same super metric for different levels, specify the deepest one.
{{% /notice %}}

Sum of vCPUs provisioned on all VMs in a group of VM.

`sum( ${ adaptertype=VMWARE, objecttype=VirtualMachine, metric=cpu|corecount_provisioned, depth=1 } )`

**Depth=1** is sufficient as the VM is directly under the group. No need to manually change the depth.

Average of CPU Usage with all VMs in a custom group:

`avg( ${ adaptertype=VMWARE, objecttype=VirtualMachine, metric=cpu|usage_average, depth=3 } )`

## 'Where' Clause

Things get more powerful and complex once you need to specify a condition.

**Use Case:** Count of all VMs in the environment which has CPU usage greater than 60% at that time.

```text
count(
    ${ adaptertype=VMWARE, objecttype=VirtualMachine, metric=cpu|usage_average, depth=5,
        where=($value > 60)
    }
)
```

{{% notice note %}}
You specify 60 not 60% or 0.6. It has to match the metric value.
{{% /notice %}}

The above formula requires version 8.1 or later.

**Use Case:** Count of all Microsoft Windows VMs.

That means you need to do a string comparison. You also need to know the actual values used by the property field.

```text
count(
    ${ adaptertype=VMWARE, objecttype=VirtualMachine, attribute=summary|guest|fullName, depth=5,
        where="summary|guest|fullName startsWith Microsoft Windows"
    }
)
```

**Use Case:** Identify the percentage of VMs with CPU Ready \> 1%.

That means you need to divide the number of VM against the total number of running VM.

```text
count(
    ${ adaptertype=VMWARE, objecttype=VirtualMachine, metric=cpu|readyPct, depth=8, where=">1" }
    )
/
${ this, metric=summary|running_vms }
* 100
```

The last row is to manually convert into percentage.

**Use Case:** Count of all VMs with CPU usage \> 70% OR memory usage \> 60%

This is a double comparison, with an OR clause. The formula gets complex as super metric is actually a run time code that gets executed directly. There is no translation!

```text
count(
    ${ adaptertype=VMWARE, objecttype=VirtualMachine, metric=cpu|usage_average, depth=8,
        where= ( $value > 70
            ||
            ${ metric=mem|usage_average } > 60
        )
    }
)
```

Notice the first comparison simply uses the variable **$value**, because it's actually defined in the **metric=**.

**Use Case:** Count of all VMs which are not Windows based or Redhat based.

This means you need to negate the comparison. The negation has to be done outside the two comparison.

```text
count(
    ${ adaptertype=VMWARE, objecttype=VirtualMachine, metric=summary|guest|fullName, depth=5,
        where= (! ($value contains 'Microsoft Windows' || $value contains 'Redhat') )
    }
)
```

## If Then Else

This takes you deeper into Java programming

**Use Case:** Count of provisioned vCPUs and if it is equal to 4, return value "1" and if it is not equal to 4, return a value "0".

```text
count( ${this, metric=cpu|corecount_provisioned, depth=1, where= ($value == 4)} )
? 1
: 0
```
{{% notice note %}}
Above formula requires version 8.1 or later.
{{% /notice %}}

**Use Case:** Find the "Actual Recommended vCPU" for a VM.

While using the rightsizing feature, vRealize Operations provide the vCPUs to be removed or added based on if it is an oversized or undersized VM. The following logic can be used find the actual recommended values:

**If** the value of Recommended vCPUs to add is 0,

**then** Actual Recommended vCPU = Provisioned vCPUs - Recommended vCPUs to remove (as an Oversized VM ),

**else** Actual Recommended vCPU = Provisioned vCPUs + Recommended vCPUs to add ( as an Undersized VM ).

```text
${this, metric=summary|undersized|vcpus} == 0
?
( ${this, metric=cpu|corecount_provisioned} - ${this, metric=summary|oversized|vcpus} )
:
( ${this, metric=cpu|corecount_provisioned} + ${this, metric=summary|undersized|vcpus} )
```

This formula uses the **$this**, a reference to the object itself. So the context is not other object.

For completeness, let's do the same for memory. Since the default unit is KB, we would like to convert into GB.

**If** the value of Recommended Memory to add  is 0,

**then** Actual Recommended Memory = Provisioned memory - Recommended Memory to remove (as an Oversized VM),

**else** Actual Recommended Memory = Provisioned Memory + Recommended Memory to add (as an Undersized VM)

```text
(
    ${this, metric=summary|undersized|memory} == 0
    ?
    ( ${this, metric=mem|guest_provisioned} - ${this, metric=summary|oversized|memory} )
    :
    ( ${this, metric=mem|guest_provisioned} + ${this, metric=summary|undersized|memory} )
)

/ 1048576
```