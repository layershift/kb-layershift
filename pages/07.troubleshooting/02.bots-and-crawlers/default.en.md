---
title: 'Bots, Crawlers, and LLMs'
aura:
    pagetype: website
metadata:
    'og:url': 'https://www.layershift.com/kb/troubleshooting/bots-and-crawlers'
    'og:type': website
    'og:title': 'Bots, Crawlers, and LLMs | Layershift KB'
    'og:image': 'https://www.layershift.com/kb/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2026-01-19T11:06:28+00:00'
    'article:modified_time': '2026-01-19T11:06:28+00:00'
    'article:author': Layershift
---

!!! Bots, crawlers, and large language models (LLMs) are now a major source of web traffic. While **some are beneficial**, (like those used by search engines) many are abusive, disruptive, or even harmful to websites and servers. 

This article explains how these crawlers evolved, the problems they cause, and the tools you can use to defend your hosting environment.

## How Bots and Crawlers Appeared
Bots began as helpful tools used by search engines to index websites. Googlebot and Bingbot were among the first, enabling website owners to index their websites for better SEO results and visibility in search engines.
Over time, the landscape changed. Bots became more diverse, with many created to gather specific types of data, test vulnerabilities, or scrape entire websites. Some followed the rules. Many didn’t.

## The First Bad Bots

Bad bots started showing up once people realized there was value in mass data collection. The early ones were designed to:

* Harvest email addresses
* Scrape product prices
* Probe websites for vulnerable WordPress plugins
* Launch brute-force login attacks

Their purpose was usually SEO manipulation, competitive analysis, or spamming. These bots often ignore robots.txt, rotate IPs to avoid detection, and overload servers with requests.

## Good Bots

Some bots are useful and necessary for your site’s visibility:

* Googlebot indexes your pages for Google Search. You can manage its behavior (including crawl rate) via Google Search Console.
* Bingbot is used by Microsoft Bing and is customizable via Bing Webmaster Tools.
* Meta/Facebook Crawler fetches page previews for shared links.

These bots are well-documented, and you can verify them online. They generally respect robots.txt and are not aggressive.

## Bad Bots

Bad bots come in many forms, including:

* PetalBot: A crawler from Huawei that often floods websites with requests and doesn't provide much control for webmasters.
* AhrefsBot: From an SEO tool—technically legitimate but known for extremely high request rates.
* New User-Agents: Every day new bots show up with names like "RandomBot"

There has been a significant increase in the quantity of bot traffic attempting to access everyone's websites - related to the growth of AI (LLM). Large Language Models require vast quantities of training data in order to acquire their "knowledge", and for the most part they do that by "stealing" it from any and every public information source they can (i.e. including your website). Due to the competition between AI vendors, there is a race to acquire this knowledge as quickly as possible, during which the needs of the content owners (website operators) are disregarded. Unlike search engines, their business is not to work "in harmony" with your website, but to simply consume the data as quickly as they can for their own competitive advantage.

Altogether, this means that even if your website continues to serve a similar number of legitimate visitors, it is likely experiencing significantly more bot traffic than before. Many of these bots are designed to evade detection and bypass restrictions, making them harder to block. As a result, your server faces increased computational load and resource pressure compared to earlier times.

Even if they're not actively malicious, they can overwhelm your server by hitting it thousands of times per hour.

## Crawlers in Disguise

Some crawlers are written by _really talented_ developers, often for machine learning or data aggregation. They simulate real users and often go undetected by standard bot protection tools. These include:

* LLM scrapers
* Aggregator tools
* AI research bots

These bots appear in logs as legitimate traffic and aren't blocked easily. Even advanced protection tools might let them through.

They might make:

* 20–50 requests per second during peak
* Several thousand in 10 minutes
* Repeated requests to heavy WordPress pages, causing strain

examples of requests below:
```
[08/Jul/2025:18:45:01 +0100] "GET /wp-json/wp/v2/posts?per_page=100 HTTP/1.1" 200 54212 "-" "Mozilla/5.0 (compatible; ML-Bot/2.1; +http://example.com/bot)"
[08/Jul/2025:18:45:03 +0100] "GET /wp-admin/admin-ajax.php?action=load_dashboard_widgets HTTP/1.1" 200 32876 "-" "Mozilla/5.0 (compatible; AIResearch/1.0)"
[08/Jul/2025:18:45:04 +0100] "GET /wp-content/uploads/2024/12/highres-banner.jpg HTTP/1.1" 200 1048202 "-" "curl/7.79.1"
[08/Jul/2025:18:45:06 +0100] "POST /wp-json/contact-form-7/v1/contact-forms/123/feedback HTTP/1.1" 200 19432 "-" "python-requests/2.28.1"
[08/Jul/2025:18:45:09 +0100] "GET /?s=product+review+plugin HTTP/1.1" 200 29876 "-" "Mozilla/5.0 (compatible; GPTScraper/3.0; +https://ai.example.org)"
[08/Jul/2025:18:45:13 +0100] "GET /wp-content/plugins/woocommerce/assets/js/frontend/cart-fragments.min.js HTTP/1.1" 200 73984 "-" "-"
[08/Jul/2025:18:45:17 +0100] "GET /wp-json/wp/v2/media?per_page=50&page=2 HTTP/1.1" 200 61230 "-" "-"
[08/Jul/2025:18:45:22 +0100] "GET /wp-content/uploads/2025/03/video-promo.mp4 HTTP/1.1" 206 2048124 "-" "Mozilla/5.0 (Linux; Android 11)"
[08/Jul/2025:18:45:24 +0100] "GET /wp-admin/css/colors.min.css?ver=5.8.1 HTTP/1.1" 200 14982 "-" "-"
[08/Jul/2025:18:45:27 +0100] "GET /wp-content/themes/twentytwentyone/assets/js/primary-navigation.js?ver=1.3 HTTP/1.1" 200 18841 "-" "Google-Extended (Large-Scale Crawler)"
```

## Static Resources

Serving static content like images, CSS, or JavaScript files to many visitors (even thousands at the same time) is generally not a problem. The real issue arises when bots trigger full page loads, which involve running WordPress or other CMS stacks, executing PHP, and querying the database. Most bots typically do not just request static resources; instead, they often request full pages, which consumes significantly more server resources and can lead to performance issues.

## WordPress Installations
WordPress sites are among the top targets for bots. Commonly abused endpoints include:

* `/wp-login.php`: brute-force login attempts
* `/xmlrpc.php`: used for DDoS attacks or mass commenting
* `/wp-json/`: used for scraping public content

If your WordPress install is not well-optimized, even a single bot request can trigger heavy PHP execution and database queries.

## HTTP Responses: What the Server Tells You
The server’s HTTP responses can help you understand bot behavior:

* 200 OK: The page loaded; request may have triggered backend logic.
* 301/302: These indicate that a page has moved permanently or temporarily. While not inherently problematic, if misconfigured (e.g. redirect chains or loops), they can confuse bots and lead to excessive crawling or indexing issues.
* 404 Not Found: Often indicates a bot scanning for known vulnerability entry points, such as outdated plugins, admin panels, or common exploit paths that don’t exist on your site.












