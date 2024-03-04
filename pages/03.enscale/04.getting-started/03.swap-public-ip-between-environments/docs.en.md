---
title: 'Swap public IP between environments'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'Introduction Many applications call for a background script to be kept running in order to perform certain important housekeeping tasks. As developers we like to write these scripts using the language we find convenient for the task at hand, which means it''s common for them to be in PHP or node.js. Neither are particularly good ..'
metadata:
    description: 'Introduction Many applications call for a background script to be kept running in order to perform certain important housekeeping tasks. As developers we like to write these scripts using the language we find convenient for the task at hand, which means it''s common for them to be in PHP or node.js. Neither are particularly good ..'
    'og:url': 'https://www.layershift.com/kb/enscale/getting-started/swap-public-ip-between-environments'
    'og:type': website
    'og:title': 'Swap public IP between environments | Layershift KB'
    'og:description': 'Introduction Many applications call for a background script to be kept running in order to perform certain important housekeeping tasks. As developers we like to write these scripts using the language we find convenient for the task at hand, which means it''s common for them to be in PHP or node.js. Neither are particularly good ..'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-04T14:30:02+00:00'
    'article:modified_time': '2024-03-04T14:30:02+00:00'
    'article:author': Layershift
---

Shifting workloads between different environments – e.g. blue-green deployment – can be a painful process if you lack the right tools for the job. Thankfully Enscale makes it easy for you to migrate a public IP, completely eliminating any DNS propagation effects and reducing downtime for this process to just a few seconds.

This feature is intended to be used by advanced users, such as within a CI/CD workflow. Therefore it is currently only available via the CLI tool or API commands:

## Enscale CLI

**Skills required: Java-jitsu**

Enscale provides a CLI tool to simplify interacting with your account and environments.

The tool is relatively easy to use and you can install it on your local machine.

### Prepare your machine

Before installing the CLI tool, you need to ensure a few things are present on your system.         

If you haven’t already, install Java 1.7 or higher on your local machine. Please refer to Java installation guides for [instructions on how to get Java](https://java.com/en/download/help/download_options.xml).

If you are a Windows user, you also need [Cygwin](https://cygwin.com/install.html) to provide you with a Unix-like environment. Mac and Linux users should skip this step.

### Installing Enscale CLI tool

To install CLI tool run the following on your command line / terminal:

	curl -s ftp://ftp.jelastic.com/pub/cli/jelastic-cli-installer.sh | bash

The tool will be installed in your home directory with all commands placed in a dedicated enscale directory.

On your first run you will be asked to provide your account details as well as Platform URL: app.enscale.cloud .

More detailed information on the CLI tool is available in the [PaaS documentation](https://www.virtuozzo.com/application-platform-docs/cli/).

### Swap the IP

Once the CLI tool is installed, you can use it to swap the public IPs used by any nodes within or between any environments on your account.

!!! The swap itself is fast and should only cause a few seconds interruption to traffic, but a service restart is triggered for the following nodes:

* GlassFish
* PHP (Apache or Nginx)
* Ruby (Apache or Nginx)

![Swap%20public%20IP%20between%20environments-2](Swap%20public%20IP%20between%20environments-2.png "Swap%20public%20IP%20between%20environments-2")

The command takes three parameters:

* **{envName}** – source environment name
* **{sourceNodeId}** – node ID that you wish to move the public IP from
* **{targetNodeId}** – node ID that you wish to move the public IP to (can belong to a different environment)

And optional parameters in case the environment has more than 1 IP attached:

* **{sourceIp}** – source environment IP
* **{targetIp}** – target environment IP

If the target node already has a public IP, it will be moved to the source node at the same time. I.e. the public IPs of the source and target nodes will be swapped.

Private / internal IP addresses are statically assigned to a node and cannot be swapped.

!!! NOTE: You can find node IDs in your dashboard; example marked below:

![Swap%20public%20IP%20between%20environments-3](Swap%20public%20IP%20between%20environments-3.png "Swap%20public%20IP%20between%20environments-3")

Once you have the details of the nodes you want to move public IP(s) between, you can do the swap using the command below:

    ~/jelastic/environment/control/swapextips --envName {env_name} \
        --sourceNodeId {source_node_id} \
        --targetNodeId {target_node_id} \
        --sourceIp sourceIp \
        --targetIp targetIp

![Swap%20public%20IP%20between%20environments-4](Swap%20public%20IP%20between%20environments-4.png "Swap%20public%20IP%20between%20environments-4")

You may verify the IP swap was successful by reviewing the response output, or checking the public IP assignments for each node as shown within the Enscale dashboard.

## Docker container

**Skills required: Inception**

If you would rather not install Java on your local machine but still wish to use the Jelastic CLI tool, you can make use of [Docker](https://www.docker.com/). Our engineers at Layershift have prepared a [lightweight docker image](https://hub.docker.com/r/layershift/jelastic-cli/) that has java and the CLI tool pre-installed. All you have to do is to pass some variables to the image and you can use the CLI tool straight away.

To run the container, specify the following variables:

* **J_LOGIN** – your Enscale login
* **J_PASSWORD** – your Enscale password
* **J_PLATFORM** – your Enscale provider Platform URL (app.enscale.cloud)

Run the image:

    docker run -it --rm \
     -e "J_LOGIN=you@domain.com" \
     -e "J_PASSWORD=password" \
     -e "J_PLATFORM=hoster.url" layershift/jelastic-cli

You will enter bash shell where you will be able to use the CLI commands.

!!! NOTE: This Docker image is intended to be run locally (not deployed onto Enscale).

## API

**Skills: God mode**

If you are brave enough not to install Java or don’t have a way or feel the need to install Docker, you may still swap IPs using a curl command, or in fact a few API commands issued from any programming language of your choice.

!!! NOTE: Windows users may need to install curl executable. It can be obtained from [here](https://curl.haxx.se/dlwiz/?type=bin). In the ‘Select operating system’ box, choose Win32 or Win64, depending on your architecture.

The swap IP API call is described in [PaaS API documentation](https://docs.jelastic.com/api/?class=environment.Binder&member=SwapExtIps).

Remember to change [hoster-api-host] to app.enscale.cloud.

The method takes the following parameters:

* **session** – your session key, created with signin API method.
* **envName** – source environment name
* **sourceNodeId** – node ID that you wish to move the public IP from
* **targetNodeId** – node ID that you wish to move the public IP to (can belong to a different environment)

And optional parameters in case the environment has more than 1 IP attached:

* **{sourceIp}** – source environment IP
* **{targetIp}** – target environment IP



