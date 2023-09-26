---
title: 'Run Enscale NodeJS application via supervisor'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/nodejs/run-enscale-nodejs-application-via-supervisor'
    'og:type': website
    'og:title': 'Run Enscale NodeJS application via supervisor |  Layershift KB'
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Run Enscale NodeJS application via supervisor |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'article:published_time': '2023-09-23T06:37:58+01:00'
    'article:modified_time': '2023-09-23T06:37:58+01:00'
    'article:author': Layershift
---

Supervisor is a handy little tool to keep your Node.js app running (auto restart if it goes down due to fatal errors), and automatically restart your app if it detects file changes.

It saves you the trouble of hunting for and killing the old process in such cases, so your development speed can be much faster.

Here’s how to run your Node app via supervisor on Enscale.

#### Connect to your Node ‘node’ via SSH

See [how to connect via SSH to your Node](https://kb.layershift.com/en/admin/pages/enscale/ssh/enscale-ssh-access/).

#### Execute the following commands

	sudo /etc/init.d/cartridge stop	
	cd ~/ROOT/
	supervisor --debug server.js &

#### Set up a cron to make this the default at server boot

Edit your crontab:

	crontab -e

Add the following entry on a new line:

	@reboot sudo /etc/init.d/cartridge stop && cd ~/ROOT/ && supervisor --debug server.js &

Save and quit with:
	
    :wq

