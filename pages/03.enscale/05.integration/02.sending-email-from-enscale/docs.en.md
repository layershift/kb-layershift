---
title: 'Sending email from Enscale'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'Layershift''s Enscale application servers run sendmail; integrated email service in the background, enabling you to use PHP mail() function as normal.'
metadata:
    description: 'Layershift''s Enscale application servers run sendmail; integrated email service in the background, enabling you to use PHP mail() function as normal.'
    'og:url': 'https://www.layershift.com/kb/enscale/integration/sending-email-from-enscale'
    'og:type': website
    'og:title': 'Sending email from Enscale | Layershift KB'
    'og:description': 'Layershift''s Enscale application servers run sendmail; integrated email service in the background, enabling you to use PHP mail() function as normal.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-04T08:56:28+00:00'
    'article:modified_time': '2024-03-04T08:56:28+00:00'
    'article:author': Layershift
---

As its main focus is hosting complex websites and applications, Enscale doesn’t include email functionality, but don’t worry there are several options available to you:

## Option 1: Use a dedicated email provider (recommended)

For the best combination of functionality, control, improved deliverability, spam feedback loops, real-time tracking, IP reputation monitoring and more, we recommend using a specialist transactional email provider.

These services cater for transactional email sent from your website/application, and you can simply point your application SMTP configuration at them (or use their APIs) to integrate.

Existing Enscale customers are using the following services:

* Postmark
* Mailjet
* Mailgun
* Sendgrid

At the time of writing, each of these offer a free tier for low volume use.

## Option 2: Use sendmail on your web servers

All Enscale application servers (e.g. Apache, Nginx, Tomcat, Wildfly etc.) run a ‘sendmail’ mail server in the background, enabling you to use JavaMail API or PHP mail() function to send emails from your applications.

!!! For abuse reasons, sendmail is disabled by default on environments created during trial. Please contact our support team with details to request it to be enabled.

We recommend for higher deliverability that you enable a public IP on your web server if you are using this feature. Without a public IP on your web servers, your emails may not be accepted or they might even be filtered as spam.

### To add a public IP follow these simple instructions:

* Login to the [Enscale dashboard](https://app.enscale.cloud/)
* Open the Topology wizard

![Sending%20email%20from%20Enscale-1](Sending%20email%20from%20Enscale-1.png "Sending%20email%20from%20Enscale-1")

* Switch Public IPv4 `ON` and click `Apply`

![Sending%20email%20from%20Enscale-2](Sending%20email%20from%20Enscale-2.png "Sending%20email%20from%20Enscale-2")

## Option 3: Install your own mailserver on an Elastic VPS

You also have the option to install your own mail server on a VPS and configure it any way you wish. The VPS feature on Enscale is called Elastic VPS and provides a plain unmanaged CentOS 7.2 or Ubuntu 16.04 server, with full root access. You are responsible for installing and maintaining any software you require on this node.

!!! The Elastic VPS node type is not available for trial accounts.

Add an Elastic VPS node to your environment by editing the environment topology (as shown below).

![Sending%20email%20from%20Enscale-3](Sending%20email%20from%20Enscale-3.png "Sending%20email%20from%20Enscale-3")
