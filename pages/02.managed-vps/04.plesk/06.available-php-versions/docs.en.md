---
title: 'Available PHP versions'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'A guide for installing PHP versions in Plesk and for changing between versions that are already installed in your Plesk Panel.'
metadata:
    description: 'A guide for installing PHP versions in Plesk and for changing between versions that are already installed in your Plesk Panel.'
    'og:url': 'https://www.layershift.com/kb/managed-vps/plesk/available-php-versions'
    'og:type': website
    'og:title': 'Available PHP versions | Layershift KB'
    'og:description': 'A guide for installing PHP versions in Plesk and for changing between versions that are already installed in your Plesk Panel.'
    'og:image': 'https://www.layershift.com/kb/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2026-01-29T16:06:34+00:00'
    'article:modified_time': '2026-01-29T16:06:34+00:00'
    'article:author': Layershift
menu: 'Available PHP versions'
---

##PHP VERSIONS
Modern web applications often require specific PHP versions. 

On a Plesk server, you can choose between using Plesk-provided PHP versions or Alt-PHP (alternative PHP) offered via Imunify360 or CloudLinux.

On our Plesk servers (without CloudLinux or Imunify360), the following PHP versions are installed and available by default:

* PHP 8.5 (latest Today: 29 Jan 2026)
* PHP 8.4 
* PHP 8.3
* PHP 8.2 


!! We strongly advise against using unsupported PHP versions.

!! Domains running outdated PHP will be inherently insecure, and we cannot take responsibility for any vulnerabilities, breaches, or issues caused as a result.

!!!! If you still require legacy PHP for specific use cases, there is a safer alternative through Alt-PHP, which offers hardened versions of old PHP builds.


##What Are Alt-PHP Versions?

Alt-PHP refers to alternative, hardened PHP builds (that we provide) by either CloudLinux or Imunify360. These versions are specifically maintained with backported security patches, meaning you can safely use older PHP versions (like 5.6, 7.0, 7.4, etc.) without compromising on basic security. This makes Alt-PHP a practical solution when legacy application requirements prevent upgrading to the latest supported PHP versions.


##Alt-PHP via CloudLinux vs. Imunify360

###CloudLinux:
Best suited for shared hosting or high-traffic environments
In addition to hardened Alt-PHP versions, CloudLinux includes LVE limits (Lightweight Virtual Environment), which let you cap CPU, RAM, I/O, and process usage per domain. This helps prevent a single poorly behaving website from affecting the performance of the entire server.
Please note: CloudLinux does not apply any LVE limits by default. These need to be manually configured. Since the resource requirements can vary significantly between domains, we recommend that clients define custom limits based on their specific domains' needs and usage patterns.


###Imunify360:

Imunify360 is the upgraded license of the basic ImunifyAV antivirus. It provides additional security, including:
- Advanced DoS and brute-force protection
- A powerful Web Application Firewall (WAF)
- Real-time malware scanning and cleanup
Also includes Alt-PHP support, making it a great choice for customers who prioritise both security and legacy PHP compatibility.

Both options provide access to a wide range of Alt-PHP versions, automatically kept up to date with essential patches by the vendors.

!!!! **Important**: When Alt-PHP is enabled, Plesk’s native PHP versions are automatically disabled. 

If you have any questions about PHP versions, legacy support with alt-PHP versions, or the best setup for your server, our support team is available 24/7 and ready to assist you.
