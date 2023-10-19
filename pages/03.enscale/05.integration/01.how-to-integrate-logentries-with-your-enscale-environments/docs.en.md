---
title: 'How to integrate Logentries with your Enscale environments'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/integration/how-to-integrate-logentries-with-your-enscale-environments'
    'og:type': website
    'og:title': 'How to integrate Logentries with your Enscale environments |  Layershift KB'
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'How to integrate Logentries with your Enscale environments |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'article:published_time': '2023-09-09T11:45:38+01:00'
    'article:modified_time': '2023-09-09T11:45:38+01:00'
    'article:author': Layershift
---

The Enscale UI always gave you access to your different component log files, however now you can stream these logs into a Logentries account which will give you the opportunity to benefit from log visualisation, search, alerts, etc. so you can easily identify application errors, warnings or exceptions.

That way, you can quickly be notified if there are any issues in your systems, and figure out a solution to any of these problems. You can also store all your Enscale logs at Logentries for as long as you want, so you can keep track of business analytics, operations, etc.

### Create your Logentries account

If you don’t already have a Logentries account, you can [create one](https://logentries.com/quick-start/) quickly and easily (free 30-day trial, with 100% free for 1GB or less logging per month).

### How to Setup Logentries in your Java environment

Logentries already have a guide specifically for you! Follow the [instructions on their site](https://logentries.com/doc/jelastic/) to configure Logentries with your Enscale Java environment.

### How to Setup Logentries in your PHP environment

For your PHP environment, you may use the [standard PHP Logentries logging mechanism](https://logentries.com/doc/php/). This is generally the best method for handling application-level logs with Logentries, but note that it performs the logging synchronously, and therefore it will slow your application down a little during communications to the Logentries servers.

Alternatively, you can implement your own local logging and parse it asynchronously to send those log events to logentries.

We’ve got you covered If you prefer to use the [Logentries agent](https://logentries.com/doc/agent/) too! As our Enscale platform is fully managed, and the agent needs to be installed at OS level, we will perform the install for you – just open a [support ticket](https://www.layershift.com/support/?form=technical) and one of our engineers will be more than happy to assist.

Don’t forget to mention which server/s and within which environment/s you want the agent to be installed on, and the desired log files / filename patterns you wish to be logged!

### Conclusion

The Logentries setup in your Enscale environment is really a piece of cake and it gives you a huge amount of value!

Have you already tried Logentries with Enscale? What are your experiences? What else would you like to see integrated with the Enscale platform?

Tweet us (@Layershift) or [email your feedback to our team](email your feedback to our team).