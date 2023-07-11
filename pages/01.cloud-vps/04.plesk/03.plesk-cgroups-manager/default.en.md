---
title: 'Plesk CGroups Manager'
media_order: 'Screenshot from 2023-07-11 07-15-50.png,Screenshot from 2023-07-11 07-19-55.png'
---

# CGroups Manager - Plesk Extension

### What is CGroups Manager extension?

The Plesk CGroups Manager is a software extension designed to manage the CPU, RAM, and disk read / write bandwidth consumption in a efficient way. It enables users to regulate and allocate system resources effectively, ensuring optimal utilization and performance.

#### Features:

With the CGroups Manager Extension, the user can set upper threshold on each resource and continiously monitor the consumption level of the resource and initiate email notifications when it exceeds the predefined threshold. 

Is it important to note that applying the predefined limitations at the service plan level will impact all subscriptions associated with that particular plan. Alternatively, you can apply specific limititations to individual subscriptions. This approach allows you to set unique constraints on resource utilization for each subscription independently, tailoring the restrictions according to specific requirements or needs.

#### Requirements

The resource manager extension **can't** be installed on a Web Admin Plesk license, you should consider upgrading to the Web Pro license and distribute the websites across multiple subscriptions. This approach enables more efficient management of resource consumption, providing better control and allocation of resources for improved performance.

### Installation procedure

In order to install the CGroups Manager, please proceed to **Tools & Settings > Updates > Add / Remove Components**:

![Screenshot%20from%202023-07-11%2007-15-50](Screenshot%20from%202023-07-11%2007-15-50.png "Screenshot%20from%202023-07-11%2007-15-50")

Find **Resource Controller (Cgroups)**, select **Install** and press the blue **Continue** button:

![Screenshot%20from%202023-07-11%2007-19-55](Screenshot%20from%202023-07-11%2007-19-55.png "Screenshot%20from%202023-07-11%2007-19-55")

Once the component is installed, initiate the activation of the component by accessing **Tools & Settings > Services Management Link** and start the **Resource Controller(Cgroups)** service:







