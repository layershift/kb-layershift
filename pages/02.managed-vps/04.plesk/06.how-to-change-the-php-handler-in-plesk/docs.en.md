---
title: 'How to change PHP handler in Plesk'
aura:
    pagetype: website
    description: 'Find out how to change PHP version and PHP handler in Plesk. Step by step guide.'
metadata:
    description: 'Find out how to change PHP version and PHP handler in Plesk. Step by step guide.'
    'og:url': 'https://www.layershift.com/kb/managed-vps/plesk/how-to-change-the-php-handler-in-plesk'
    'og:type': website
    'og:title': 'How to change PHP handler in Plesk | Layershift KB'
    'og:description': 'Find out how to change PHP version and PHP handler in Plesk. Step by step guide.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2025-06-26T16:40:04+01:00'
    'article:modified_time': '2025-06-26T16:41:11+01:00'
    'article:author': Layershift
taxonomy:
    category:
        - docs
menu: 'Change PHP Version'
media_order: 'plesk-dashboard-php.png,change php handler.png,change php version.png'
---

In Plesk, you have the flexibility to easily modify PHP handler without experiencing any server or domain downtime. This feature can be particularly advantageous for enhancing website performance or switching to your preferred PHP handler, if you have one in mind! When PHP operates, it creates new files and writes to existing ones using the user it runs as.

## Available handlers

* 	FPM (FastCGI Process Manager) - Best performance, recommended for most sites.
* 	FastCGI - Most commonly used, reliable, and generally good performance. (required when using LiteSpeed)
* 	CGI -Older method, slower, only use if required.

Below are step-by-step instructions guiding you on how to change the PHP handler directly from within the Plesk Dashboard:

![plesk-dashboard-php](plesk-dashboard-php.png "plesk-dashboard-php")
![change%20php%20handler](change%20php%20handler.png "change%20php%20handler")

### FastCGI application served by Apache
* The default option on many servers
* Stable, secure, and widely compatible
* Starts a new PHP process for each request (less efficient)

### FPM application served by Apache
* Faster than FastCGI due to persistent parent-PHP processes
* Nginx proxies the PHP requests to Apache
* Ideal for high-traffic sites

### FPM application served by nginx
* Same benefits as above
* NGINX handles PHP directly (faster in some setups)

### Dedicated FPM (Apache or nginx)
* One PHP process pool per domain
* Best for busy or resource-intensive domains
* Slightly more memory usage

!!!! By default, both FastCGI and FPM handlers are available and enabled on your Plesk server.


## How to change the PHP Version

![change%20php%20version](change%20php%20version.png "change%20php%20version")