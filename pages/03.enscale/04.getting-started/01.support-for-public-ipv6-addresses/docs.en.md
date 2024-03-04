---
title: 'Support for Public IPv6 Addresses'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'Find out details about IPv6 protocol and a few tips to help get you started on using IPv6 addresses with Enscale Paas.'
metadata:
    description: 'Find out details about IPv6 protocol and a few tips to help get you started on using IPv6 addresses with Enscale Paas.'
    'og:url': 'https://www.layershift.com/kb/enscale/getting-started/support-for-public-ipv6-addresses'
    'og:type': website
    'og:title': 'Support for Public IPv6 Addresses | Layershift KB'
    'og:description': 'Find out details about IPv6 protocol and a few tips to help get you started on using IPv6 addresses with Enscale Paas.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-04T10:04:53+00:00'
    'article:modified_time': '2024-03-04T10:04:53+00:00'
    'article:author': Layershift
---

## What are IPv6 Addresses?

The‌ ‌IPv6‌ ‌protocol‌ ‌was‌ ‌invented in the 90s but was only formally‌ ‌approved‌ ‌as‌ ‌an‌ ‌internet‌ ‌standard‌ ‌in‌ ‌2017 when ISP’s and various providers started rolling it out one by one. It ‌was‌ ‌designed‌ ‌as‌ ‌a‌ ‌replacement‌ ‌for‌ ‌the‌ ‌IPv4‌ ‌protocol,‌ ‌which‌ ‌has‌ ‌almost‌ ‌exhausted‌ ‌all‌ ‌its‌ ‌available‌ ‌4.3-billion‌ ‌address‌ ‌space.‌ ‌

It‌ ‌functions‌ ‌similarly‌ ‌to‌ ‌IPv4‌ ‌in‌ ‌that‌ ‌it‌ ‌provides‌ ‌the‌ ‌unique‌ ‌IP‌ ‌addresses‌ ‌necessary‌ ‌for‌ ‌Internet-enabled‌ ‌devices‌ ‌to‌ ‌communicate,‌ ‌but‌ because ‌it‌ ‌utilizes‌ ‌a‌ ‌128-bit‌ ‌size ‌not ‌32‌ ‌bit‌ ‌like‌ ‌the‌ former standard, it exponentially increased the available addresses.

The many key benefits they come with may not be visible for the common internet user, but they do make the life of techs working behind the scenes a lot easier:

* Solves private address collisions
* Comes with built-in authentication and privacy support
* Simplifies processes for routing
* Offers better multicast routing and a simpler header format
* Eliminates NAT (Network Address Translation)
* Provides‌ ‌easier‌ ‌administration‌

## When to use IPv6?

In short, you should start right away.

As‌ ‌mobile‌ ‌device‌ ‌adoption‌ ‌continues‌ ‌to‌ ‌expand‌ ‌rapidly,‌ Internet of Things (IoT) is making its way more and more into our lives, at‌ ‌some‌ ‌point,‌ ‌new‌ ‌devices‌ ‌will‌ ‌no‌ longer‌ ‌be‌ ‌able‌ ‌to‌ ‌connect‌ ‌to‌ ‌internet‌ ‌services‌ ‌that‌ ‌require‌ ‌an‌ ‌IPv4‌ ‌address.‌ ‌There‌ ‌are‌ ‌temporary‌ ‌solutions‌ ‌such‌ ‌as‌ ‌CGN‌ ‌NAT,‌ ‌but‌ ‌these‌ ‌have‌ ‌their‌ ‌own‌ ‌headaches‌ ‌associated‌ ‌with‌ ‌scalability‌ ‌and‌ ‌geo-location‌ ‌personalization.‌ ‌

Depending‌ ‌on‌ ‌your‌ ‌business‌ ‌profile‌ ‌and‌ ‌type‌ ‌of‌ ‌users,‌ ‌you‌ ‌should‌ ‌consider‌ ‌providing‌ ‌support‌ ‌for‌ ‌IPv6‌-only ‌users too,‌ ‌so‌ ‌that‌ ‌you‌ ‌don’t‌ ‌end‌ ‌up‌ ‌dropping‌ ‌traffic‌ ‌without‌ ‌even‌ ‌knowing,‌ ‌as‌ ‌it‌ ‌won’t‌ even ‌make‌ ‌it‌ ‌to‌ ‌your‌ ‌web‌ ‌server‌ ‌logs.‌

More and more wan networks are using the IPv6 protocol as their priority. This means that as soon as the webpage is available in the IPv6 version, the connection will take place in this protocol, but without a notable difference to the end user.

## Notation differences

You’ll notice some mild differences that you need to take into account when first starting to use IPv6 protocol, not limited to the below:

* A single address can be notated in different ways, but the most compressed version should be generally used:

* An IPv6 address has a total of 128 bits that are represented in hexadecimal form, using 8 x 4 hex character groupings, separated by a colon (:) as you can see in the example below:

!!! Expanded: 3001:abcd:0000:0000:0123:1234

* Addresses can be compressed depending on the digits by substituting the 0 with double colon (::), though note than just one double colon can be used in the notation:

!!! Compressed leading zeros: 3001:abcd:0:0:123:1234

!!! Compressed using double colon: 3001:abcd::0123:1234

!!! Compressed leading zeros and double colon: 3001:abcd::123:1234

* IPv6 addresses should be enclosed in square brackets in URLs: http://[234:abcd::123:1234]/index.html

* SSH will work only without the brackets: username@3001:abcd::123:1234

* You’ll need to use ping6 instead of ping

## Cost

IPv6 addresses are free of charge but limited to 10 per Enscale node or 50 per Cloud VPS containers. 

**Note:** Public IP’s (IPv4 and IPv6) are not available for trial accounts, due to high abuse risk, but they can be enabled by request. Let our friendly [sales team](sales@layershift.com) know if you want to test this feature.

## How to enable

For Cloud VPS customers, IPv6 addresses can be enabled in the [Customer Control Panel](https://control.layershift.com/cp) > **Account** > **Buy Resources** > **Next** and follow the wizard to place the order:

![Support%20for%20Public%20IPv6%20Addresses-1](Support%20for%20Public%20IPv6%20Addresses-1.png "Support%20for%20Public%20IPv6%20Addresses-1")

If you are a Enscale user, you can easily enable IPv6 addresses via the environment topology wizard in your [Dashboard](https://app.enscale.cloud) or via [API](https://docs.jelastic.com/multiple-public-ip/#api-reference-on-multiple-public-ips).

![Support%20for%20Public%20IPv6%20Addresses-2](Support%20for%20Public%20IPv6%20Addresses-2.png "Support%20for%20Public%20IPv6%20Addresses-2")

## Configuration tips

* Connections‌ ‌will‌ ‌run‌ ‌over‌ ‌IPv6‌ ‌protocol when‌ ‌possible,‌ ‌but‌ ‌we‌ ‌recommend‌ ‌enabling‌ ‌IPv6‌ ‌alongside‌ ‌your‌ ‌IPv4‌ ‌address‌ ‌to‌ ‌avoid‌ ‌any‌ ‌connection‌ ‌issues‌ ‌in‌ ‌case‌ ‌IPv6‌ ‌is‌ ‌not‌ ‌yet‌ ‌fully‌ ‌supported‌ ‌by‌ ‌your‌ ‌end‌ ‌users‌ ‌browsers‌ ‌for‌ ‌example.‌ ‌
* In‌ ‌case‌ ‌the‌ ‌address‌ ‌type‌ ‌to‌ ‌use‌ ‌is‌ ‌not‌ ‌specifically‌ ‌indicated‌ ‌(e.g.‌ ‌in‌ ‌JPS‌ ‌packages,‌ ‌add-ons‌ ‌or‌ ‌when‌ ‌creating‌ ‌a‌ ‌VPS‌ ‌node),‌ ‌the‌ ‌IPv4‌ ‌will‌ ‌be‌ ‌used‌ ‌by‌ ‌default.‌ ‌
* You‌ ‌will‌ ‌be‌ ‌able‌ ‌to‌ ‌attach‌ ‌multiple‌ ‌IPv6‌ ‌IP‌ ‌addresses‌ ‌to‌ ‌a‌ ‌single‌ ‌container‌ ‌and‌ ‌adjust‌ ‌their‌ ‌number‌ ‌or‌ ‌swap‌ ‌them‌ ‌if‌ ‌required.‌ ‌This‌ ‌will allows ‌you to run ‌several‌ ‌websites‌ ‌on‌ ‌a‌ ‌single‌ ‌node.‌ 
* You can configure your DNS settings to indicate that your site supports IPv6 connections via AAAA records and make sure that your content is virtually identical to your IPv4 content for SEO reasons when using both IP address protocols for the same website.

## Conclusion

Most users won’t notice which IP address type they are using as everything will continue to work seamlessly during the transition thanks to the fact that this functionality is mostly invisible to them. 

The IPv6 protocol solves our immediate issue of running out of IP addresses by allowing us to connect more devices to the internet, but it also gives the tech industry the possibility of re-architecting the world wide web in order to improve performance, security and privacy.

Login to your [Enscale Dashboard](https://app.enscale.cloud) or your [VPS Customer Control Panel](https://control.layershift.com/cp/) and give IPv6 a try.

If you don’t have an account, [get in touch](mailto:sales@layershift.com) and we’ll do our best to advise on the best solution for you!




