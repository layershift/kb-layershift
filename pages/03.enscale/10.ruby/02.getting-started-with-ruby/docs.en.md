---
title: 'Getting started with Ruby'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/ruby/getting-started-with-ruby'
    'og:type': website
    'og:title': 'Getting started with Ruby |  Layershift KB'
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Getting started with Ruby |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'article:published_time': '2023-09-30T10:09:52+01:00'
    'article:modified_time': '2023-09-30T10:09:52+01:00'
    'article:author': Layershift
---

### Overview

Enscale provides Ruby support via:

* Passenger (Apache or Nginx)
* Unicorn (Nginx)
* Puma (Nginx)

Each run your choice of Ruby version:

* 1.9.3
* 2.0.0
* 2.1.5
* 2.2.3

! You can switch Ruby version at any time in the Enscale dashboard.

### Dependency Management

Dependencies are resolved automatically by **Bundler**. Simply list required gems in your **Gemfile** and Bundler will search rubygems.org to install them for you. If you need to resolve a gem dependency from another location, specify its repository URL in your Gemfile and Bundler will download and install it from there for you instead.

Enscale offers all 3 standard deployment modes (`development`, `test`, `production`) which you can select from during deployment, and change later, in the Enscale dashboard.

Bundler attempts to resolve your dependencies in 3 cases:

* Initial deployment
* Switching Ruby version
* Change of deployment mode

!!! Bundler’s actions are logged and available to you in `bundle_install.log`

### Supported Frameworks

Any Ruby framework – just add the corresponding dependencies to your Gemfile! Here are some examples of popular frameworks you can run on Enscale:

* Ruby on Rails
* Sinatra
* Rack
* therubyracer
* Ramaze
* ExecJS

### Deploying Ruby apps

Enscale provides a choice of 2 deployment methods for your Ruby application to suit your preferred workflow.

* Deploy from git or svn
* Deploy using a file archive (zip, tar.gz)

!! Ruby application deployment can take a few minutes due to high CPU consumption during the deployment process

#### Post-deployment configuration

Enscale executes any post-deployment configuration actions (e.g. `db:migrate`) via rake according to commands found in the `rake_deploy` file within your application root. This file is deleted after successful execution, and results are logged and available to you in `rake_deploy.log`.


