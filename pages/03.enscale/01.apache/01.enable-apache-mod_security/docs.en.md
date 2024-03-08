---
title: 'Enable Apache mod_security'
aura:
    pagetype: website
    description: 'On Enscale PaaS, you can benefit from custom Apache modules, including mod_security2. Learn how to add it to your Apache server.'
metadata:
    description: 'On Enscale PaaS, you can benefit from custom Apache modules, including mod_security2. Learn how to add it to your Apache server.'
    'og:url': 'https://www.layershift.com/kb/enscale/apache/enable-apache-mod_security'
    'og:type': website
    'og:title': 'Enable Apache mod_security | Layershift KB'
    'og:description': 'On Enscale PaaS, you can benefit from custom Apache modules, including mod_security2. Learn how to add it to your Apache server.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-03T03:24:09+00:00'
    'article:modified_time': '2024-03-03T03:24:09+00:00'
    'article:author': Layershift
taxonomy:
    category:
        - docs
---

Mod_security operates embedded into the web server, acting as a powerful umbrella – shielding applications from attacks.

In Enscale, you can add this module to your Apache server. As Enscale gives full access to Apaches config files you can define your own custom rules in mod_security.conf. The module can be added to new environments only and it is disabled by default, but can enabled really easy by following these simple steps:

* Log in to your [Enscale dashboard](https://app.enscale.cloud/).
* Click **Config** on the Application Node:

![Enable%20Apache%20mod_security-1](Enable%20Apache%20mod_security-1.png "Enable%20Apache%20mod_security-1")

* Access the **conf.modulesd/** directory and search for `10-mod_security.conf` and click on it:

![Enable%20Apache%20mod_security-2](Enable%20Apache%20mod_security-2.png "Enable%20Apache%20mod_security-2")

* Once there, activate mod_security by uncommenting the two LoadModule lines in **10-mod_security.conf** (mod_security2 + mod_unique_id):

![Enable%20Apache%20mod_security-3](Enable%20Apache%20mod_security-3.png "Enable%20Apache%20mod_security-3")

* Finally, restart Apache and you can start using the **mod_security** module:

![Enable%20Apache%20mod_security-4](Enable%20Apache%20mod_security-4.png "Enable%20Apache%20mod_security-4")