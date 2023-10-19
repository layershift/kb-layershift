---
title: 'Generating Enscale SSH keys with PuTTYgen'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/ssh/generating-enscale-ssh-keys-with-puttygen'
    'og:type': website
    'og:title': 'Generating Enscale SSH keys with PuTTYgen |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/07.ssh/02.generating-enscale-ssh-keys-with-puttygen/Generating Enscale SSH keys with PuTTYgen-1.png'
    'og:image:type': image/png
    'og:image:width': 357
    'og:image:height': 350
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Generating Enscale SSH keys with PuTTYgen |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/07.ssh/02.generating-enscale-ssh-keys-with-puttygen/Generating Enscale SSH keys with PuTTYgen-1.png'
    'article:published_time': '2023-10-07T11:36:01+01:00'
    'article:modified_time': '2023-10-07T11:40:48+01:00'
    'article:author': Layershift
media_order: 'Generating Enscale SSH keys with PuTTYgen-1.png,Generating Enscale SSH keys with PuTTYgen-2.png,Generating Enscale SSH keys with PuTTYgen-3.png,Generating Enscale SSH keys with PuTTYgen-4.jpg'
---

We’ve just added key-based SSH access to our Enscale PaaS, and with many of our Windows users using PuTTY as their preferred SSH client it seems a good moment to give a brief PuTTYgen walkthrough. Here’s how to generate SSH keys using PuTTY.

* [Download and open puttygen.exe](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) (included with putty-version-installer.exe, or standalone)
* Enter the following parameters (the defaults are fine):

Type of key | Number of bits
--------------- | -----------------------------------
SSH-2 RSA ir SSH-2 DSA | 2048

* Note the OpenSSH compatible output at the top of the window. This is what you’ll need to copy/paste into the Enscale dashboard. You can always access this again later using the ‘Load an existing  private key file’ option.

![Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-1](Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-1.png "Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-1")

* Enter a **Key comment** to help you to identify this key later. For example something describing where you use this key. We’re just using rsa-key-enscale since we’ll use this key with our Enscale PaaS

* Your key is saved encrypted on disk, and the **key passphrase** will be used to unlock it when you want to use it. In other words, this protects your key from malicious use, so treat it like any other password – use something long and strong!

* Save the private key part to your computer before exiting PuTTYgen (note: you can save the public key file too if you wish, but it’s not saved in OpenSSH format so it’s not useful here).

Don’t forget to copy/paste the public key (in OpenSSH format) from step #3 into your Enscale dashboard. See our Enscale SSH Access KB article for more details.

### Configure PuTTY to use your SSH key

* Add the private key to PuTTY, under `Connection > SSH > Auth`. Just browse for your .ppk file (private key saved from **PuTTYgen**). The other settings on this screen can be left as the defaults.

![Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-2](Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-2.png "Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-2")

* (optional) Configure your username, under Connection > Data so that you don’t have to enter it manually every time you connect. Your Enscale SSH user ID is located in the SSH Access settings section of your Enscale dashboard. We’re using user 3072 in our example. Make sure to replace this with your specific user ID.

![Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-3](Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-3.png "Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-3")

* Finally, configure the host name (gate.j.layershift.co.uk) and SSH port (3022) for the connection. We recommend that you save the session profile so that you can connect again easily in future.

![Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-4](Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-4.jpg "Generating%20Enscale%20SSH%20keys%20with%20PuTTYgen-4")

* Then just hit **Open** to establish your SSH connection. Enter your SSH key passphrase, and you’re connected. Take a moment to verify the SSH fingerprint presented during the authentication phase matches the one published in our KB article.

Next time you can just **Load** the saved session and **Open**.

Congrats! Now you can use PuTTY to connect to your ENscale PaaS servers via SSH using key based authentication.