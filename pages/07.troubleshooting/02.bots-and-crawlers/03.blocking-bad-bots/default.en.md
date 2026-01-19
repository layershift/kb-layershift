---
title: 'Blocking Bad Bots'
aura:
    pagetype: website
metadata:
    'og:url': 'https://www.layershift.com/kb/troubleshooting/bots-and-crawlers/blocking-bad-bots'
    'og:type': website
    'og:title': 'Blocking Bad Bots | Layershift KB'
    'og:image': 'https://www.layershift.com/kb/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2026-01-19T10:48:19+00:00'
    'article:modified_time': '2026-01-19T10:48:19+00:00'
    'article:author': Layershift
---

## Tools you can use:

###  .htaccess and robots.txt: First Line of Defense

`robots.txt` is a public file that well-behaved bots use to determine what they can crawl. However, many bad bots simply ignore it.
```
User-agent: BADBOT
Disallow: /
```
`.htaccess` can be used to block known bad bots more effectively.

```
RewriteEngine On
RewriteCond %{HTTP_USER_AGENT} BAD_BOT_NAME [NC,OR]
RewriteCond %{HTTP_USER_AGENT} ANOTHER_KNOWN_BAD_BOT [NC]
RewriteRule ^.* - [F,L]
```

This `.htaccess` rule above blocks access to your domain for any request where the User-Agent contains "PetalBot" or "AhrefsBot". When either of these bots attempts to access your domain, Apache will respond with a 403 Forbidden HTTP status code, effectively denying them access to all resources.

###  Bad Bot Blocker

The Bad Bot Blocker is a Plesk extension available on our servers that can be installed and activated per domain with just a few clicks. Once enabled, it works by using a large, community-maintained list of known malicious or abusive User-Agents.

This list is regularly updated to keep up with newly discovered bots and crawlers that attempt to overload or scrape websites. The extension configures server-level rules (usually via NGINX) to block these requests before they ever reach your PHP stack, helping reduce CPU, RAM, and bandwidth usage. It's a lightweight yet effective way to cut down on unwanted traffic and protect your hosting environment.

###  BotStopper

**BotStopper**, is built on Anubis, developed by [TechAro](https://anubis.techaro.lol/)

It’s a Plesk extension that Layershift is actively developing in collaboration with the Anubis team, with the goal of rolling it out across all our Plesk systems as bot traffic issues continue to grow.

This extension needs a license that has a small fixed costs which helps continuously support the developers and ongoing maintenance of the project. Licenses can be purchased directly from [https://extensions.layershift.com/](https://extensions.layershift.com/)

Anubis filters traffic **before it reaches your server**, using a detailed ruleset to block or challenge known scrapers, AI data collectors, headless browsers, and legacy clients. 

Some highlights of its **default** behavior:

**Blocked by Default:**
- Requests with the header `CF-Worker: .*`
- Headless browsers like `HeadlessChrome`, `HeadlessChromium`, and automation tools such as `LightPanda`
- A long list of AI-related and scraper User-Agents (e.g. `GPTBot`, `ClaudeBot`, `Amazonbot`, `Anthropic-AI`, `PerplexityBot`, `SemrushBot`, etc.)
- Outdated or suspicious User-Agent strings (e.g. `MSIE`, `Trident`, `Presto`, `Windows 95`, `Alexa Toolbar`)

**Challenged by Default:**
- Clients containing `Windows NT 11.0`, `iPod`
- Generic User-Agents like `Mozilla` or `Opera` that may indicate spoofing

**Allowed by Default:**
- Known good crawlers like `googlebot`, `bingbot`, `duckduckbot`, `internet-archive`, `kagibot`, `mojeekbot`, based on both User-Agent and IP
- Important crawler URLs such as `/robots.txt`, `/favicon.ico`, `/sitemap.xml`, and `/.well-known/`

Search engine indexing is **not affected**. Bots like Googlebot and Bingbot are explicitly allowed to pass **without challenge**.

#### **Visual Verification**

BotStopper can also be configured on a per-domain basis. When enabled, the first request to a domain presents a short visual verification page. Once the user passes this check, all subsequent requests load normally without interruption. This process is effective against bots, as most cannot properly handle JavaScript challenges. The verification page itself can be lightly customized within the extension to reflect your branding.

###  CDNetworks

Our Web Application Firewall (WAF), powered by CDNetworks, helps filter malicious and suspicious traffic before it reaches your server. It offers protection based on:

* IP-based rules and geo-blocking
* Rate limiting
* Basic user-agent filtering
* Custom security rules

While it does not include a dedicated anti-bot engine or advanced bot fingerprinting, it still helps mitigate common automated attacks like basic content scraping, and credential stuffing from known malicious IPs.

You can find out more about CDNetworks and the available plans in [this article.](../../content-delivery-network)

(please note that WAF+DOS protection are in a separate category in the article above)

###  Imunify360

Imunify360 adds:

* Bot protection using heuristics
* Captcha verification
* DDoS mitigation
* Malware scanning and real-time defense

###  CloudLinux and LVE Limits

LVE limits lets us control how much CPU, RAM, and I/O each domain can use. This means if a single site is attacked or abused by bots, it won't take down the entire server.

Please note that you can't have both Imunify360 and Cloudlinux on your server. Cloudlinux is an OS like AlmaLinux, and running imunify360 on cloudlinux could create conflicts. However, ImunifyAV is still available on cloudlinux (i think?)

## Understanding How Each Layer Works

Here’s a simplified view of how different tools interact:

| Tool       | Filters before PHP code is executed? | Blocks CPU/RAM drain? |
|------------|--------------------|----------------------|
| robots.txt | No                 | No                   |
| .htaccess  | Yes                | Partially            |
| Anubis(beta) | Yes | Yes |
| CDNetworks WAF        | Yes                | Yes                  |
| Imunify360 | Yes                | Yes                  |
| LVE limits | No*                | Yes                  |

\* LVE limits **do not** filter requests before reaching PHP, but if **configured properly**, they will restrict or kill processes that exceed defined limits for memory, CPU, or disk I/O—effectively containing resource abuse.


!!!! To reduce server load, it's **critical** to block malicious traffic as early as possible.

## The Cost of Bad Code
When your code is inefficient, even a small number of requests can use a lot of memory or CPU, triggering alerts or rendering your server/domain unresponsive.

* **RAM example**: One PHP process of the domain example.com is serving a single page and using 200MB+. With a max_children setting of let's say 20, this example.com domain will solely use 4GB of RAM.
* **CPU example**: A slow database query or loop in PHP can max out a CPU core.
* **Disk I/O**: Repeated warnings or errors written to logs for invalid requests can cause disk bottlenecks.

## How to Protect Your Site and Server

Going back to points 1 to 6 above, there's several tools to mitigate bot traffic:

* robots.txt and .htaccess – Free and effective for low-level filtering
* BadBotBlocker Extension
* BotStopper Extension
* WAF – Premium protection with  bot mitigation
* Imunify360 – Included in many plans, or available as an upgrade
* CloudLinux LVE – Included on shared servers and managed servers to isolate high resource usage

!!!! If your website is under bot pressure or slowing down from unknown traffic, [contact us](../../support). 
We can help you analyze the logs and provide tailored recommendations for the best course of action moving forward.
