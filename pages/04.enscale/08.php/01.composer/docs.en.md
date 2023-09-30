---
title: Composer
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/php/composer'
    'og:type': website
    'og:title': 'Composer |  Layershift KB'
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Composer |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'article:published_time': '2023-09-30T08:59:23+01:00'
    'article:modified_time': '2023-09-30T11:52:24+01:00'
    'article:author': Layershift
---

Composer is a popular dependency manager for PHP, borrowing from the ideas of **npm** (node) and **bundler** (ruby). It’s super easy to install and use **Composer** on the Enscale PaaS.

### How to Install Composer on your Enscale Server

Connect to your **Apache PHP** or **Nginx PHP** server in one of your Jelastic environments using the [Enscale SSH gateway](https://kb2.layershift.com/enscale/ssh/jelastic-ssh-access). Change your working directory to a suitable one of your choice, such as **/var/www/webroot**:

	-bash-4.1$ cd /var/www

Then simply execute the **Composer installer** as normal:

	-bash-4.1$ curl -sS https://getcomposer.org/installer | php

That’s all there is to it! Composer is installed and ready to use. But, we can also make a few little optimisations to make life easier:

	-bash-4.1$ mkdir ~/bin
	-bash-4.1$ mv ~/composer.phar ~/bin/composer

This does 2 things at once:
	* Renames composer.phar to composer, to save your fingers some work in future
    * Moves composer to a private bin directory which is helpful for the next step

### Add Composer to your PATH

This step allows you to effortlessly execute **composer** from any working directory on the server, without having to write out its full path; otherwise you’d need to write **/var/www/bin/composer** (or **/var/lib/nginx/bin/composer**) each time you want to call it!

#### Apache

	-bash-4.1$ export PATH=$PATH:/var/www/bin	
	-bash-4.1$ echo 'export PATH=$PATH:/var/www/bin' >> ~/.bash_profile

#### Nginx

	-bash-4.1$ export PATH=$PATH:/var/lib/nginx/bin
	-bash-4.1$ echo 'export PATH=$PATH:/var/lib/nginx/bin' >> ~/.bash_profile

!!! Bash offers various startup files. For our purposes, `~/.bash_profile` is fine because every SSH login via the gateway is invoked as an interactive login shell; you could equally use `~/.bashrc` providing that you also call it from your `~/.bash_profile`.

### Using Composer

To confirm that the above steps have worked:

	-bash-4.1$ composer about
	Composer - Package Management for PHP
	Composer is a dependency manager tracking local dependencies of your projects and libraries.
	See http://getcomposer.org/ for more information.

Now you can use Composer to manage dependencies within your PHP projects.










