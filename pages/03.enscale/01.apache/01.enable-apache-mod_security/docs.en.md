---
title: 'Enable Apache mod_security'
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/apache/enable-apache-mod_security'
    'og:type': website
    'og:title': 'Enable Apache mod_security |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/01.apache/01.enable-apache-mod_security/Enable Apache mod_security-1.png'
    'og:image:type': image/png
    'og:image:width': 1098
    'og:image:height': 143
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Enable Apache mod_security |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/01.apache/01.enable-apache-mod_security/Enable Apache mod_security-1.png'
    'article:published_time': '2023-08-27T06:41:33+01:00'
    'article:modified_time': '2023-08-27T06:41:33+01:00'
    'article:author': Layershift
media_order: 'Enable Apache mod_security-1.png,Enable Apache mod_security-2.png,Enable Apache mod_security-3.png,Enable Apache mod_security-4.png'
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