---
title: 'SPF Record'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/managed-vps/dns%20records/spf-record'
    'og:type': website
    'og:title': 'SPF Record |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/02.managed-vps/06.dns records/03.spf-record/SPF-Record.png'
    'og:image:type': image/png
    'og:image:width': 1437
    'og:image:height': 445
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'SPF Record |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/02.managed-vps/06.dns records/03.spf-record/SPF-Record.png'
    'article:published_time': '2024-02-12T04:58:44+00:00'
    'article:modified_time': '2024-02-12T04:58:44+00:00'
    'article:author': Layershift
media_order: 'SPF-Record.png,SPF-Record-2.png'
---

### About SPF record

The **SPF (Sender Policy Framework)** record identifies which mail servers are permitted to send an email on behalf of your domain. It has a key role in preventing spammers from spoofing your domain.To enable SPF, you need to add an SPF record fot your domain name.

To enable SPF, you need to add an SPF record for your domain name. It is a DNS record from the TXT DNS type and it holds the necessary information that allows verifying which e-mail servers are truly authorized to send messages from the name of your domain name.

### How to add an SPF record within Plesk Dashboard?

Access the desired domain, click on the **Hosting & DNS** tab and press **DNS**:

![SPF-Record](SPF-Record.png "SPF-Record")

Press the blue **Add Record** button and select **TXT** as record type:

![SPF-Record-2](SPF-Record-2.png "SPF-Record-2")

From this point, feel free to fill the **Domain name**, **TXT record**, **TTL** text fields with the necessary information and press the **OK** when you are finished.

Below you can find how a SPF record should look:

> Domain name: example.com

> Type: TXT

> TXT Record: "v=spf1 include:_spf.google.com ~all*"

> TTL: 1 hour(3600 seconds)