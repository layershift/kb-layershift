---
title: 'How to check the PHP versions available on your server'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/cloud-vps/plesk/how-to-check-the-php-versions-available-on-your-server'
    'og:type': website
    'og:title': 'How to check the PHP versions available on your server |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/02.cloud-vps/04.plesk/09.how-to-check-the-php-versions-available-on-your-server/How to check the PHP versions available on your server-1.png'
    'og:image:type': image/png
    'og:image:width': 1172
    'og:image:height': 550
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'How to check the PHP versions available on your server |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/02.cloud-vps/04.plesk/09.how-to-check-the-php-versions-available-on-your-server/How to check the PHP versions available on your server-1.png'
    'article:published_time': '2023-12-03T15:36:57+00:00'
    'article:modified_time': '2023-12-03T15:36:57+00:00'
    'article:author': Layershift
media_order: 'How to check the PHP versions available on your server-1.png,How to check the PHP versions available on your server-2.png'
---

Not sure which OS and PHP version your VPS is running on? This KB article will show you how to check the OS installed on your server and how to run other PHP versions in parallel with the standard version.

### Identify your OS version

* Login to the [Layershift Customer Control Panel](https://control.layershift.com)
* Go to the **System** section of the main top menu
* Click on **Server Info**
* Under the **General Info** section you’ll see which **CentOS** version is installed on your server, as in the following example:

### Check the PHP versions available for your OS

### CentOS 7

| PHP Version | mod_php Handler | php-fpm Handler | fastCGI Handler | Updated until 
------------------  | -----------------------  | ---------------------- | ---------------------  | -----------------
|      PHP 5.3       |     No    |     No    |   No  | March 2023 |
|      PHP 5.4       |    Yes   |   Yes   |   Yes  |  Jun 2024*   |
|      PHP 5.5       |    No    |   Yes   |   Yes  |  Jun 2016**   |
|      PHP 5.6       |    No    |   Yes   |   Yes  |   Dec 2018  | 
|      PHP 7          |   No     |   Yes   |   Yes  |  Nov 18       |

!!! PHP 5.4 on CentOS 7 is a special long-term support release which is fully supported and regularly updated with security and bug fixes backported from newer versions of PHP.

!!! If you are using PHP 5.5, we strongly recommend changing to PHP 5.4 to benefit from the long-term support. PHP versions that reached the end of life will remain available to existing websites, but security/bug fixes will no longer be applied.

### CentOS 6

| PHP Version | mod_php Handler | php-fpm Handler | fastCGI Handler | Updated until 
------------------  | -----------------------  | ---------------------- | ---------------------  | -----------------
|      PHP 5.3       |     No    |     No    |   No  | Nov 2020 |
|      PHP 5.4       |    No   |   Yes   |   Yes  |  Sep 2015*   |
|      PHP 5.5       |    No    |   Yes   |   Yes  |  Jun 2016**   |
|      PHP 5.6       |    No    |   Yes   |   Yes  |   Dec 2018  | 
|      PHP 7          |   No     |   Yes   |   Yes  |  Nov 18       |

!!! PHP 5.3 on CentOS 6 is a special long-term support release which is fully supported and regularly updated with security and bug fixes backported from newer versions of PHP.

!!! If you are using PHP 5.4 or PHP 5.5, we strongly recommend changing to PHP 5.3 to benefit from the long-term support. PHP versions that reached the end of life will remain available to existing websites, but security/bug fixes will no longer be applied.

### CentOS 5

| PHP Version | mod_php Handler | php-fpm Handler | fastCGI Handler | Updated until 
------------------  | -----------------------  | ---------------------- | ---------------------  | -----------------
|      PHP 5.3       |     Yes    |     Yes    |   Yes  | Mar 2017* |
|      PHP 5.4       |    No   |   No   |   Yes  |  Sep 2015**   |
|      PHP 5.5       |    No    |   No   |   Yes  |  Jun 2016**   |
|      PHP 5.6       |    No    |   No   |   Yes  |   Dec 2018  | 

!!! PHP 5.3 on CentOS 5 is a special long-term support release which is fully supported and regularly updated with security and bug fixes backported from newer versions of PHP.

!!! If you are using PHP 5.4 or PHP 5.5, we strongly recommend changing to PHP 5.3 to benefit from the long-term support. PHP versions that reached the end of life will remain available to existing websites, but security/bug fixes will no longer be applied.

!! For those customers running a version of PHP not labelled as recommended above, we will routinely install the latest minor version (e.g. 5.5.x, 5.6.x) on our Cloud VPS range, so for stability and to minimise the risk of needing to modify your code we recommend using PHP 5.3 (CentOS 5/6) or 5.4 (CentOS 7) wherever possible (where patches are back-ported for stability), and only using newer versions when you’re an active developer or need the newest functionality.

#### How to check the PHP version used by a domain

If you are not sure which PHP version is installed by default on your server, please see below for instructions:

* Login to your **Plesk Dashboard**
* Go to **Tools and settings** in the main top menu
* Go to **Server Management**
* Click **Server Components**
* Search for `php` in the search box:

![How%20to%20check%20the%20PHP%20versions%20available%20on%20your%20server-1](How%20to%20check%20the%20PHP%20versions%20available%20on%20your%20server-1.png "How%20to%20check%20the%20PHP%20versions%20available%20on%20your%20server-1")

If you also want to see the additional PHP versions you’ve installed so far:

* Go to **Websites & Domains**
* Click on the domain name you want to check
* Select **PHP**

![How%20to%20check%20the%20PHP%20versions%20available%20on%20your%20server-2](How%20to%20check%20the%20PHP%20versions%20available%20on%20your%20server-2.png "How%20to%20check%20the%20PHP%20versions%20available%20on%20your%20server-2")

Now that you know the CentOS version of your VPS, here are some technical specifications depending on each Operating System installed on your server.

For more detailed instructions on how to install additional PHP versions please refer to the [Installing PHP 5.4 5.5, 5.6 or 7](/installing-php-plesk) article.

!!! mod_php and php-fpm handlers are only available for the PHP version installed by default. For all other additional PHP versions you add to your server, you will only be able to execute PHP scripts using FastCGI or CGI.

In case you’re not certain of the differences between mod_php, FastCGI or CGI, don’t worry. We’ve got this covered! Check out our [Which PHP mode? Apache vs CGI vs FastCGI](http://blog.layershift.com/which-php-mode-apache-vs-cgi-vs-fastcgi/) blog article and find out the advantages and disadvantages of using a particular PHP handler.