---
title: 'Plesk mail in Thunderbird'
media_order: 'step_1_thunderbird.png,step_2_thunderbird.png,step_3_thunderbird.png,step_3_alt_thunderbird.png'
metadata:
    description: 'Here is a step-by-step guide to help you configure Plesk mail in Outlook.'
    'og:url': 'https://www.layershift.com/kb/managed-vps/email/plesk-mail-in-thunderbird'
    'og:type': website
    'og:title': 'Plesk mail in Thunderbird | Layershift KB'
    'og:description': 'Here is a step-by-step guide to help you configure Plesk mail in Outlook.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2026-02-05T16:51:25+00:00'
    'article:modified_time': '2026-02-05T16:51:25+00:00'
    'article:author': Layershift
content:
    items:
        - '@self.children'
    limit: 5
    order:
        by: date
        dir: desc
    pagination: true
    url_taxonomy_filters: true
aura:
    pagetype: website
    description: 'Here is a step-by-step guide to help you configure Plesk mail in Outlook.'
taxonomy:
    category:
        - docs
menu: 'Plesk mail in Thunderbird'
---

Here is a step-by-step guide to help you configure Plesk mail in Thunderbird.

### Step 1

Open Thunderbird and select to set up an email:

![step_1_thunderbird](step_1_thunderbird.png "step_1_thunderbird")
### Step 2

Enter your name, as you want it to appear in any messages you send, email address and password:

![step_2_thunderbird](step_2_thunderbird.png "step_2_thunderbird")

### Step 3

In the manual configuration, adjust the incoming and outgoing Hostname to match your Plesk VPS hostname. The Ports and Connection security should either use `STARTTLS` or `SSL/TSL` (with associated ports seen in example pictures): 

![step_3_thunderbird](step_3_thunderbird.png "step_3_thunderbird")

Alternate port and Connection security option:

![step_3_alt_thunderbird](step_3_alt_thunderbird.png "step_3_alt_thunderbird")

Once set, click `Re-test`:

### Step 4

If the Re-test was successful, you can click Done to finish setting up your email.