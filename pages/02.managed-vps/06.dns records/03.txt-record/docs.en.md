---
title: 'TXT Record'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/managed-vps/dns%20records/txt-record'
    'og:type': website
    'og:title': 'TXT Record |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/02.managed-vps/06.dns records/04.txt-record/SPF-Record.png'
    'og:image:type': image/png
    'og:image:width': 1437
    'og:image:height': 445
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'TXT Record |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/02.managed-vps/06.dns records/04.txt-record/SPF-Record.png'
    'article:published_time': '2024-02-12T05:55:36+00:00'
    'article:modified_time': '2024-02-12T05:55:36+00:00'
    'article:author': Layershift
media_order: 'SPF-Record.png,SPF-Record-2.png'
---

### About TXT Record

The TXT record furnishes textual data accessible to entities beyond your domain, serving both human and machine readership for diverse objectives. Typically, it includes domain particulars alongside crucial information for authentication and email confirmation purposes.

The content within a TXT record serves multifaceted roles. However, its primary utility revolves around:

* **Establishing domain ownership**: Various providers such as Google, Office 365, etc., often mandate the inclusion of a distinct verification code within your DNS zone via TXT record. This process substantiates your ownership of the specific domain.
* **Mitigating email spam**: Additionally, TXT records are frequently employed for SPF, DKIM, and DMARC domain keys, serving as a deterrent against email spam.

### How to add an SPF record within Plesk Dashboard?

Access the desired domain, click on the **Hosting & DNS** tab and press **DNS**:

![TXT-Record](SPF-Record.png "TXT-Record")

Press the blue **Add Record** button and select **TXT** as record type:

![TXT-Record-2](SPF-Record-2.png "TXT-Record-2")

From this point, feel free to fill the **Domain name**, **TXT record**, **TTL** text fields with the necessary information and press the **OK** when you are finished.


