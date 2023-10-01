---
title: 'Change environment owner'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/getting%20started/change-environment-owner'
    'og:type': website
    'og:title': 'Change environment owner |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/04.getting started/07.change-environment-owner/Change environment owner-1.png'
    'og:image:type': image/png
    'og:image:width': 1104
    'og:image:height': 443
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Change environment owner |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/04.getting started/07.change-environment-owner/Change environment owner-1.png'
    'article:published_time': '2023-10-01T16:00:46+01:00'
    'article:modified_time': '2023-10-01T16:00:46+01:00'
    'article:author': Layershift
media_order: 'Change environment owner-1.png,Change environment owner-2.png,Change environment owner-3.png,Change environment owner-4.png'
---

Any environment that you create in your Enscale account can now be transferred to another Enscale user. The environment owner is responsible for usage charges, and may control which users have collaborative access to it – if you want to change the person in your organisation with these responsibilities, this gives you a way forward.

This feature is also perfect for digital agencies and freelancers. It allows you to create, fully configure, deploy, and test an environment for your customer – then when you’re done you can transfer billing responsibility for this environment to your customer as part of the project handover process. It saves you time (you don’t have to redo that work on a new environment they create for themselves), and avoids many potential headaches.

### How to transfer an environment to a new owner

* Enter **Environment Settings** for the environment that you wish to transfer:

![Change%20environment%20owner-2](Change%20environment%20owner-2.png "Change%20environment%20owner-2")

* Go to **Change owner** and enter the new owner’s Enscale account email address.

![Change%20environment%20owner-1](Change%20environment%20owner-1.png "Change%20environment%20owner-1")

You can only transfer the environment to an existing user with a **paid** account; you will receive a warning if the person you wish to transfer it to does not have an account, or their account is not in the correct status (e.g. a trial or expired account).

! If you want to transfer to a user without a Jelastic account, add them as a collaborator on your account first, and then simply ask them to upgrade to a paid account.

* An approval email is sent to the new owner, since they will become responsible for all future usage charges for this environment as soon as the transfer completes. They must click a link in the email to complete the transfer. The link expires after 7 days.

Meanwhile you can view the transfer status in **Environment Settings > Change owner**, and if you change your mind you may cancel the transfer request to immediately invalidate the approval link.

![Change%20environment%20owner-3](Change%20environment%20owner-3.png "Change%20environment%20owner-3")

The environment is marked with a custom icon within your environment list, so you can see at a glance that it has a pending transfer request:

![Change%20environment%20owner-4](Change%20environment%20owner-4.png "Change%20environment%20owner-4")

* The environment owner is changed immediately as soon as the new owner clicks the ‘accept’ link in their approval email. The previous environment owner also receives a courtesy notification to inform them that the transfer was completed successfully.

Usage charges for the environment for each subsequent hour are charged to the new owner. Historical charges remain on the previous owner’s account.

### Special Notes

#### Environment collaboration users are removed upon transfer completion

Any users sharing the environment are immediately removed (from this environment only) when the transfer completes. This is an important security feature to ensure that the new owner is explicitly aware of all users with access to the environment, and permission levels are explicitly set by the new owner to suit their own needs.

#### Environments can be transferred in any status

There is no requirement for the environment to be running. You may transfer an environment even if it is stopped.

#### No disruption to environment operation

All environment settings, alerts, scaling thresholds, files, configuration settings, IP addresses etc. are retained entirely untouched during the transfer process. There are no changes to the server(s) themselves, which remain online and fully operational throughout the transfer process.
