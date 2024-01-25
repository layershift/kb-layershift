---
title: 'Deploy NodeJS application on Enscale'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/nodejs/run-enscale-nodejs-application-via-supervisor'
    'og:type': website
    'og:title': 'Deploy NodeJS application on Enscale |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/08.nodejs/01.run-enscale-nodejs-application-via-supervisor/Run Enscale NodeJS application via supervisor-1.png'
    'og:image:type': image/png
    'og:image:width': 876
    'og:image:height': 548
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Deploy NodeJS application on Enscale |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/08.nodejs/01.run-enscale-nodejs-application-via-supervisor/Run Enscale NodeJS application via supervisor-1.png'
    'article:published_time': '2023-12-27T03:35:42+00:00'
    'article:modified_time': '2023-12-27T03:35:42+00:00'
    'article:author': Layershift
media_order: 'Run Enscale NodeJS application via supervisor-1.png,Deploy NodeJS application on Enscale-2.png,Deploy NodeJS application on Enscale-3.png,Deploy NodeJS application on Enscale-4.png'
---

To launch your **Node.js application**, you must configure the necessary environment through the robust and user-friendly Topology Wizard. Navigate to the Node.js tab, choose the suitable engine version for your application server, and include any additional software stacks needed. If necessary, make adjustments to other parameters like cloudlets and node count, Public IPv4 and IPv6, etc.

![Run%20Enscale%20NodeJS%20application%20via%20supervisor-1](Run%20Enscale%20NodeJS%20application%20via%20supervisor-1.png "Run%20Enscale%20NodeJS%20application%20via%20supervisor-1")

### Node.js Versioning

Currently, the following Node.js versions are supported:

* 21.5.9 and below
* 20.10.0 and below
* 18.19.0 and below
* 16.20.0 and below

![Deploy%20NodeJS%20application%20on%20Enscale-2](Deploy%20NodeJS%20application%20on%20Enscale-2.png "Deploy%20NodeJS%20application%20on%20Enscale-2")

You can select the required **version of Node.js** directly from the topology wizard during the creation of a new environment and adjust it for the existing one via **container redeployment.**

### Node.js Application Deployment

Enscale PaaS automates the deployment process for the managed NodeJS application servers using:

* application archive uploaded from the local machine or via external URL
* remote VCS repository (e.g. 
 
![Deploy%20NodeJS%20application%20on%20Enscale-2](Deploy%20NodeJS%20application%20on%20Enscale-2.png "Deploy%20NodeJS%20application%20on%20Enscale-2")GitHub)

### Node.js Package Managers

To facilitate development, NodeJS application servers incorporate a versatile tool known as a package manager, streamlining the installation, upgrading, configuring, and removing of essential components. Enscale, a prominent cloud-based application platform, supports two prominent package managers:

* **npm** - manages your project requirements by installing the additional modules, packages, and ready-to-use applications
* **yarn** - operates the same requirements as in npm (so no changes are required for the existing applications), while providing higher speed, reliability, and convenience

![Deploy%20NodeJS%20application%20on%20Enscale-4](Deploy%20NodeJS%20application%20on%20Enscale-4.png "Deploy%20NodeJS%20application%20on%20Enscale-4")

### Node.js Process Managers

**Process managers** serve as robust tools for managing application lifecycles, monitoring ongoing services, and ensuring project operability. Enscale PaaS, a comprehensive cloud-based platform, offers support for the following process managers tailored to the NodeJS stack:

* npm - initiates and configures multiple processes
* pm2 - provides a huge variety of application management features, including the launched Node.js processes monitoring

Users can effortlessly select the appropriate process manager during container redeployment or by modifying the PROCESS_MANAGER environment variable. To implement the chosen process manager, a container restart is necessary. The available process managers include forever, npm, pm2, and supervisor.