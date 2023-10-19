---
title: 'Enscale certified containers vs. Docker® containers'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/getting%20started/enscale-certified-containers-vs-docker-r-containers'
    'og:type': website
    'og:title': 'Enscale certified containers vs. Docker® containers |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/04.getting started/05.enscale-certified-containers-vs-docker-r-containers/Enscale certified containers vs. Docker® containers-1.png'
    'og:image:type': image/png
    'og:image:width': 464
    'og:image:height': 39
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Enscale certified containers vs. Docker® containers |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/04.getting started/05.enscale-certified-containers-vs-docker-r-containers/Enscale certified containers vs. Docker® containers-1.png'
    'article:published_time': '2023-10-01T15:33:11+01:00'
    'article:modified_time': '2023-10-01T15:33:11+01:00'
    'article:author': Layershift
media_order: 'Enscale certified containers vs. Docker® containers-1.png'
---

### What are Enscale certified containers?

When creating an environment in Enscale, you can choose between a variety of certified containers based on the programming language your application uses.

![Enscale%20certified%20containers%20vs.%20Docker%C2%AE%20containers-1](Enscale%20certified%20containers%20vs.%20Docker%C2%AE%20containers-1.png "Enscale%20certified%20containers%20vs.%20Docker%C2%AE%20containers-1")

When creating an environment by choosing one of the above options, you will be using specially crafted and verified Java, PHP, Ruby, Node.js, Go or Python Application nodes and the corresponding specially crafted and verified Load balancer, Database and Cache nodes as well.

All of these nodes are thoroughly tested and proven to work optimally on Enscale. In many cases these nodes also benefit from additional platform integration, such as automated configuration optimisation based on the resource (cloudlet) limits you define, or SSL certificate installation.

When you select to install an application from the Marketplace, we can assure you that the created environment is also using certified containers which are optimised to the needs of the application itself.

#### Elastic VPS

The Elastic VPS is the only option within the language-specific tabs that is not a certified container. It provides a pure CentOS container without any additional software installed.

Root access is provided to Elastic VPS containers. You install, configure, and maintain any software needed. This makes Elastic VPS a good choice to deploy other types of database, or application server, than those offered as Enscale certified containers. It’s almost like having a dedicated server, but with the advantages of automatic vertical scaling.

Since all configuration is done by you, our technical team are only able to assist with issues related to platform and network maintenance.

### What are Docker containers and how do they work on Enscale?

When you create a Enscale environment using Docker, you deploy a Docker image which might not use an official version of the programming language (e.g. may be a nightly snapshot, other pre-release, or customised version). You can choose from a huge variety of Docker images available via the Docker Hub Registry, or any other compatible and accessible (public or private) registry image.

As most applications require multiple containers (one per role), you will typically deploy multiple Docker containers within your environment, and then configure appropriate environment variables to link them together (e.g. database server credentials).

After you create the container, you will need to perform custom configurations either in the Configuration Manager or via Root SSH access.

Docker-based applications deployed from our Marketplace are already preconfigured for you; additional steps are not usually required.

### What’s the difference?

Although there are many third party Docker images, to take full advantage of Docker requires knowledge of the underlying OS packages. You have to do some low-level work to build, or modify, your server environment to fit your needs – and then additional work to maintain that (security patches, bugs etc.).

Using Enscale certified containers takes care of these headaches; you only care about your own code, nothing lower down the stack. The table below highlights some of the key differences:

Differences | Certified containers | Docker containers |
---------------------------------------------------------------------- |
SSH access level |       user         |          root               |
Server security patching |  Layershift |    Customer      |
Automatic config. tuning and optimisation | yes |  no   |
Advanced orchestration integration (deployment, SSL installation etc.) | yes | no |
Technical support | yes | no |
Server software quality | production grade | unknown |

When you create an environment using certified containers, you have the security of knowing that the language version you use is fully supported by the Enscale platform and has been thoroughly tested. However, when deploying a Docker image, it’s up to you to verify that the origins and quality of the server software meets your needs.

We have been working with containers since 2003 and our experienced technical team can offer troubleshooting advice and recommend optimal configurations. We perform security patching against deployed certified containers as well, so you can remain fully focussed on your own application code – no need to become a sysadmin each time a new CVE is published!

With the multitude of Docker images available, it is impossible for us to test them all and ensure that they are both secure and fully operational. This responsibility falls on the shoulders of the Docker image creator.

From this reason stems the fact that we cannot apply security patches automatically to environments created in Docker containers, as we have no way of knowing exactly what the image contains. Docker images, or a base image, may be updated at the registry to contain an important security fix. We give you the ability to redeploy your Docker containers to benefit from those updates, but it is your responsibility to monitor for their release. You are also putting faith in the image creator to make the updates safe and secure. When using a custom image, our technical team can only offer support for the platform and network connectivity.

Root access is not available on certified containers, to ensure safe and reliable security patching (we can’t patch or support something where we don’t know what you’ve installed or modified!). However most modifications that require root access can be handled on your behalf by our 24/7 support team. You still have SSH access on our certified containers, allowing you to edit configuration files, access application level CLI tools, import/export from database and so on.

When using a Docker image, you have root access to apply any modifications for yourself – but pay attention that they should be incorporated back to the registry image or your next re-deploy could revert all of your hard work!

### Which should I use?

The main benefit of Docker containers is portability. You define your application’s server environment on your laptop and can consistently and repeatedly deploy that same server environment to all stages of the application lifecycle (development, staging, production).

The drawback is that a server has multiple packages that need to be installed – each with potential for new vulnerabilities to be uncovered. You need to pay very close attention to security patches for each of your dependencies. This is often a difficult issue for developers, because most organisations do not have the capacity or 24×7 availability to react to new security issues with the necessary speed. In any case, the natural focus for developers is the application code that they write – not low level server packages like glibc, OpenSSL or NSS. Neglect this at your peril.

Of course, Docker containers are really useful to augment the platform. If your application requires a language/version that is not currently available via a Enscale certified container, a Docker image gives you access to that extra functionality. This can also be used to test bleeding edge technologies and major new releases. For example some of our customers tested PHP 7 release candidates on our platform via Docker containers prior to the final release version and addition of PHP 7 as an option in our certified containers.

In summary, we strongly recommend using certified containers in most cases. Babysitting a server should not be your responsibility. You have enough to worry about already. Don’t take on more headaches than you have to! By using a certified container, we can take care of this for you so that you can remain fully focussed on your application code.
