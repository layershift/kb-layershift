---
title: 'Plesk CGroups Manager'
published: true
aura:
    pagetype: website
    description: 'The Plesk CGroups Manager is designed to manage the CPU, RAM, and disk read/write bandwidth consumption in an efficient way.'
metadata:
    description: 'The Plesk CGroups Manager is designed to manage the CPU, RAM, and disk read/write bandwidth consumption in an efficient way.'
    'og:url': 'https://www.layershift.com/kb/managed-vps/plesk/plesk-cgroups-manager'
    'og:type': website
    'og:title': 'Plesk CGroups Manager | Layershift KB'
    'og:description': 'The Plesk CGroups Manager is designed to manage the CPU, RAM, and disk read/write bandwidth consumption in an efficient way.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-02T23:21:43+00:00'
    'article:modified_time': '2024-03-02T23:21:43+00:00'
    'article:author': Layershift
taxonomy:
    category:
        - docs
---

The Plesk CGroups Manager is a software extension designed to manage the CPU, RAM, and disk read/write bandwidth consumption in an efficient way. It enables users to regulate and allocate system resources effectively, ensuring optimal utilization and performance.

## Features:

With the CGroups Manager Extension, the user can set the upper threshold on each resource and continuously monitor the consumption level of the resource and initiate email notifications when it exceeds the predefined threshold. 

Is it important to note that applying the predefined limitations at the service plan level will impact all subscriptions associated with that particular plan. Alternatively, you can apply specific limitations to individual subscriptions. This approach allows you to set unique constraints on resource utilization for each subscription independently, tailoring the restrictions according to specific requirements or needs.

## Requirements

The resource manager extension **can't** be installed on a Web Admin Plesk license, therefore you should consider upgrading to the Web Pro license and distributing the websites across multiple subscriptions. This approach enables more efficient management of resource consumption, providing better control and allocation of resources for improved performance.

## How to configure the CGroups Manager?

Before you start setting up the CGroups Manager extension, it is important to remember that incorrectly configuring it can have a negative impact on the functionality of your website. This can result in slower performance or even render it unavailable. Therefore, it is crucial that you carefully read and comprehend the instructions provided on this topic before making any modifications.

You have the flexibility to configure the CGroups Manager extension at different levels, including the **Service Plan** level, where the settings will impact all subscriptions associated with that plan. Additionally, you can configure it all at the **Subscription** level, allowing you to customize the settings for individual subscriptions.

### Service Plan level

To configure the resource manager at the Service Plan level, please follow the provided instructions:

* From your **Plesk Dashboard**, access **Service Plan > Hosting Plans**:

![Plesk-CGroups-Manager-1](Plesk-CGroups-Manager-1.png "Plesk-CGroups-Manager-1")

* Select the desired service plan you want to configure CGroups Manager, open **RAM, CPU, Disk I/O** tab, and set the thresholds:

![Plesk-CGroups-Manager-2](Plesk-CGroups-Manager-2.png "Plesk-CGroups-Manager-2")

### Subscription level

To configure the resource manager at the **Subscription** level, please follow the provided instructions:

* From your **Plesk Dashboard**, access **Subscriptions** and select the desired subscription:

![Plesk-CGroups-Manager-3](Plesk-CGroups-Manager-3.png "Plesk-CGroups-Manager-3")

* Once you selected the desired subscription, expand the right sidebar using the button shown in the screenshot:

![Plesk-CGroups-Manager-9](Plesk-CGroups-Manager-9.png "Plesk-CGroups-Manager-9")

* Scroll down to **Account** and press **Customize**:

![Plesk-CGroups-Manager-10](Plesk-CGroups-Manager-10.png "Plesk-CGroups-Manager-10")

* Once there, you are ready to configure: 

![Plesk-CGroups-Manager-11](Plesk-CGroups-Manager-11.png "Plesk-CGroups-Manager-11")

## Limiting Resource Consumption

### Setting up the Limits

##### If a specific resource is limited for a particular subscription:

* The CGrouos Manager actively monitors all processes associated with the system user of that subscription. Collectively, these processes must not exceed the threshold that was set for each resource. If the subscription reaches its limit, the operating system takes a predefined action depending on the type of resource. It's important to note that even if there are unused resources of the corresponding type available on the server (such as idle CPU cycles or free RAM), the subscription cannot surpass its assigned limit.

##### If a resource is not limited for a given subscription:

* The processes linked to the subscription are allowed to utilize as much of the unrestricted resources as much of the unrestricted resource as is currently available. This resource is shared among the processes of all subscriptions. CPU time and disk I/O are distributed nearly equally among the processes, while RAM is shared based on the requirements of each process.

#### Allowed Setting Values for Monitoring

The thresholds settings may have the following values:

* CPU limit: **Percentage of CPU time**, where 100% is one CPU core fully used
* RAM limit: **MB / GB value** - representing the amount of RAM that can be used by the subscription/service plan
* Disk Read: **MB per second / GB per second** - the amount of disk read bandwidth that can be used by the subscription/service plan
* Disk Write: **MB per second / GB per second** - the amount of disk write bandwidth that can be used by the subscription/service plan

## Setting up Monitoring

Once you have established resource limits for a particular resource, you can configure it to send notifications whenever the specified threshold for that resource is exceeded. To enable this feature, you must ensure that the `Notify when exceeded` threshold is set for the resource in question, and then activate the `Notification enabled` option.

![Plesk-CGroups-Manager-8](Plesk-CGroups-Manager-8.png "Plesk-CGroups-Manager-8")

### Recipients and Content of the Notifications

In order to configure who will receive the notifications, please do the following:

* Go to `Tools & Settings` and access **Notifications**:

![Plesk-CGroups-Manager-6](Plesk-CGroups-Manager-6.png "Plesk-CGroups-Manager-6")

* In the `Event` column, find `RAM, CPU, and Disk I/O (Cgroups)` and place the desired `Email addresses`:

![Plesk-CGroups-Manager-7](Plesk-CGroups-Manager-7.png "Plesk-CGroups-Manager-7")






