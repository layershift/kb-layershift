---
title: 'Introducing Cloudlets'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'What is a cloudlet? We measure RAM & CPU usage in this special combined resource unit on our Enscale PaaS to help simplify the billing model. One Cloudlet is roughly equivalent to 128MiB RAM and 400MHz CPU. Using this scale, a Cloudlet is the maximum of: RAM: the maximum RAM usage over the hour CPU: the average CPU usage ..'
metadata:
    description: 'What is a cloudlet? We measure RAM & CPU usage in this special combined resource unit on our Enscale PaaS to help simplify the billing model. One Cloudlet is roughly equivalent to 128MiB RAM and 400MHz CPU. Using this scale, a Cloudlet is the maximum of: RAM: the maximum RAM usage over the hour CPU: the average CPU usage ..'
    'og:url': 'https://www.layershift.com/kb/enscale/getting-started/introducing-cloudlets'
    'og:type': website
    'og:title': 'Introducing Cloudlets | Layershift KB'
    'og:description': 'What is a cloudlet? We measure RAM & CPU usage in this special combined resource unit on our Enscale PaaS to help simplify the billing model. One Cloudlet is roughly equivalent to 128MiB RAM and 400MHz CPU. Using this scale, a Cloudlet is the maximum of: RAM: the maximum RAM usage over the hour CPU: the average CPU usage ..'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-04T10:37:51+00:00'
    'article:modified_time': '2024-03-04T10:37:51+00:00'
    'article:author': Layershift
---

## What is a cloudlet

We measure RAM & CPU usage in this special combined resource unit on our Enscale PaaS to help simplify the billing model.

One Cloudlet is roughly equivalent to 128MiB RAM and 400MHz CPU.

Using this scale, a Cloudlet is the maximum of:

* **RAM**: the maximum RAM usage over the hour
* **CPU**: the average CPU usage over the hour

For example, if you use 512MiB (peak) during an hour, you can use an average of 1.6GHz CPU in that hour at no extra charge – so in this case you’d only pay for 4 Cloudlets – saving you money.

All Enscale PaaS resources are billed on an hourly basis, so if your usage is variable from one hour to the next Enscale saves you a lot of money vs. other solutions.

## Dynamic Cloudlets

One of the many unique benefits of the Enscale PaaS is its ability to dynamically scale server resources for you automatically – based entirely on application demand.

Dynamic Cloudlets make that magic happen – they’re added instantly when you need them, and gracefully removed again as soon as you’re done with them. This helps you to cope with celebrity endorsements (e.g. Twitter or Facebook mentions), or any other unexpected surges in demand, without any pre-planning or special coding.

Thanks to the hourly billing, you only pay for those additional resources for the limited amount of time that you need them (you no longer need to upgrade your entire hosting package for 1 month or 1 year just to cope with a short term spike in demand!).

! Keep complete control over the maximum amount of Dynamic Cloudlets that can be added to each of your servers by setting the Scaling Limit.
Simply set the Scaling Limit slider to the desired setting when you create (or edit) your environment in the topology wizard.

## Reserved Cloudlets

You can now configure **Reserved Cloudlets** for your servers to “pre-book” resource usage in advance. **You always pay for Reserved Cloudlets (even if your actual resource usage is lower)** – but in exchange you get up to 30% discount compared to Dynamic Cloudlets.

If you prefer the certainty of fixed pricing, simply set all of your servers to only use **Reserved Cloudlets** (set the Reserved Cloudlet slider to the same amount as the Scaling Limit slider) – of course you lose the benefits of automatic scaling if you do that, so it’s not recommended!

!!! TIP: Use Reserved Cloudlets for your typical usage (to pay the minimum price) combined with the powerful automatic scaling provided by Dynamic Cloudlets to handle your unexpected peaks in demand.

![Introducing%20Cloudlets-1](Introducing%20Cloudlets-1.png "Introducing%20Cloudlets-1")

## Automatic Discounts

Everyone loves a discount, and with Layershift’s Enscale PaaS you earn discounts automatically!

**The more cloudlets (Reserved, Dynamic – or both) that you use, the bigger the discounts are:**

### Dynamic Cloudlet Discounts

![Introducing%20Cloudlets-2](Introducing%20Cloudlets-2.png "Introducing%20Cloudlets-2")

Discounts for **Dynamic Cloudlets** are applied automatically based on your usage each hour. So if you use a total of 8 Dynamic Cloudlets (across all servers in your environment), you automatically receive a 10% discount. Then if the next hour your usage increases to **16 Dynamic Cloudlets**, your discount level also increases to 20%!

### Reserved Cloudlet Discounts

![Introducing%20Cloudlets-3](Introducing%20Cloudlets-3.png "Introducing%20Cloudlets-3")

Discounts for Reserved Cloudlets are also applied automatically – but in this case during configuration in the topology wizard.

As you add more and more Reserved Cloudlets to the environment, you’ll see a bar on the right of the wizard showing the discount you’re getting, and the details of the next discount tier (in some cases it might be cheaper to add just 1 more cloudlet to hit the next discount tier):

![Introducing%20Cloudlets-4](Introducing%20Cloudlets-4.png "Introducing%20Cloudlets-4")