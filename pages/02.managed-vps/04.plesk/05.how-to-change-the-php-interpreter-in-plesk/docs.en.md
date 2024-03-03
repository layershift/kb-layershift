---
title: 'How to change PHP interpreter in Plesk'
aura:
    pagetype: website
    description: 'Find out how to change PHP version and PHP interpreter in Plesk. Step by step guide.'
metadata:
    description: 'Find out how to change PHP version and PHP interpreter in Plesk. Step by step guide.'
    'og:url': 'https://www.layershift.com/kb/managed-vps/plesk/how-to-change-the-php-interpreter-in-plesk'
    'og:type': website
    'og:title': 'How to change PHP interpreter in Plesk | Layershift KB'
    'og:description': 'Find out how to change PHP version and PHP interpreter in Plesk. Step by step guide.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-03T00:14:50+00:00'
    'article:modified_time': '2024-03-03T00:14:50+00:00'
    'article:author': Layershift
taxonomy:
    category:
        - docs
menu: 'Change PHP Version'
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


