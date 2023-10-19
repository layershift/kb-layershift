---
title: 'Connect to your Plesk server using SSH client'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/cloud-vps/ssh/connect-to-your-plesk-server-using-ssh-client'
    'og:type': website
    'og:title': 'Connect to your Plesk server using SSH client |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/01.cloud-vps/05.ssh/02.connect-to-your-plesk-server-using-ssh-client/Connect to your Plesk server using SSH client-1.png'
    'og:image:type': image/png
    'og:image:width': 803
    'og:image:height': 1131
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Connect to your Plesk server using SSH client |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/01.cloud-vps/05.ssh/02.connect-to-your-plesk-server-using-ssh-client/Connect to your Plesk server using SSH client-1.png'
    'article:published_time': '2023-10-10T09:19:40+01:00'
    'article:modified_time': '2023-10-10T09:22:35+01:00'
    'article:author': Layershift
media_order: 'Connect to your Plesk server using SSH client-1.png,Connect to your Plesk server using SSH client-3.png,Connect to your Plesk server using SSH client-2.png,Connect to your Plesk server using SSH client-5.png,Connect to your Plesk server using SSH client-6.png,Connect to your Plesk server using SSH client-7.png,Connect to your Plesk server using SSH client-4.png'
---

In order to successfully connect to your server / website over SSH you’ll have to:

* Allow SSH access for your domain
* Configure your SSH client

### Allow SSH access for your domain

Log in to your **Plesk Dashboard**, go to `Websites & Domains`, then go to `Web Hosting Access` for your domains that you want to connect to. Choose **/bin/bash** shell and save it:

[Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-1](Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-1.png "Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-1")

### Connect using password

You have to find out the user to be used to establish the connection. For this go to **Web Hosting Access** for domain that you want to connect to.

Open the **Putty** client. In the PuTTY configuration window, into the `Host Name (or IP address)` field enter the username and host name or IP address of your server separated by **@** as well as into the **Saved Sessions** field. Then, click `Save` to save the new session so you can reuse it later. Click the newly saved session then click Open to establish the connection.

![Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-2](Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-2.png "Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-2")

### Connect using SSH key pair

Using SSH keys is more convenient and secure than traditional password authentication, therefore we are going to show you how to use SSH key pair for authentication. You’ll have to generate your own key pair, for this follow this guide to [Generate your key pair](/generate-ssh-key-using-puttygen-2).

#### Install the SSH Keys Manager extension

Go to **Extensions**, search for `SSH Keys Manager` and click `Get it Free` to install it.

![Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-3](Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-3.png "Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-3")

Go to particular subscription to manage SSH keys for access to that subscription via SSH. At right hand side click `SSH Keys`, then click `Add key` to add your public key.

#### Configure the SSH client

We are using PuTTY, a free SSH client for Windows and UNIX platforms. [Download](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) it to your machine and run it.

Double click the PuTTY executable file to launch it. In the PuTTY configuration window, into the `Host Name (or IP address)` field enter the host name or IP address of your server as well as into the `Saved Sessions` field. Then, click `Save` to save the new session so you can reuse it later.

![Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-6](Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-6.png "Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-6")

In the `Connection -> SSH -> Auth` section, browse to the private key file (.ppk) you’ve previously generated.

![Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-4](Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-4.png "Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-4")

In the `Connection -> Data` section, enter the username ( system user of your domain ) into the `Auto-login username` field, under the `Login details` section.

![Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-5](Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-5.png "Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-5")

In the `Session` section, click on the `Save` button to save the current configuration.

Select the session you want to start (in case that you have saved more than one session) and click the `Open` button to open an SSH session to the server.

![Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-7](Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-7.png "Connect%20to%20your%20Plesk%20server%20using%20SSH%20client-7")

**PuTTY** will first ask you to confirm the server’s host key and add it to the cache. Go ahead and click `Yes`.

