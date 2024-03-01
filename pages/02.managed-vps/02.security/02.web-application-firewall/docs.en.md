---
title: 'Web Application Firewall (WAF)'
visible: true
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'Comparison of Atomic Basic ModSecurity (free) vs. Atomic Advanced ModSecurity Rules (Security Core Complete add-on) for Plesk Web Application Firewall'
metadata:
    description: 'Comparison of Atomic Basic ModSecurity (free) vs. Atomic Advanced ModSecurity Rules (Security Core Complete add-on) for Plesk Web Application Firewall'
    'og:url': 'https://www.layershift.com/kb/managed-vps/security/web-application-firewall'
    'og:type': website
    'og:title': 'Web Application Firewall (WAF) | Layershift KB'
    'og:description': 'Comparison of Atomic Basic ModSecurity (free) vs. Atomic Advanced ModSecurity Rules (Security Core Complete add-on) for Plesk Web Application Firewall'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-01T13:26:39+00:00'
    'article:modified_time': '2024-03-01T13:26:39+00:00'
    'article:author': Layershift
---

In addition to [filtering traffic by IP address](../firewall), Plesk provides an integrated Web Application Firewall (WAF) feature via Apache mod_security. 

! Requests served only by Nginx (e.g. via *Serve static files directly by nginx* or *Process PHP by nginx* options) cannot be filtered by the WAF

Rather than simply looking at the IP address originating a request to your server, a WAF analyses each HTTP/HTTPS request for potentially malicious patterns. For example, querystring parameters shouldn't usually contain things that look like an SQL injection attack, so if a WAF spots a request of that form it can block it for you.

# How to enable

The WAF is an advanced feature, so it's turned off by default to avoid potentially blocking legitimate traffic (see below).

It can be enabled, server-wide, via Plesk under Tools & Settings > Security > Web Application Firewall (ModSecurity).

There are 3 modes:
* Off (default)
* Detection only - bad requests are logged but not blocked; useful to evaluate potential service impact from activating a WAF rule set
* On - bad requests are blocked

## Per domain

After enabling server-wide, a *Web Application Firewall* option is added to each domain within Plesk. Here, you can set the desired WAF mode for the domain, view related logs, and configure exceptions.

!! The per domain WAF mode cannot be more restrictive than the server-wide mode (e.g. if server-wide is *detection only*, per domain may be *off* or *detection only*, but cannot be *on*).

# WAF Rule sets

As you might imagine, crafting WAF rules in such a way that blocks malicious requests but otherwise stays out of your way and lets legitimate traffic flow freely is a difficult and time consuming task.

Although you can [define a custom rule set](https://www.modsecurity.org/CRS/Documentation/making.html) if you wish, it's not recommended - the rules need to be carefully crafted and refined on an ongoing basis: think of it like anti-virus signatures for web requests.

Instead, there are various (free and commercial) rule sets available to you. The 2 most popular options are both provided by Atomic; their free and paid options are compared below:



|     | Basic ModSecurity   | Advanced ModSecurity Rules
----- | :-----------------: | :-------------------------:
**Price** | **Free** | **£9.99 / $14.99 per month**
**Vulnerability** |||
SQL injection | [color=#3ab31c][fa=check /][/color] | [color=#3ab31c][fa=check /][/color]
Cross-site scripting (XSS) | [color=#3ab31c][fa=check /][/color] | [color=#3ab31c][fa=check /][/color]
Remote file inclusion (RFI) | [color=#3ab31c][fa=check /][/color] | [color=#3ab31c][fa=check /][/color]
Local file inclusion (LFI) | [color=#3ab31c][fa=check /][/color] | [color=#3ab31c][fa=check /][/color]
Command injection | [color=#3ab31c][fa=check /][/color] | [color=#3ab31c][fa=check /][/color]
Virtual patching | Limited | [color=#3ab31c][fa=check /][/color]
**Malware** |||
Advanced protection for WordPress, Joomla, Drupal, and Magento | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Malicious website code suppression | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Web shell blocking | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Brute force protection | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
PCI-DSS compliance | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Data loss protection | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
**Bot protection** |||
Malicious bots | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Comment form spam | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
**False positives** |||
Advanced false positive prevention | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Real time correction to false positive rules | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Search engine spider whitelist | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Anti-evasion protection | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Manual override (whitelisting) | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
**Updates** |||
Real time blacklists | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Crowd sourced threat intelligence | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]
Rules updated multiple times per day | [color=#c10000][fa=times /][/color] | [color=#3ab31c][fa=check /][/color]