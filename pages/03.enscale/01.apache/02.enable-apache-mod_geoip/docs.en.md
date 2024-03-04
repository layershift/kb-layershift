---
title: 'Enable Apache mod_geoip'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'On Enscale PaaS, you can benefit from custom Apache modules, including mod_geoip. Learn how to add it to your Apache server.'
metadata:
    description: 'On Enscale PaaS, you can benefit from custom Apache modules, including mod_geoip. Learn how to add it to your Apache server.'
    'og:url': 'https://www.layershift.com/kb/enscale/apache/enable-apache-mod_geoip'
    'og:type': website
    'og:title': 'Enable Apache mod_geoip | Layershift KB'
    'og:description': 'On Enscale PaaS, you can benefit from custom Apache modules, including mod_geoip. Learn how to add it to your Apache server.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-03T03:28:03+00:00'
    'article:modified_time': '2024-03-03T03:28:03+00:00'
    'article:author': Layershift
---

Mod_geoip can be used to perform redirection based on country location. Installing it will allow you to block or redirect traffic based on the geographical location of the client using their IP address. You can also read the geoIP result inside your PHP scripts (or output into JS) to perform application logic.

With Enscale, you can add this module to your Apache server. There is also the possibility to upload your own GeoIP.dat file. The module can be added to new environments only and it is disabled by default, but it can be enabled really easy by following these simple steps:

* Log in to your [Enscale dashboard](https://app.enscale.cloud/).
* Click **Config** on the Application Node:
 
![Enable%20Apache%20mod_geoip-1](Enable%20Apache%20mod_geoip-1.png "Enable%20Apache%20mod_geoip-1")

* Access the **conf.modules.d/** directory and search for `10-geoip.conf` and click on it:

* Once there, activate **mod_geoip** by uncommenting the LoadModule line:

![Enable%20Apache%20mod_geoip-2](Enable%20Apache%20mod_geoip-2.png "Enable%20Apache%20mod_geoip-2")

* Finally, restart Apache to implement the config changes, and you’re ready to start using the mod_geoip Apache module:

![Enable%20Apache%20mod_geoip-3](Enable%20Apache%20mod_geoip-3.png "Enable%20Apache%20mod_geoip-3")

The module looks at the incoming IP address and sets some variables which provide geolocation information for that IP. The variables it set depend on the specific GeoIP database being used (Country, City, ISP, etc.).

You can use these variables inside .htaccess / httpd.conf files, or even read them in your PHP scripts to perform some appropriate application logic. Let’s look at some examples:

#### Example 1: Blocking Countries

If you have problems with spam requests from certain locations which wouldn’t normally have any legitimate interest, you could potentially block them from your site like this. It’s up to you to decide the relative merits – we’re just presenting technical possibilities.

In your .htaccess or httpd.conf you can add:

!!! * <DirectoryMatch “^/var/www/webroot/ROOT/.*/html”>
!!! * SetEnvIf GEOIP_COUNTRY_CODE RU BlockCountry
!!! * SetEnvIf GEOIP_COUNTRY_CODE CN BlockCountry
!!! * SetEnvIf GEOIP_COUNTRY_CODE UA BlockCountry
!!! * Deny from env=BlockCountry
!!! * </DirectoryMatch>

The country codes are in 2 character **ISO 3166-1** format.

This would block requests from Russia, China, and Ukraine where the code is a ***.html** file located in **/var/www/webroot/ROOT**.

#### Example 2: Allow Countries

You can take the opposite approach, and only allow requests from certain countries.

In your **.htaccess** or **httpd.conf** you can add:

!!! * <Directory “/var/www/webroot/ROOT”>
!!! * SetEnvIf GEOIP_COUNTRY_CODE GB AllowCountry
!!! * SetEnvIf GEOIP_COUNTRY_CODE US AllowCountry
!!! * Deny from all
!!! * Allow from env=AllowCountry
!!! * </Directory>

This would allow requests from the **UK** (note: GB is the **ISO-3166-1** code) and **USA**. Requests from all other locations would be blocked.

#### Example 3: Conditional Redirect

!!! * RewriteEngine on
!!! * RewriteCond %{ENV:GEOIP_COUNTRY_CODE} ^GB$
!!! * RewriteRule ^(.*)$ http://www.for-uk-only.co.uk$1 [R,L]

This will redirect UK visitors to www.for-uk-only.co.uk and not do anything to requests made from other IP addresses.

#### Example 4: Using the GeoIP result in PHP

You may have noticed in the above examples we are simply reading environment variables. Of course, you can do that directly in **PHP** as well in the **$_SERVER superglobal**:

!!! echo $_SERVER['GEOIP_COUNTRY_CODE'];

#### Important Notes

If your Apache server does not have a public IP (or if you’re using the load balancer feature), your requests are proxied and you must configure **mod_geoip** to read the **X-Forwarded-For** header. Just add the following to **conf.d/geoip.conf**:

!!! GeoIPScanProxyHeaders On

**Additional Note:** Restart Apache afterwards for the configuration change to take effect).

The accuracy of mod_geoip depends on the GeoIP.dat database, and due to ISP routing is never 100%. You should use mod_geoip to assist your visitors, but always consider that it might sometimes be wrong.

You can update the GeoIP.dat database with another at any time – just upload the new database file via the dashboard.