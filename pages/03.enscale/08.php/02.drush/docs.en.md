---
title: Drush
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'Quick install steps for Drush via Composer on the revolutionary Enscale PaaS.'
metadata:
    description: 'Quick install steps for Drush via Composer on the revolutionary Enscale PaaS.'
    'og:url': 'https://www.layershift.com/kb/enscale/php/drush'
    'og:type': website
    'og:title': 'Drush | Layershift KB'
    'og:description': 'Quick install steps for Drush via Composer on the revolutionary Enscale PaaS.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-04T09:41:01+00:00'
    'article:modified_time': '2024-03-04T09:41:01+00:00'
    'article:author': Layershift
---

The Drush Project Manager is an invaluable CLI tool for Drupal, enabling experienced Drupal administrators to perform various admin tasks via CLI that would otherwise require many clicks in the UI. In other words, just like Jelastic, it’s a massive time saver!

## How to install Drush on your Jelastic Server

The recommended way to install Drush is now using Composer (the Pear channel still exists, but will likely become deprecated in future – as has already happened with many other projects). Composer is really easy to use and offers a lot of benefits over pear; not least the flexibility to have different versions of the same software co-existing on one server (pear works globally).

So first up, you’ll need to install [Composer](../composer) (if you haven’t already done so).

Drush installation now becomes as simple as:

	-bash-4.1$ composer global require drush/drush:6.*

## Add Drush to your PATH

The above process installs **drush** to `~/.composer/vendor/drush/drush` but you can use your `~/.bash_profile` once again to put it into your path so it’s nice and convenient to use:

### Apache

	-bash-4.1$ export PATH=$PATH:/var/www/.composer/vendor/drush/drush
	-bash-4.1$ echo 'export PATH=$PATH:/var/www/.composer/vendor/drush/drush' >> ~/.bash_profile

### Nginx

	-bash-4.1$ export PATH=$PATH:/var/lib/nginx/.composer/vendor/drush/drush
	-bash-4.1$ echo 'export PATH=$PATH:/var/lib/nginx/.composer/vendor/drush/drush' >> ~/.bash_profile

## Using Drush

	-bash-4.1$ drush version
	Drush Version : 6.3.0

### Advanced configuration

Drush power users might also consider expanding the `~/.bash_profile` to include some of the aliases in the scripts on the [drush github page](https://github.com/drush-ops/drush#post-install) for even quicker access to the most useful drush commands.






