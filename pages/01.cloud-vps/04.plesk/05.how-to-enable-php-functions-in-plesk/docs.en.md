---
title: 'How to enable PHP functions in Plesk'
media_order: 'How to enable PHP functions in Plesk-1.png,How to enable PHP functions in Plesk-2.png'
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/cloud-vps/plesk/how-to-enable-php-functions-in-plesk'
    'og:type': website
    'og:title': 'How to enable PHP functions in Plesk |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/01.cloud-vps/04.plesk/05.how-to-enable-php-functions-in-plesk/How to enable PHP functions in Plesk-1.png'
    'og:image:type': image/png
    'og:image:width': 1461
    'og:image:height': 788
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'How to enable PHP functions in Plesk |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/01.cloud-vps/04.plesk/05.how-to-enable-php-functions-in-plesk/How to enable PHP functions in Plesk-1.png'
    'article:published_time': '2023-08-27T17:14:40+01:00'
    'article:modified_time': '2023-08-27T17:17:32+01:00'
    'article:author': Layershift
taxonomy:
    category:
        - docs
---

# How to enable PHP functions in Plesk

As a security best practice, we disable several core PHP functions by default on our servers that are often used for malicious purposes and rarely required by legitimate code.

As part of our layered security model we try to take every possible precaution to prevent your server from being attacked. The advanced network-level attack mitigation policies we have in place at various levels of our infrastructure mitigate many types of attacks before they reach your server. We perform regular security updates for the OS and pre-installed software. We also offer non-stop kernel updates with patches implemented within hours to ensure your service is protected. Furthermore, we closely monitor all our services to try to stop attacks and ensure that we can pro-actively resolve any issues without any service disruption. In addition to this, we preventively block or disable high risk features/services which might lead to security issues.

Despite all the security measures we take, we cannot always prevent hackers from exploiting application vulnerabilities. By having some core PHP functions disabled, in the unfortunate event that a hacker manages to execute an unauthorised code on your website, the damage they can cause to your server is substantially reduced.

These are the core PHP functions that we disable by default:

* exec 
* passthru
* system
* pcntl_exec
* proc_open
* shell_exec

We recognise that some PHP based CLI tools for certain frameworks may legitimately require the use of these functions. Using these functions does not imply that a script is inherently malicious or designed in an insecure way; they are simply functions that can perform powerful operations.

We strongly recommend to only enable functions from this high risk list strictly for the type of scripts that require them (CLI or HTTP). This will minimise the security risk to your server.

### Enable PHP functions for CLI scripts

The most flexible and recommended option is to override the disable_functions setting when calling the PHP CLI. For example:

`php -d disable_functions='' your-script.php`

This will enable all functions for that particular script execution only.

If for some reason you need to make that the default behaviour for CLI scripts, it must be set globally for your server by our technical support team. Please include a list of the needed functions and specify that you need them for a CLI script in your support request.

By only enabling these potentially harmful functions for CLI, you retain protection against malicious scripts that an attacker may try to execute via HTTP (e.g. after uploading them to your site disguised as an image or a similar common application vulnerability).

### Enable PHP functions for HTTP scripts

If you have HTTP scripts that require certain functions, you can enable these from your Plesk Control Panel on a per site basis by following the steps below:

* Access your `Plesk Dashboard`, click `Websites & Domains` and navigate to the domain you would like to enable the functions for.
* Click on `PHP`:

![How%20to%20enable%20PHP%20functions%20in%20Plesk-1](How%20to%20enable%20PHP%20functions%20in%20Plesk-1.png "How%20to%20enable%20PHP%20functions%20in%20Plesk-1")

* Remove the function(s) you would like to enable from the `disable_functions` list.

![How%20to%20enable%20PHP%20functions%20in%20Plesk-2](How%20to%20enable%20PHP%20functions%20in%20Plesk-2.png "How%20to%20enable%20PHP%20functions%20in%20Plesk-2")



