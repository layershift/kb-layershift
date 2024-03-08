---
title: 'How to configure Plesk mail in Mac'
metadata:
    description: 'Here is a step-by-step guide on how to configure Plesk mail in Mac.'
    'og:url': 'https://www.layershift.com/kb/managed-vps/email/how-to-configure-plesk-mail-in-mac'
    'og:type': website
    'og:title': 'How to configure Plesk mail in Mac | Layershift KB'
    'og:description': 'Here is a step-by-step guide on how to configure Plesk mail in Mac.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-05T18:48:16+00:00'
    'article:modified_time': '2024-03-05T18:48:16+00:00'
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
menu: 'Plesk mail in Mac'
aura:
    pagetype: website
    description: 'Here is a step-by-step guide on how to configure Plesk mail in Mac.'
taxonomy:
    category:
        - docs
---

Here is a step-by-step guide to help you configure Plesk mail in Mac.

### Step 1

Open Mail, either from **Dock**:

![1_Configure-Plesk-mail-in-Mac-Step-1A](1_Configure-Plesk-mail-in-Mac-Step-1A.png "1_Configure-Plesk-mail-in-Mac-Step-1A")

or from **Spotlight** (CMD+Space):

![3_Configure-Plesk-mail-in-Mac-Step-2](3_Configure-Plesk-mail-in-Mac-Step-2.png "3_Configure-Plesk-mail-in-Mac-Step-2")

### Step 2

On the Finder bar, click ‘Mail’ and select `Accounts`.

![2_Configure-Plesk-mail-in-Mac-Step-1B](2_Configure-Plesk-mail-in-Mac-Step-1B.png "2_Configure-Plesk-mail-in-Mac-Step-1B")

### Step 3

Expand `Add Other Account`:

![4_Configure-Plesk-mail-in-Mac-Step-3](4_Configure-Plesk-mail-in-Mac-Step-3.png "4_Configure-Plesk-mail-in-Mac-Step-3")

### Step 4

Select `Mail account`:

![5_Configure-Plesk-mail-in-Mac-Step-4](5_Configure-Plesk-mail-in-Mac-Step-4.png "5_Configure-Plesk-mail-in-Mac-Step-4")

### Step 5

Provide your email login details:
    
![6_Configure-Plesk-mail-in-Mac-Step-5](6_Configure-Plesk-mail-in-Mac-Step-5.png "6_Configure-Plesk-mail-in-Mac-Step-5")

### Step 6

To discover incoming and outgoing mail server settings for you account, please visit [this site](https://info.layershift.com/mail/) and use your email address as a parameter.

### Step 7

Select the account type (**POP** or **IMAP**) and enter the incoming and outgoing mail server names.
If you have doubts on whether POP3 or IMAP suits you best, see our article about [general settings](../how-to-configure-plesk-mail#incoming-mail-settings).

![7_Configure-Plesk-mail-in-Mac-Step-6](7_Configure-Plesk-mail-in-Mac-Step-6.png "7_Configure-Plesk-mail-in-Mac-Step-6")

### Step 8

If you receive a SSL Certificate warning please open a support ticket at [help.layershift.com](https://help.layershift.com) in order to investigate the mail server setup:

![8_Configure-Plesk-mail-in-Mac-Step-7](8_Configure-Plesk-mail-in-Mac-Step-7.png "8_Configure-Plesk-mail-in-Mac-Step-7")

### Step 9

To accept the certificate permanently tick ‘Always trust’ and hit ‘Continue’.

![9_Configure-Plesk-mail-in-Mac-Step-8](9_Configure-Plesk-mail-in-Mac-Step-8.png "9_Configure-Plesk-mail-in-Mac-Step-8")

### Step 10

To set up **SMTP** (outgoing mail) select to ‘Preferences’ from the ‘Mail’ menu.

![10_Configure-Plesk-mail-in-Mac-Step-10](10_Configure-Plesk-mail-in-Mac-Step-10.png "10_Configure-Plesk-mail-in-Mac-Step-10")

### Step 11

Expand **SMTP** and choose `Edit SMTP Server List` from the drop down menu:

![11_Configure-Plesk-mail-in-Mac-Step-11](11_Configure-Plesk-mail-in-Mac-Step-11.png "11_Configure-Plesk-mail-in-Mac-Step-11")

### Step 12

Go to the `Advanced` tab, set Authentication to **Password** and enter your login details.
    
![12_Configure-Plesk-mail-in-Mac-Step-11](12_Configure-Plesk-mail-in-Mac-Step-11.png "12_Configure-Plesk-mail-in-Mac-Step-11")
