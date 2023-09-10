---
title: 'LiteSpeed Web Server on Enscale'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/litespeed/litespeed-web-server-on-enscale'
    'og:type': website
    'og:title': 'LiteSpeed Web Server on Enscale |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/06.litespeed/litespeed-web-server-on-enscale/LiteSpeed Web Server on Enscale-8.png'
    'og:image:type': image/png
    'og:image:width': 886
    'og:image:height': 491
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'LiteSpeed Web Server on Enscale |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/06.litespeed/litespeed-web-server-on-enscale/LiteSpeed Web Server on Enscale-8.png'
    'article:published_time': '2023-09-10T10:38:10+01:00'
    'article:modified_time': '2023-09-10T10:38:10+01:00'
    'article:author': Layershift
media_order: 'LiteSpeed Web Server on Enscale-8.png,LiteSpeed Web Server on Enscale-1.png,LiteSpeed Web Server on Enscale-2.png,LiteSpeed Web Server on Enscale-3.png,LiteSpeed Web Server on Enscale-4.png,LiteSpeed Web Server on Enscale-6.png,LiteSpeed Web Server on Enscale-7.png,LiteSpeed Web Server on Enscale-5.png'
---

### What is LiteSpeed?

LiteSpeed Web Server is the 5th most popular web server out there and as of April 2020, it’s been the choice of almost 6.4% of the websites on the public internet, according to Wikipedia. It is developed by LiteSpeed Technologies under a proprietary license, but there is also an open-source version called OpenLiteSpeed maintained at the same standards under the GPLv3 license.

#### When to use it?

LiteSpeed comes in handy when deploying your web applications and promises very high performance in comparison with other similar solutions.

LiteSpeed is a good option to consider if you want to benefit from the event-driven scalability of Nginx, combined with the ability to use Apache’s configuration syntax (such as .htaccess) which in some cases you might find easier to migrate to, or just prefer out of personal preference.

#### Why choose LiteSpeed over other web servers?

At a first glance, LiteSpeed promises to evade the effort of getting acquainted with a new configuration template, by offering an almost fully compatible interface with Apache. Moreover, it also features Apache capabilities like **mod_rewrite**, **mod_security**, and **.htaccess**, which ease the transition. From a caching perspective, LiteSpeed doesn’t need an extra HTTPS reverse proxy to access the 3rd party plugins.

In particular, when deploying either WordPress or Magento platforms, the yielded results under stress go high above its competitors.

![LiteSpeed%20Web%20Server%20on%20Enscale-1](LiteSpeed%20Web%20Server%20on%20Enscale-1.png "LiteSpeed%20Web%20Server%20on%20Enscale-1")

Among the supported protocols, the most important to mention is the HTTP up to version 3. Also, there is support for LSPHP with suEXEC that outperforms PHP-FPM in every single way.

As for the hardware requirements, they are considerably lower due to the event-driven architecture and SSL offloading capabilities, thus allowing thousands of parallel connections with only a fraction of the processes needed by other web servers. Basically LiteSpeed Web Server supports an unlimited number of connections.

![LiteSpeed%20Web%20Server%20on%20Enscale-2](LiteSpeed%20Web%20Server%20on%20Enscale-2.png "LiteSpeed%20Web%20Server%20on%20Enscale-2")

Security-wise, LiteSpeed WebServer helps you shield your server from HTTP Flood and other similar DDoS attacks, quickly and easily, using one-click [reCAPTCHA](https://docs.litespeedtech.com/products/lsws/recaptcha/) validation.

### LiteSpeed license costs

The commercial versions of LiteSpeed Web Server and LiteSpeed ADC (Load Balancer) are subject to licensing fees and therefore adding it to your environment will generate additional costs.

##### LiteSpeed Web Server

Normally, LiteSpeed Web Server licenses are leased on a monthly (or yearly) basis and you have to pay a fixed fee in advance. The main advantage of using Jelastic is that you pay-per-use, so when your environments are stopped, your LiteSpeed Web Server costs are zero. No commitments here!

Cloudlet usage | Domain Limit | Workers | Price per hour
-------------------- | ------------------ | ----------- | ------------------ 
        1 - 16        |          1           |       1       |      Free       
      17 - 64        |          5           |       1       |      £0.11
     Unlimited     |          5           |       1       |      £0.175
 
##### LiteSpeed ADC (Load Balancer)

This license is charged based on the network traffic processed by the node at the rates below:

LiteSpeed as Load Balancer (price per node) 
------------------------------------------------------------ |
           1p / GB (max £65 / month)

!!! If traffic levels are zero, you will still be charged a minimum of 1p/hour.

### How to configure LiteSpeed Web Server on Jelastic PaaS

Create a new environment and pick the LiteSpeed Web Server for the Application Nodes:

![LiteSpeed%20Web%20Server%20on%20Enscale-3](LiteSpeed%20Web%20Server%20on%20Enscale-3.png "LiteSpeed%20Web%20Server%20on%20Enscale-3")

If you want to scale up with more than one Application Node, add a Load Balancer Node:

Adjust the scaling setting as desired. The default Scaling limit for a LiteSpeed Web Server node is 6 cloudlets, but you can increase this up to a total of 16 Cloudlets, without being charged any LiteSpeed licensing fees. Since Jelastic only bills for the cloudlets that are actually used (not just allocated), it’s actually recommended to allow some room for your server to scale up during busy times.

![LiteSpeed%20Web%20Server%20on%20Enscale-4](LiteSpeed%20Web%20Server%20on%20Enscale-4.png "LiteSpeed%20Web%20Server%20on%20Enscale-4")

Your new environment has now been created:

![LiteSpeed%20Web%20Server%20on%20Enscale-5](LiteSpeed%20Web%20Server%20on%20Enscale-5.png "LiteSpeed%20Web%20Server%20on%20Enscale-5")

### Adding Virtual Hosts from the Configuration Panel 

Unlike its competitors **Nginx** and **Apache**, **LiteSpeed Web Server** has a unique feature: the config panel, which allows you to quickly add or edit virtual hosts. Check your email after the environment is created for the login credentials to the **LiteSpeed Configuration** panel.

![LiteSpeed%20Web%20Server%20on%20Enscale-6](LiteSpeed%20Web%20Server%20on%20Enscale-6.png "LiteSpeed%20Web%20Server%20on%20Enscale-6")

In the **Configuration** tab, among other options, there is also a quick **virtual-host** provisioning choice.

![LiteSpeed%20Web%20Server%20on%20Enscale-7](LiteSpeed%20Web%20Server%20on%20Enscale-7.png "LiteSpeed%20Web%20Server%20on%20Enscale-7")

As shown in the screenshot below, adding a new vhost is quite a simple procedure.

![LiteSpeed%20Web%20Server%20on%20Enscale-8](LiteSpeed%20Web%20Server%20on%20Enscale-8.png "LiteSpeed%20Web%20Server%20on%20Enscale-8")

### Conclusion

At first glance, LiteSpeed Web Server presents itself as the choice to out rule them all. Not only it provides the same features as the major web servers on the market, but it also performs better, with lower resource consumption. Noticeably, it’s the only one of its kind to provide a graphical user interface for configuration purposes, thus being more accessible to the end-users who do not possess a more advanced technical expertise.




