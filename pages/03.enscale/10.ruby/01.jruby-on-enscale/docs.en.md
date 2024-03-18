---
title: 'JRuby on Enscale'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'How to run JRuby application on Layershift Enscale PaaS to run high performance Ruby applications.'
metadata:
    description: 'How to run JRuby application on Layershift Enscale PaaS to run high performance Ruby applications.'
    'og:url': 'https://www.layershift.com/kb/enscale/ruby/jruby-on-enscale'
    'og:type': website
    'og:title': 'JRuby on Enscale | Layershift KB'
    'og:description': 'How to run JRuby application on Layershift Enscale PaaS to run high performance Ruby applications.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-04T09:58:23+00:00'
    'article:modified_time': '2024-03-04T09:58:23+00:00'
    'article:author': Layershift
---

### Why JRuby

[JRuby](http://jruby.org/) is a JVM implementation of Ruby, and therefore offers various performance and scalability benefits against [MRI based Ruby](../getting-started-with-ruby) applications.

Using JRuby you can access any Java library meaning that you can benefit from a very mature and vast Java ecosystem – many immature Ruby libraries already have well established Java equivalents which can offer you more performance, stability, features, or just an alternative option.

One of the main benefits often stated in favour of JRuby is performance, since running on the JVM means you get multi-threaded concurrency. This is a double-edged-sword however since it also exposes more potential problems: if your locking is incorrect, your code is likely to break.

### How to Deploy JRuby applications to Enscale

First install the JVM and JRuby locally on your own computer.

When you’re ready to deploy, install the [warbler gem](https://rubygems.org/gems/warbler) and use it to build a WAR file from your project. It’s a simple as this:

	-bash-4.1$ warble war

!!! This process should work for any Rails, Merb, or Rack-based application. Please refer to the [Warbler docs](http://rubydoc.info/gems/warbler/1.4.3/frames) for more details.

Once you have your WAR file, it can be deployed to any Java application server on Enscale by [upload to the deployment manager](../../getting-started/deploy-a-simple-application-from-a-zip-war-or-ear-archive) in the dashboard.
