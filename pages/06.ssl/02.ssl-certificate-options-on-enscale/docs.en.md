---
title: 'SSL Certificate options on Enscale'
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/ssl/ssl-certificate-options-on-enscale'
    'og:type': website
    'og:title': 'SSL Certificate options on Enscale |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/09.ssl/02.ssl-certificate-options-on-enscale/SSL certificate options on Enscale-7.png'
    'og:image:type': image/png
    'og:image:width': 1919
    'og:image:height': 335
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'SSL Certificate options on Enscale |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/09.ssl/02.ssl-certificate-options-on-enscale/SSL certificate options on Enscale-7.png'
    'article:published_time': '2023-08-26T17:53:59+01:00'
    'article:modified_time': '2023-08-26T17:53:59+01:00'
    'article:author': Layershift
media_order: 'SSL certificate options on Enscale-7.png,SSL certificate options on Enscale-6.png,SSL certificate options on Enscale-5 .png,SSL certificate options on Enscale-4.png,SSL certificate options on Enscale-3.png,SSL certificate options on Enscale-2.png,SSL certificate options on Enscale-1.png'
---

As the number of hackers, identity thieves and phishing attacks is constantly increasing, it’s very important to keep the information path between you and your customers’ computers safe and private. With Enscale you can make sure you’ve got this covered by enabling the SSL feature. You can choose between the Shared (free) Enscale SSL or a private SSL certificate. 

Although the Shared SSL is a quick and free solution it’s designed only for testing purposes. For all other cases (e.g. production websites, public demos, anything business critical) we strongly recommend using a Custom SSL to ensure your users see your own domain in the URL without Layershift branding, a shared SSL certificate might raise suspicions. If you try forcing your domain name in the secure connection you will end up getting browser warnings, which will only affect your credibility even more. 

### What’s Enscale Shared SSL? 

As its name suggests, this shared SSL is a free certificate provided by Enscale, available for use to all platform users. The certificate is issued for  *.j.layershift.co.uk and it covers all subdomains under this main domain name. What this means is that you won’t be able to use SSL with a custom domain name, you’ll instead need to use this format: 

**https://your-environment-name.j.layershift.co.uk.** 

Enscale Shared SSL is intended to be used for start-up projects, staging / development websites or in any other scenarios where the secure connections are not intended to be seen by the public.

##### How to enable Shared SSL on Enscale 

* Login to your Enscale account at https://app.j.layershift.co.uk 
* Click on the `Change environment topology` icon (or on the **New Environment** button if you don’t already have one). 

![SSL%20certificate%20options%20on%20Enscale-1](SSL%20certificate%20options%20on%20Enscale-1.png "SSL%20certificate%20options%20on%20Enscale-1") 

* Click on the **SSL icon** to turn on the Jelastic SSL. 

![SSL%20certificate%20options%20on%20Enscale-2](SSL%20certificate%20options%20on%20Enscale-2.png "SSL%20certificate%20options%20on%20Enscale-2")

* Enable `Built-In SSL` option and click `Apply`: 

![SSL%20certificate%20options%20on%20Enscale-3](SSL%20certificate%20options%20on%20Enscale-3.png "SSL%20certificate%20options%20on%20Enscale-3") 
Please note that if you switch IPv4 **ON** for any node in your environment, the Jelastic shared SSL will be automatically disabled. 
### Using your own Custom SSL certificate (recommended) 

**Jelastic’s Custom SSL feature is designed for all production websites** where you can install a certificate issued specifically for your domain name. To be able to install your own custom SSL certificate you will need to add a public IP to your application server or Nginx load-balancer. 

This category of SSL certificates is very popular as it allows you to secure your own branded URL. There are multiple certificate types, depending on the validation process, the number of domains they cover or the level of assurance. We have a [blog article](https://blog.layershift.com/ssl-certificates-explained/) explaining each certificate type in detail so please take a look.

##### Setting up a custom SSL Certificate 

Before you can set up a private SSL you need to make sure you have:

* a **Public IP** 
 
A **public IP** can be switched on from the environment **Topology** settings > click the on/off button to turn on then **Apply**. 

![SSL%20certificate%20options%20on%20Enscale-4](SSL%20certificate%20options%20on%20Enscale-4.png "SSL%20certificate%20options%20on%20Enscale-4") 

* a registered **domain name** 
 
We’re offering a large range of [top-level domains](https://www.layershift.com/hosting/domain-names) so if you haven’t picked your favourite yet, you can do it easily. 

After the IP address is added to your environment you need to point your domain name to the public IP. 

1. Click the additional button for the server in your environment and Copy the Public IP. 

![SSL%20certificate%20options%20on%20Enscale-4](SSL%20certificate%20options%20on%20Enscale-4.png "SSL%20certificate%20options%20on%20Enscale-4") 

2. Set the A Record to point your domain to your Public IP address in your DNS manager at your current domain registrar. 

* an **SSL certificate** 
 
We completely take care of the installation process for you for any certificates purchased from [Layershift](https://www.layershift.com/hosting/ssl-certificates) for use on our hosting services. However, if you’ve already purchased the certificate from a third party, here’s how you can add it to your environment: 

1. Go to your environment and click on the Settings icon. 

![SSL%20certificate%20options%20on%20Enscale-6](SSL%20certificate%20options%20on%20Enscale-6.png "SSL%20certificate%20options%20on%20Enscale-6") 

2. Select the **Custom SSL** option, upload the **Server key**, **Intermediate certificate (CA)** and **Domain certificate** files and then click **Save**. 

![SSL%20certificate%20options%20on%20Enscale-7](SSL%20certificate%20options%20on%20Enscale-7.png "SSL%20certificate%20options%20on%20Enscale-7") 
 
!!!! Your website or application is now secured!