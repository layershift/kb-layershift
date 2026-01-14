---
title: 'Transferring a gTLD to Layershift'
aura:
    pagetype: website
    description: 'Transferring a gTLD to Layershift.'
metadata:
    description: 'Transferring a gTLD to Layershift.'
    'og:url': 'https://www.layershift.com/kb/domains/transfers/transferring-a-gtld-to-layershift'
    'og:type': website
    'og:title': 'Transferring a gTLD to Layershift | Layershift KB'
    'og:description': 'Transferring a gTLD to Layershift.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2025-07-24T16:14:56+01:00'
    'article:modified_time': '2025-07-24T16:14:56+01:00'
    'article:author': Layershift
menu: 'gTLD to Layershift'
taxonomy:
    category:
        - docs
---

Layershift currently support the registration or transfer of the following domain names:

* .com
* .org
* .net
* .info
* .biz
* .us
* .eu
* .ca
* .mobi
* .me
* .in
* .co
* .asia
* .io
* .cool
* .guru
* .ninja
* .rocks

For .uk domain transfers please see the related article: Transferring a .uk domain name to Layershift

Any of these domains can be transferred to your account with Layershift free-of-charge. However, ICANN rules require that the domain is renewed for 1 year as part of the transfer process. So you will need to pay an early renewal fee, which will basically extend the domain registration by 1 year.

### What you need to do at the current provider side

* Obtain EPP transfer code from your existing registrar.
The EPP code or Domain Authorization Code is usually a (up to) 16 characters code assigned by the registrar in order to provide an extra security measure. This code ensures that a domain can only be transferred by the domain owner and not by a malicious third party. You will not be able to continue with a domain transfer until you receive the Authorization Code from your current registrar.

* Ensure that any transfer locks at your registrar are removed/unlocked.
In most of the cases, the registrars lock the domains automatically to protect them from unauthorized transfers. You need to contact your current registrar or use your registrar’s domain management tools to unlock your domain before you initiate the transfer, otherwise the transfer will fail.

### What you need to do on Layershift side:

Once you’ve made sure that you have successfully completed all the steps mentioned above, please follow these guidelines to complete the transfer process:

1.Go to our website to initiate the transfer: [UK-hosted subscriptions](https://buy.layershift.com/uk/domains.php) (paid in GBP) **or** [US or Singapore-hosted subscriptions](https://buy.layershift.com/us/domains.php) (those paid in USD)
2.You will need to switch to **Transfer Domains Mode**, fill in the domain(s) you wish to transfer then follow the wizard to place the order and submit the payment.
3.Select the desired DNS records in the Step 3 of the transfer order. The nameservers you enter in this step will only be set **after** the transfer is completed.

##### Layershift DNS cluster:

In this case you have to choose the first option – `Manage DNS via My Layershift’s default name servers`:

* DNS1.TRANSNEXIS.NET
* DNS2.TRANSNEXIS.NET
* DNS3.TRANSNEXIS.NET

![Transferring%20a%20gTLD%20to%20Layershift-1](Transferring%20a%20gTLD%20to%20Layershift-1.png "Transferring%20a%20gTLD%20to%20Layershift-1")

##### Custom nameservers

If you wish to keep your existing DNS records or add other custom ones, select the `Enter custom name servers` option and fill in the NS records manually.

![Transferring%20a%20gTLD%20to%20Layershift-2](Transferring%20a%20gTLD%20to%20Layershift-2.png "Transferring%20a%20gTLD%20to%20Layershift-2")

**Additional Note:** You can check the nameservers using an online whois check tool (e.g.this Whois Lookup), but please note that it may include cached information.

4.After placing the order, a transfer request is submitted to your existing registrar which they need to respond to that request (i.e. either releasing the domain or rejecting it) within 5 days.

The whole transfer process for a domain transfer can take anything from a few hours to around 5 days. This varies depending on the (losing) registrar involved.

There is no downtime for your domains during this process, because nameservers settings should remain unchanged throughout.

##### Check your domain nameservers are accurate

Your domain name will be using the nameservers you entered during the transfer order. If you wish to update these details you can do this via our Layershift control panel:

1. Login to [Layershift Customer Control Panel](https://control.layershift.com/) .
2. Use the drop-down `Subscription` on the right corner of the screen and select `All My Domains`.
3. Open `All My Domains` tab.
4. Click on the domain name you have just transferred (or any other domain you want to change nameservers on).
5. Open the `Name Servers` tab.
6. Click `Edit` and enter the nameservers required. You have three choices:
	* Custom **Nameservers** (recommended for Cloud VPS and Dedicated customers)
	* Our redundant **DNS cluster** (recommended for shared hosting)
	* External **DNS servers** (not recommended).
    For a full explanation on the nameservers options, please check our related article: [Setting up DNS for your domains](../../dns/setting-up-dns-for-your-domains)
    **
Additional Note:** _Repeat from step 3 if you have multiple domains._

Our systems will immediately send a request to the domain name registry to update your nameservers, and this is usually completed within 5 minutes. You may need to wait for your ISP or your computer to expire their DNS cache (this occurs automatically) before you can see your domain name pointing at our servers, but usually this does not take more than a few hours.

