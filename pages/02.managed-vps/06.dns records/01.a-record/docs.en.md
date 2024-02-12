---
title: 'A Record'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/managed-vps/dns%20records/a-record'
    'og:type': website
    'og:title': 'A Record |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/02.managed-vps/06.dns records/02.a-record/A Record.png'
    'og:image:type': image/png
    'og:image:width': 1437
    'og:image:height': 445
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'A Record |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/02.managed-vps/06.dns records/02.a-record/A Record.png'
    'article:published_time': '2024-02-10T15:35:30+00:00'
    'article:modified_time': '2024-02-10T15:35:30+00:00'
    'article:author': Layershift
media_order: 'A Record.png,A Record-2.png'
---

### About A records

A records are among the most frequently utilized records for linking a domain name to a host. They resolve a domain name to an IPv4 address and are specifically designated for websites. Essentially, they establish a connection between your domain and your server's IP address, enabling users to access and load a website without having to remember or input the actual IP address. This process is automated within the user's web browser through a query sent to a DNS resolver.

The significance of DNS A records lies in several key aspects:

* **Enhanced Web Accessibility**: A records translate domain names into IP addresses, ensuring effortless access to your website for users.
* **IP Address Association**: They link your domain with a designated IPv4 address, streamlining the routing of traffic to your server.
* **Load Balancing**: Through the utilization of multiple A records, incoming traffic can be evenly distributed across various servers, thereby enhancing performance and reliability.

### How to create the DNS record within Plesk Dashboard?

Access the desired domain, click on the **Hosting & DNS** tab and press **DNS**:

![A%20Record](A%20Record.png "A%20Record")

Press the blue **Add Record** button and select **A** as record type:

![A%20Record-2](A%20Record-2.png "A%20Record-2")

From this point, feel free to fill the **Domain name**, **IP address**, **TTL** text fields with the necessary information and press the **OK** when you are finished.