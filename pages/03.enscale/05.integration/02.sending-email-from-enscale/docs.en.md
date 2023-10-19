---
title: 'Sending email from Enscale'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/integration/sending-email-from-enscale'
    'og:type': website
    'og:title': 'Sending email from Enscale |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/05.integration/03.sending-email-from-enscale/Sending email from Enscale-1.png'
    'og:image:type': image/png
    'og:image:width': 1100
    'og:image:height': 72
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Sending email from Enscale |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/05.integration/03.sending-email-from-enscale/Sending email from Enscale-1.png'
    'article:published_time': '2023-09-10T09:33:54+01:00'
    'article:modified_time': '2023-09-10T09:33:54+01:00'
    'article:author': Layershift
media_order: 'Sending email from Enscale-1.png,Sending email from Enscale-2.png,Sending email from Enscale-3.png'
---

As its main focus is hosting complex websites and applications, Enscale doesn’t include email functionality, but don’t worry there are several options available to you:

#### Option 1: Use a dedicated email provider (recommended)

For the best combination of functionality, control, improved deliverability, spam feedback loops, real-time tracking, IP reputation monitoring and more, we recommend using a specialist transactional email provider.

These services cater for transactional email sent from your website/application, and you can simply point your application SMTP configuration at them (or use their APIs) to integrate.

Existing Enscale customers are using the following services:

* Mailjet
* Mailgun
* Sendgrid

At the time of writing, each of these offer a free tier for low volume use.

#### Option 2: Use sendmail on your web servers

All Enscale application servers (e.g. Apache, Nginx, Tomcat, Wildfly etc.) run a ‘sendmail’ mail server in the background, enabling you to use JavaMail API or PHP mail() function to send emails from your applications.

!!! For abuse reasons, sendmail is disabled by default on environments created during trial. Please contact our support team with details to request it to be enabled.

We recommend for higher deliverability that you enable a public IP on your web server if you are using this feature. Without a public IP on your web servers, your emails may not be accepted or they might even be filtered as spam.

##### To add a public IP follow these simple instructions:

* Login to the [Enscale dashboard](https://app.enscale.cloud/)
* Open the Topology wizard

![Sending%20email%20from%20Enscale-1](Sending%20email%20from%20Enscale-1.png "Sending%20email%20from%20Enscale-1")

* Switch Public IPv4 `ON` and click `Apply`

![Sending%20email%20from%20Enscale-2](Sending%20email%20from%20Enscale-2.png "Sending%20email%20from%20Enscale-2")

### Option 3: Install your own mailserver on an Elastic VPS

You also have the option to install your own mail server on a VPS and configure it any way you wish. The VPS feature on Jelastic is called Elastic VPS and provides a plain unmanaged CentOS 7.2 or Ubuntu 16.04 server, with full root access. You are responsible for installing and maintaining any software you require on this node.

!!! The Elastic VPS node type is not available for trial accounts.

Add an Elastic VPS node to your environment by editing the environment topology (as shown below).

![Sending%20email%20from%20Enscale-3](Sending%20email%20from%20Enscale-3.png "Sending%20email%20from%20Enscale-3")