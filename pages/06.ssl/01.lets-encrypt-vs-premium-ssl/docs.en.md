---
title: 'Let’s Encrypt vs Premium SSL'
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/ssl/lets-encrypt-vs-premium-ssl'
    'og:type': website
    'og:title': 'Let’s Encrypt vs Premium SSL |  Layershift KB'
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Let’s Encrypt vs Premium SSL |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'article:published_time': '2023-08-26T16:33:37+01:00'
    'article:modified_time': '2023-08-26T16:33:37+01:00'
    'article:author': Layershift
---

Back in 2014, Google’s [announcement](https://security.googleblog.com/2014/08/https-as-ranking-signal_6.html) that websites served from https will get better SEO rankings, along with their call for “https everywhere”, raised a lot of controversy amongst developers and site owners. Some were quite happy with this initiative as they bought into the idea that generalised https use will make the internet safer, while others mainly saw it as an unnecessary, complicated and expensive decision that not only meant they needed to [re-code](https://developer.chrome.com/blog/avoid-not-secure-warn/) their websites to use https but also spend more money on SSL certificates they didn’t otherwise need.

If, at the time, it may not have seemed very likely that https will take over the world wide web so easily, and many non-believers dismissed the importance of Google’s decision, here we are, in 2017, where Google is already marking non-https websites that request passwords or credit card details as insecure. This sure makes the whole initiative look a lot more convincing and the permanent transition to https appears to be inevitable now.

To comply with Google’s requirements and avoid their website being flagged as “not secure”, every site owner should aim to provide all pages of their websites over https as soon as possible, as many other browsers are also switching to actively warn (rather than passively ignore) unencrypted connections too. Google have a [short walk through about changing to https](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes?visit_id=638286604048668608-3971439028&rd=1) in case you need some guidance.

What’s important to note is that simply enabling https on a domain is not enough – every element of your page must be loaded via https (all images, javascript, css files), so you should take a moment to check any third party services that you integrate in your code (analytics, social plugins etc.) and make sure they are configured correctly.

### What is Let’s Encrypt and how is it different from a traditional Certificate Authority


!!!! Let’s Encrypt is a free, automated, and open certificate authority (CA), run for the public’s benefit. It is a service provided by the Internet Security Research Group (ISRG).”

While you might get dazzled by the “free” aspect of the service, it’s also important to consider the rest of the implications that come with using this service. After all, you know what they say: all that glitters is not gold.

The principle behind Let’s Encrypt is simple – they support the generalisation of https and want to make it available to everyone. However, due to their non-profit business model and the limited resources (which mainly come from donations, sponsorships or crowdfunding), they need to focus their efforts on sustaining the organisation’s core principle, which is developing an easy, automated SSL issuance process. Their goal is not to provide end user support for certificate generation / renewals, which is understandable given the nature of this initiative and the little manpower available (at the time of writing this article they had eight full time employees and two other members of staff that were hired by partner companies).

Let’s Encrypt is still a young service – they only left Beta in April 2016 – which means that they don’t have the reputation, credibility and experience of an established Certificate Authority and therefore lack a very important feature that traditional CAs provide, which is ubiquity. All browsers and Operating Systems have a default root repository containing a list of approved (or trusted) CAs along with their root certificates which states which Intermediary Certificate to be trusted or not, so being part of this elitist group is very important for a certificate authority.

Put another way, because they are still a new company, Let’s Encrypt’s certificates are not yet 100% accepted by browsers, especially those that were released before this organisation came to life, which is why they reached out to IdenTrust, another certificate authority that is trusted by most major browsers, to cross-sign their CAs. Whilst this solves most browser warnings, it still leaves some compatibility issues which we will discuss further later in this article.

On the bright side, Let’s Encrypt use their self-issued root and Intermediate certificates and the private keys are stored, according to their website, on hardware security modules (HSMs) where they are out of hackers’ reach. They are also part of the Certificate Transparency program, which helps keep the certificates misuse under control and weighs as a strong point for them, but they lack the added warranty the traditional Certificate Authorities provide, and only issue SSL certificates with a short validity period (their SSLs are only valid for 90 days) which can be a bit of a hassle. Most CAs have certificate lifetimes that last up to 3 years, making the renewals less frequent.

### Benefits and limitations

##### Issuance speed

Because Let’s Encrypt certificates are free and their issuance process is entirely automated, certificates are generated really fast, if not instant. The validation is performed very quickly with the help of an [ACME protocol](https://ietf-wg-acme.github.io/acme/) based software and users can have a valid certificate enabled on their domain in a matter of seconds.

In contrast, with a traditional CA, you have to place an SSL order first, either directly on their website or through a reseller, and then perform the validation steps manually, which can take from a few hours to several days, depending on the certificate type purchased.

##### Validation / visitor trust level

The only certificate types available through Let’s Encrypt are the basic or SAN (multi-domain) DCV SSL certificates; the recently established Certificate Authority have no plans to offer Organisation Validated or Extended Validation certificates in future.

DCV stands for Domain Control Validation which means the only thing that is being checked before issuing the certificate is that the certificate requester has access to the domain, by either uploading a simple .txt file in the root folder of the domain or by adding a specific DNS record in the domain zone. This raises quite a lot of question marks over the credibility of https since basically anyone can have access to a free SSL certificate now, including malicious organisations that will by no means miss the chance to use the https padlock, which is a worldwide recognised symbol of security, to try pass as “genuine” businesses.

Free, easy access to trusted SSL certificates minimises the importance of https and uneducated users can be tricked more easily. How will visitors be able to tell the difference between a genuine respectable business and a phishing website?

This is where the Organisation Validated / Extended Validation certificates step in. For these types of certificate, in addition to  the DCV step, businesses are also required to prove their legitimacy – either by showing proof of incorporation or by providing other documents attesting their existence as a bona fide trading entity. Furthermore, for Extended Validation certificates, the validation is even more thorough – CAs perform independent checks to confirm that the information provided by the requester matches those available in public registers.

OV / EV SSL certificates always include some information about the website owner, depending on the level of validation, and browsers expose this certificate information to website visitors – e.g. using a green address bar containing the company name – which can substantially increase their trust level. We expect this impact to get higher as the inevitable scandals emerge regarding scams involving basic DCV certificates.  OV / EV SSL certificates also usually provide branded site seals which further increase end user confidence through association with a known / trusted security brand (Verisign / Symantec etc.).

Please refer to our blog for further [comparison between the different certificate types](https://blog.layershift.com/ssl-certificates-explained/).

##### Browser compatibility

As mentioned earlier, Let’s Encrypt are not fully compatible with all browsers, due to the fact that they are still a new Certificate Authority and legacy browsers / operating systems don’t recognise them. Let’s Encrypt publish a list of known incompatibilities:

Possibly Incompatible:

* Sony PS3 and PS4 Game Consoles

Known Incompatible: 

* Blackberry OS v10, v7, & v6 (Comodo support 4.3.0 + )
* Android < v2.3.6 (comodo – 1.5 +)
* Nintendo 3DS
* Windows XP prior to SP3
* Java 7 < 7u111
* Java 8 < 8u101

In practice, most website operators should find that Let’s Encrypt is compatible with the devices used by the majority of their clients. However [as with SNI](https://blog.layershift.com/sni-ssl-production-ready/), if you have clients still using older operating systems, browsers, or mobile devices, you may encounter problems.

Purchasing a premium SSL certificate issued by a well established Certificate Authority should typically avoid compatibility issues entirely, because they are already well recognised and trusted by all major software and hardware combinations – not just now, but in the past as well (meaning older devices also work as expected).

##### Reliability and certificate lifetime

Let’s Encrypt certificates have a maximum lifetime of 90 days. Given that renewal is 100% automated,  this might not appear to be an issue at first. However, the renewal process is not error free and quite a lot of issues were already reported on Let’s Encrypt’s community page: users are complaining about renewals failing for various reasons (problems with the .config files, failed domain control authentication, etc).

Without a reliable renewal system and with no support staff available to help troubleshoot the technical problems on the spot, renewing the SSL certificates can turn into a daunting task. Even with the correct sets of skills, because the renewals are so frequent, babysitting this process can still take up a lot of your time in the long run.

The simple fact that Certbot advise users to run their auto-renewal cronjobs multiple times per day should raise some red flags about the reliability of this process:

!!!! “if you’re setting up a cron or systemd job, we recommend running it twice per day (it won’t do anything until your certificates are due for renewal or revoked, but running it regularly would give your site a chance of staying online in case a Let’s Encrypt-initiated revocation happened for some reason).”

We can attest that most website operators definitely need more than just “a chance” of their website staying online, but of course this is a matter of getting the service level that you pay for (Let’s Encrypt certificates are free, so limitations should be expected…).

Premium SSL certificates have a lifetime of 1 – 2 years. Naturally, the longer the period between renewals, the lower the risk from a malfunctioning renewal process (at worst, it might impact your business once per 2 years vs. once per 3 months!).

Moreover, premium SSL certificates are normally renewed by a human. Provided that you have appropriate processes in place to ensure that a certificate expiry doesn’t slip by unnoticed, that human element can identify and resolve problems before they impact your business. For example, smoothing over validation or certificate installation problems that might’ve been missed or even compounded by simplistic automation.

At Layershift we take personal responsibility for each premium SSL certificate that we provide: we notify customers 60 days prior to certificate expiry, and manage the entire issuance / validation and installation process. The renewal reliability of a premium certificate from Layershift vs. the Let’s Encrypt certificate process is unmatched. If SSL renewal failures might cause problems for your business, a premium certificate should be a serious consideration.

##### Certificate limits

Let’s Encrypt do not issue wildcard certificates, meaning that you need a certificate for each specific subdomain that you wish to secure, and you must know the exact subdomain when you request the certificate (or replacement certificate).

You can request up to 20 certificates per domain in a 7 day period, so if you have more than 20 subdomains this can be awkward to manage. There is no override mechanism, so however you reach that limit (by mistakes or by volume of domains), the only possibility is to wait 7 days until the limit resets.

Although you can request multiple domains in 1 certificate, this is limited to 100 names – if you need more your only option is a premium SSL certificate.

There are also some other technical limits regarding the issuance and renewal process, but you shouldn’t normally hit them. Still, it’s important to note that if you do the only option is to wait for the limit to reset. There is no technical support person at Let’s Encrypt to make an exception for you.

### Should I still pay for SSL?

The answer to this question depends on the type of business you operate, the technical skills you or your IT department have and how much you value your time. Yes, Let’s Encrypt certificates are free and that’s obviously great if you’re on a tight budget, but in reality **the average cost of a premium SSL certificate is less than £1 per week**: amongst the lowest of your business overheads. Ask yourself – does the time and business risk involved with dealing with a potential renewal malfunction justify such a paltry cost saving?

As a  Layershift customer you already know that we provide fully managed services and our top-class support extends to ancillary services like SSL certificates or domains too. Purchasing a premium SSL from us comes with our white glove SSL management included, meaning that everything related to the ordering, installation, renewal, reissuance processes, even troubleshooting advice, falls under our responsibility.

Besides zero admin burden, premium SSL certificates carry a lot of weight with customers’ trust, which is a vital aspect in any business but especially in eCommerce scenarios where users need to feel comfortable with filling in their card details or giving out personal information and having a Green Bar or a Site Seal provides the much needed reassurance that the trade is being made by a reliable company.








