---
title: 'Setting up DNS for your domains'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/domains/dns/setting-up-dns-for-your-domains'
    'og:type': website
    'og:title': 'Setting up DNS for your domains |  Layershift KB'
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Setting up DNS for your domains |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'article:published_time': '2023-08-22T16:02:28+01:00'
    'article:modified_time': '2023-08-22T16:02:28+01:00'
    'article:author': Layershift
---

In order to point a domain name at a server, it is necessary to use some nameservers. These point at DNS servers which act like address books for the internet which tell visitors to your website which server your domain name is hosted on. Every domain name uses nameservers, as this is the only way visitors can access a website. To point domain names at your VPS hosting subscription we offer several options:

## Using pre-configured DNS servers (strongly recommended)

Your VPS is pre-installed with a DNS (Domain Name Service) server which allows you to run your own DNS service. This is tightly integrated with Parallels Plesk Control Panel which means that any domain name you add to Plesk will automatically update the associated record in the DNS server. Further, when adding/removing custom sub-domains or enabling services like mailing lists, these are also automatically updated on your DNS server within a matter of seconds without any further manual work required.

For all new VPS’s we configure some default DNS servers based on the server name you chose when ordering. These nameservers are setup automatically when your VPS is being created and can be found in your welcome email. You are not required to perform any additional configuration to get these up and running except updating your domains to use these nameservers at your domain registrar. We will fully maintain these nameservers if there are any changes required.

Your DNS servers will be automatically created in this format:

* **ns1.your-vps-hostname.com**

* **ns2.your-vps.hostname.com**

## Advanced DNS options

We offer a number of advanced DNS options with varying levels of included management and support (please see our ‘Scope of DNS Management’ section below before making your choice).

### Private nameservers

This also uses the integrated DNS server, but allows you to add branding to the nameservers. You are responsible for keeping the IP address used by these nameservers updated.

#### Register your nameservers with your domain registrar

##### **If you have a domain name registered with us**:

It is recommended that you use a .com/net/org domain name for this if possible. If you have such a domain, you should contact our support team and we can register nameservers for you at the domain registry (any changes you require will need to be 	requested in future, we will not automatically maintain these nameservers for you). You will need to let us know the nameserver addresses you want (for example, ns1.yourdomain.com and ns2.yourdomain.com – don’t forget to tell us which domain to 	use! We recommend you to have 2 nameservers as this is required by some domain registries.)

If you do not have such a domain name, we recommend using pre-configured DNS servers as above.

##### **If you do not have a domain name registered with us**:

There are two options here:
	
1. You can create custom nameservers using the domain control panel of your current domain registrar. You will need to provide your domain registrar with 1 or 2 IP addresses from your VPS subscription. These can be found by logging in to Layershift Customer Control Panel and clicking on the ‘System’ tab then opening the ‘Server Info’ page. As the exact process varies between domain registrars, the exact method for registering nameservers should be checked with your domain registrar support team or in their documentation or FAQ.

2. We can provide you with custom nameservers using a whitelabel domain name – simply let us know and we can set this up for you.

You then simply need to add domain names into Parallels Plesk Control Panel and they will automatically be added to your DNS servers. Don’t forget to point all of your domain names at your new nameservers when they have been setup. For all domains registered with us, you can do this using the following method:

* Login to `Layershift Customer Control Panel` and open the **Home** tab.
* In the `Domain Management` section open  **All My Domains**.
* Click on the domain name you wish to update.
* Open the `Name Servers` sub-tab.
* Click `Edit`.
* Set the `Custom Name Servers` you require.
* Click `Save`.
* Repeat from step 3 if you have other domains to configure.

#### Modify the default DNS template in Plesk

To ensure that all visitors can access your websites, it is important to update the DNS zone template in Plesk. This is when creating domain names to create a default, ready-to-use DNS zone for each domain.

* Login to `Parallels Plesk Control Panel`.
* Click **Tools & Settings** on the left-menu.
* On the `General Settings` submenu, click **DNS Template Settings** in the main window.
* You will see a line with `NS` in the `Record Type` column – tick the box next to this and click **Remove** at the top.
* Click **Add DNS Record** and enter the following information in the box that appears:
	1. **Record Type** = < NS >
	2. **Domain Name** = < leave empty >
    3. **Name server** = < enter your first nameserver, for example ns1.yourdomain.com. This must match the nameservers you registered above exactly >
* Repeat step 5 to add your second nameserver (for example ns2.yourdomain.com)
* Remove any other NS records already added to your VPS, as they will cause problems if you are using this DNS server method instead
    
Note that this will not update any domains which already exist, it will only be used for new domains. If you already have domains created, you should perform the following steps to ensure the DNS zones for the domains are updated to use the correct nameservers:
    
##### Plesk in `Service Provider` mode:

* Login to `Parallels Plesk Control Panel`.
* Click **Domains** on the left-menu.
* Click ‘Manage hosting’ on the right side of the screen for the domain you want to check.
* Open `Websites and Domains` tab.
* Go to `DNS Settings` section.
* Click `Manage` on the right of the domain name you want to update.
* Click `Restore Defaults` (recommended) or manually make the required changes.
    
##### Plesk in `Power User` mode:
    
* Login to `Parallels Plesk Control Panel`.
* Click `Webspaces` on the top menu.
* Select your domain name.
* Click **Switch to webspace**.
* Go to **Websites and domains** tab on the top menu.
* Go to **DNS Settings**
* Click **Restore Defaults** (recommended) or manually make the required changes

### Use our redundant DNS cluster

You can use our DNS cluster and point hosted domains nameservers towards our redundant nameservers located on multiple servers in multiple countries. These servers are highly reliable, but the downside is that this option requires you to manually add domains to our DNS servers in two places – in Parallels Plesk Control Panel, and in [Layershift Customer Control Panel](https://control.layershift.com/cp/).

To use these you need to add a domain in Parallels Plesk Control Panel in the normal way. Once this is done, you should check the IP address your domain is hosted on (by clicking on your domain in Plesk, you should see this on the first screen). You need to make a note of this and do the following:

* Login to [Layershift Customer Control Panel](https://control.layershift.com/cp/)
* In the  `Domain Management ` section click  **All My Domains**.
* Click **Add Domain**
* Complete the form to add your domain and click `Save`.
* Click on the domain name you have just added.
* Open the **DNS Zone** tab.
* Click **New Record** and add the DNS record you require.
* Repeat from step 7 if you have other records to configure.

All of these domain names then need to be configured at your domain registrar to point at our DNS servers (it is recommended to use all three where possible, but this is not mandatory):

* DNS1.TRANSNEXIS.NET
* DNS2.TRANSNEXIS.NET
* DNS3.TRANSNEXIS.NET

For all domains registered with us, you can do this using the following method:

* Login to [Layershift Customer Control Panel](https://control.layershift.com/cp/)
* In the  `Domain Management ` section click  **All My Domains**.
* Click on the domain name you wish to update.
* Open the **Name Servers** sub-tab.
* Click `Edit`.
* Click `Use Provider’s Name Servers set`.
* Click `Save`.
* Repeat from step 3 if you have other domains to configure.

Please keep in mind that all DNS zones will be managed only via the main control panel and the default Plesk DNS template will be ignored.

### Use external DNS servers

Many domain registrars offer an external DNS service which you can use, but in many cases these are unreliable and we do not recommend these are used. If you still wish to proceed with this option you will need to determine the IP address your domain is configured to use on our servers, and provide this to your DNS provider to point your domain name at our servers. Any changes you make to your domain inside Parallels Plesk Control Panel, such as adding sub-domains or enabling mailing lists, will need to be configured manually by you or your DNS provider in their systems.

##### **To determine which IP address your website is using in Plesk `Service Provider` mode**:

* Login to `Parallels Plesk Control Panel`.
* Click `Domains` on the left-menu.
* Click on your domain name.
* You will see the **IP address** displayed on the page in the Hosting section.
* To view an example of **DNS records** you could use to configure the DNS server in your DNS provider’s control panel you can:
* Click **Domains** on the left-menu:
	1. Click **Manage hosting** on the right side of the screen for the domain you want to check.
	2. Open **Websites and Domains** tab
	3. Go to **DNS Settings** section.

##### **To determine which IP address your website is using in Plesk ‘Power User’ mode**:

* Login to Parallels Plesk Control Panel.
* Click `Webspaces` on the top menu.
* Select your domain name.
* Click `Switch to webspace`.
* You will see the IP address displayed in the **System Overview** section.
* To view an example of DNS records you could use to configure the DNS server in your DNS provider’s control panel you can:
	1. 	Access `Websites and domains` tab on the top menu.
	2. 	Click on `DNS settings`.

## Scope of DNS management

We support a wide range of DNS management options with varying levels of support.

Of course our friendly support team are available 24×7 to advise you on which DNS records to create even for DNS services hosted elsewhere.

Situation | Responsibility for changes | Point of support
-----------  | ----------------------------------- | ---------------------               
Pre-configured DNS servers (e.g. ns1/ns2.vpshostname.com) | Layershift | Layershift
Layershift redundant DNS cluster (dns1/2/3.transnexis.net) | Layershift | Layershift
Private nameservers on domains registered with Layershift (ns1/ns2.yourdomain.com) | Customer | Layershift
Private nameservers on domains registered elsewhere (ns1/ns2.yourdomain.com) | Customer | Your domain registrar
External DNS servers (ns1/ns2.dnsprovider.com) | Customer | Your DNS provider
 
 **Additional Note 1:** We will fully manage your DNS servers including updates if you change IP address or request migrations of your services between our datacentres except where “responsibility for changes” is shown as Customer. In such cases you are responsible for requesting changes, even if your domain is registered via Layershift.

**Additional Note 2:** Using our pre-configured DNS servers are strongly recommended so we can fully manage this aspect of your hosting service.





   
    







