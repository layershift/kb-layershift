---
title: 'Generate SSH Key using PuTTYgen '
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/ssh/generating-ssh-keys-with-puttygen'
    'og:type': website
    'og:title': 'Generate SSH Key using PuTTYgen |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/07.ssh/05.generating-ssh-keys-with-puttygen/Generate SSH Key using PuTTYgen-1.png'
    'og:image:type': image/png
    'og:image:width': 484
    'og:image:height': 472
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Generate SSH Key using PuTTYgen |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/07.ssh/05.generating-ssh-keys-with-puttygen/Generate SSH Key using PuTTYgen-1.png'
    'article:published_time': '2023-10-10T09:23:36+01:00'
    'article:modified_time': '2023-10-10T09:23:36+01:00'
    'article:author': Layershift
media_order: 'Generate SSH Key using PuTTYgen-1.png,Generate SSH Key using PuTTYgen-2.png,Generate SSH Key using PuTTYgen-4.png,Generate SSH Key using PuTTYgen-3.png,Generate SSH Key using PuTTYgen-6.png,Generate SSH Key using PuTTYgen-5.png'
---

With PuTTYgen you can generate SSH key pairs (public and private key) that are used by PuTTY to connect to your server from a Windows client. The private key will be stored on your local machine, while the public key has to be uploaded in your dashboard. When connecting with PuTTY, your session loaded with your private key will generate a signature which will be authenticated by the server using the matching public key.

### Download PuTTYgen

Simply download and save the PuTTYgen executable (.exe) file from this [link](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html). Since it’s a standalone application, you will not need to perform any installation steps for it.

### Generate SSH Key

* Open PuTTYgen.
* Select these parameters:

	* 	Enscale requires an SSH-2 RSA (recommended) or SSH-2 DSA key
	* 	The number of bits can be either 2048 or 4096 (recommended). This defines the strength of the key and its resistance to brute-force attacks.

* Click the **Generate** button.

![Generate%20SSH%20Key%20using%20PuTTYgen-1](Generate%20SSH%20Key%20using%20PuTTYgen-1.png "Generate%20SSH%20Key%20using%20PuTTYgen-1")

* Move your mouse randomly within the empty area to generate your key until the progress bar fills up.

![Generate%20SSH%20Key%20using%20PuTTYgen-2](Generate%20SSH%20Key%20using%20PuTTYgen-2.png "Generate%20SSH%20Key%20using%20PuTTYgen-2")

* In the next screen you can see the following:

![Generate%20SSH%20Key%20using%20PuTTYgen-3](Generate%20SSH%20Key%20using%20PuTTYgen-3.png "Generate%20SSH%20Key%20using%20PuTTYgen-3")

#### Your Public Key

You can copy and paste this key directly to your Enscale dashboard. To see how to add your public key to Enscale, please see: [How to connect to Enscale using PuTTY](/how-to-connect-to-jelastic-using-putty)

#### Your Key Fingerprint

In this field you should enter something to help you remember what you will use this key for. For example if you are going to use this key pair to connect to your Enscale environments, you could enter `Enscale` here.

#### Key passphrase

Here you can set a password you can use to encrypt your Private Key. While this is not mandatory, it is strongly recommended to ensure that nobody from your workstation will be able to connect to your server without knowing the passphrase.

! If you are using SSH for scripts, you will need to leave the Key passphrase field empty.

### Save your SSH key

You can either copy and paste your public key into the Enscale dashboard, or you can click the `Save public key` button to save the file on your computer. You can open it with a simple text editor, like Notepad.

You should save the private key on your computer as a .ppk (PuTTY Private Key) file.

![Generate%20SSH%20Key%20using%20PuTTYgen-4](Generate%20SSH%20Key%20using%20PuTTYgen-4.png "Generate%20SSH%20Key%20using%20PuTTYgen-4")

### Load a previous SSH key

If you would like to change the comment or passphrase for an existing SSH key, or you would simply like to view the fingerprint or maybe save another copy of the public key, you can always load your SSH key in PuTTYgen.

* Open **PuTTYgen**.
* Click **Load**

![Generate%20SSH%20Key%20using%20PuTTYgen-5](Generate%20SSH%20Key%20using%20PuTTYgen-5.png "Generate%20SSH%20Key%20using%20PuTTYgen-5")

* Select your SSH Private Key file.

![Generate%20SSH%20Key%20using%20PuTTYgen-6](Generate%20SSH%20Key%20using%20PuTTYgen-6.png "Generate%20SSH%20Key%20using%20PuTTYgen-6")

* Enter your passphrase if prompted and click **OK**

* You will see the Public key, fingerprint and related information in the PuTTY Key Generator window.

