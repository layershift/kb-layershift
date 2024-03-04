---
title: 'BitNinja on Enscale'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'BitNinja is an optional paid add-on that provides full-stack server protection for your Enscale environment nodes.'
metadata:
    description: 'BitNinja is an optional paid add-on that provides full-stack server protection for your Enscale environment nodes.'
    'og:url': 'https://www.layershift.com/kb/enscale/security/bitninja-on-enscale'
    'og:type': website
    'og:title': 'BitNinja on Enscale | Layershift KB'
    'og:description': 'BitNinja is an optional paid add-on that provides full-stack server protection for your Enscale environment nodes.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-04T10:01:56+00:00'
    'article:modified_time': '2024-03-04T10:01:56+00:00'
    'article:author': Layershift
---

BitNinja is an optional paid add-on that provides full-stack server protection for your Enscale environment. It’s a good option if you need to secure your nodes against all kinds of cyber threats such as SQL injections, malware, and DoS attacks.

### Main features

* Detect and block botnets
* Find backdoors
* Zero-day protection against CMS vulnerabilities
* Block SQL injection, XSS, remote and local file injections
* Stop brute force attacks
* Detect and mitigate DoS attacks

### Enscale node compatibility

BitNinja is supported and can be installed on nearly all Enscale node types. For maximum protection, we recommend to install BitNinja on each layer of your environment to protect against the different types of threats faced by each part of your application stack.

### How to Install BitNinja on Enscale

* Open your [Enscale dashboard](https://app.enscale.cloud/) and expand the environment where you wish to install the BitNinja add-on.
* Select **Add-Ons** for the layer you want to install BitNinja on (Apache Application server in our example):

![BitNinja%20on%20Enscale-1](BitNinja%20on%20Enscale-1.png "BitNinja%20on%20Enscale-1")

* Find **BitNinja** Service in the **Add-Ons** list, and click **Install**:

![BitNinja%20on%20Enscale-2](BitNinja%20on%20Enscale-2.png "BitNinja%20on%20Enscale-2")

* Review the install dialog, click Install and wait for the installation to complete:

![BitNinja%20on%20Enscale-3](BitNinja%20on%20Enscale-3.png "BitNinja%20on%20Enscale-3")

!!! Note: You will receive a license key activation email from BitNinja during the installation process – ignore that, Enscale installs the BitNinja agent for you automatically.

![BitNinja%20on%20Enscale-4](BitNinja%20on%20Enscale-4.png "BitNinja%20on%20Enscale-4")

When installation is completed, the Add-Ons panel contains controls to access the **BitNinja Admin Panel** and **Restart Agent**.

* Repeat the steps for **every layer** in your environment for maximum protection!

![BitNinja%20on%20Enscale-5](BitNinja%20on%20Enscale-5.png "BitNinja%20on%20Enscale-5")

### How to use BitNinja

BitNinja does not require much work or attention from your side – the service largely takes care of itself, keeping your servers safe and secure in the background whilst you focus on the things that make your business money!

You can access the **BitNinja Admin Panel** using the button in the Add-Ons panel shown above in order to:

* Enable/disable applicable modules
* Fine-tune module settings
* View incident reports
* Enable and manage WAF rulesets
* Initiate or schedule a malware scan

### BitNinja help

If you need help with any BitNinja feature, you can simply [contact the experts at BitNinja](https://bitninjaio.atlassian.net/servicedesk/customer/portal/1) directly for guidance.

* [BitNinja Documentation](https://doc.bitninja.io/docs/intro/)
* [BitNinja Knowledge Base](https://knowledgebase.bitninja.io/)

