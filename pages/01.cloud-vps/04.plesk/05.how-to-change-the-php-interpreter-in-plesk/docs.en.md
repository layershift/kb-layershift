---
title: 'How to change PHP interpreter in Plesk'
media_order: 'How to change PHP version and PHP interpreter in Plesk-1.png,How to change PHP interpreter in Plesk-2.png'
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/cloud-vps/plesk/how-to-change-php-version-and-php-interpreter-in-plesk'
    'og:type': website
    'og:title': 'How to change PHP interpreter in Plesk |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/01.cloud-vps/04.plesk/06.how-to-change-php-version-and-php-interpreter-in-plesk/How to change PHP version and PHP interpreter in Plesk-1.png'
    'og:image:type': image/png
    'og:image:width': 1463
    'og:image:height': 553
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'How to change PHP interpreter in Plesk |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/01.cloud-vps/04.plesk/06.how-to-change-php-version-and-php-interpreter-in-plesk/How to change PHP version and PHP interpreter in Plesk-1.png'
    'article:published_time': '2023-08-27T17:25:07+01:00'
    'article:modified_time': '2023-08-27T17:25:07+01:00'
    'article:author': Layershift
---

# How to change PHP interpreter in Plesk

In Plesk 18.0.54, you have the flexibility to easily modify PHP interpreter without experiencing any server or domain downtime. This feature can be particularly advantageous for enhancing website performance or switching to your preferred PHP interpreter, if you have one in mind! When PHP operates, it creates new files and writes to existing ones using the user it runs as.

However, it's important to note that switching between PHP modes may result in changes to file permissions. Previously writable files may no longer be writable, or vice versa. If you encounter this situation, you may need to adjust file permissions or seek assistance from support to modify file ownership, especially when switching PHP mode for an existing website.

**Additional Note:** If the file permissions on the domain are incorrect, altering this setting may cause unexpected behaviour. Please contact our support team if you’d like further guidance.

Below are step-by-step instructions guiding you on how to change the PHP handler directly from within the Plesk Control Panel:

* From your Plesk Dashboard, scroll down to your desired domain and click on `Hosting Settings`:

![How%20to%20change%20PHP%20version%20and%20PHP%20interpreter%20in%20Plesk-1](How%20to%20change%20PHP%20version%20and%20PHP%20interpreter%20in%20Plesk-1.png "How%20to%20change%20PHP%20version%20and%20PHP%20interpreter%20in%20Plesk-1")

* Navigate to the section labeled **Web Scripting** and choose your preferred PHP interpreter:

![How%20to%20change%20PHP%20interpreter%20in%20Plesk-2](How%20to%20change%20PHP%20interpreter%20in%20Plesk-2.png "How%20to%20change%20PHP%20interpreter%20in%20Plesk-2")

* Finally, to apply the changes you have made, please click on the `Ok` button.


