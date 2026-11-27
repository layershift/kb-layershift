---
title: 'Support Scope'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://www.layershift.com/kb/managed-vps/docker/support-scope'
    'og:type': website
    'og:title': 'Support Scope | Layershift KB'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2026-08-18T15:44:52+01:00'
    'article:modified_time': '2026-08-18T15:44:52+01:00'
    'article:author': Layershift
---

Due to the vast flexibility and nature of Docker images, we cannot provide our usual level of end-to-end support and management for Docker as we do for the rest of your server. This page summarises the shared responsibility model applicable to running Docker on Plesk at Layershift: which aspects we can help you with, and which aspects are your responsibility.

## Supported by Layershift

* Advice and guidance on how to deploy and configure Docker via the Plesk interface (i.e. using the Plesk Docker extension)
* Backup and restore of data stored within Docker volumes (i.e. via your VPS's chosen backup plan)
* Security of the underlying host operating system - in this case, the host is your VPS, so we manage and maintain that as an integral part of your Managed VPS subscription
* Network - again, in this case the network is the same as your VPS's, so we manage and maintain it as an integral part of your Managed VPS subscription
* Physical security of the underlying hardware - as an integral part of your Managed VPS subscription

## Your responsibilities

* Evaluating the relative merits of one Docker image or another: there are often multiple images for popular applications. You need to decide which publisher to trust and which image best suits your particular use case; we cannot make this decision for you.
* Configuring the deployed Docker container / application within: the publisher of a given image usually provides instructions (e.g. which environment variables are recognised, and what various values will do); we cannot know the intricacies of the applications/images you're deploying any better than the documentation provided by its author - they are the best placed to help with these topics.
* Secure configuration of the application: you must ensure that your application not only works, but is configured in line with security best practices - consult the application author's documentation for guidance.
* Timely deployment of required security updates: Docker images contain a whole OS stack, so you must remain vigilant not only to application-level security updates (e.g. within Valkey), but also within rest of the image (e.g. within Alpine, Debian etc. as applicable to your chosen image).
* Implementation of access controls: any user authentication or firewall ACLs required to prevent unauthorised access to your application must be implemented within the Docker image since the VPS firewall doesn't apply to the Docker container.

### Tips

* Some publishers provide security information about their images (e.g. Docker Hardened Images, Docker Official Images), tracking known vulnerabilities for each tag.
* Avoid use of ambiguous tags (e.g. "latest") which will become confusing over time: specific named tags make it much easier to evaluate which versions you have deployed, and therefore what your current security posture is (which things need updating!)
* Make sure your Docker container is only accessible from the Internet if required (i.e. use the option "Make the port inaccessible to the internet" on all mapped ports that don't need to be accessible from the internet.)
* Double-check your Volume mapping before creating any data inside the Docker container (otherwise it will be lost!)
