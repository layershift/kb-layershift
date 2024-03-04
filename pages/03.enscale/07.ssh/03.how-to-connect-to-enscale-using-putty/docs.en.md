---
title: 'How to connect to Enscale using PuTTY'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'Here you will find a step-by-step guide for how to connect to your Jelastic gateway or a specific node in your environment using PuTTY.'
metadata:
    description: 'Here you will find a step-by-step guide for how to connect to your Jelastic gateway or a specific node in your environment using PuTTY.'
    'og:url': 'https://www.layershift.com/kb/enscale/ssh/how-to-connect-to-enscale-using-putty'
    'og:type': website
    'og:title': 'How to connect to Enscale using PuTTY | Layershift KB'
    'og:description': 'Here you will find a step-by-step guide for how to connect to your Jelastic gateway or a specific node in your environment using PuTTY.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-04T09:25:34+00:00'
    'article:modified_time': '2024-03-04T09:25:34+00:00'
    'article:author': Layershift
---

Connecting to the SSH gateway or to your specific node is really easy, all you need to do make some basic configurations in your SSH client and you’re ready to go.

Bellow you can see what you need to do in 4 simple steps:

#### Add your Public Key

First you will need to add your Public Key to your account.

* Open **Settings > SSH Access** via the button at the right of the desired environment and press **Add Public SSH Key**, as shown below:

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-1](How%20to%20connect%20to%20Enscale%20using%20PuTTY-1.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-1")

* Enter a meaningful **Title** to help you identify this key in future, and copy/paste the SSH key into the **Key** box.

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-2](How%20to%20connect%20to%20Enscale%20using%20PuTTY-2.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-2")

* Finally, press **Add**.

#### Get your connection details

You can see your connection details by hovering over the desired environment and accessing `Settings > SSH Access > SSH Connection`:

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-3](How%20to%20connect%20to%20Enscale%20using%20PuTTY-3.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-3")

!!! **20106** is the User ID. This will be different for you, so make sure to check your own dashboard!

**sshgateway.io** is the hostname for the SSH gateway that you’re connecting to

**3022** is the port number

If you would like to connect to a specific node directly, you will need to combine the Node ID with your User ID to log in in the following format: **nodeID-userID**.

To get your Node ID, first find the environment and then expand the UI.

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-4](How%20to%20connect%20to%20Enscale%20using%20PuTTY-4.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-4")

**112559-20106** is the username needed to connect to this specific Apache node. Please note that you will need to check your dashboard for your own node ID.

#### Configure your PuTTY session

* Open PuTTY and go to **Session**:

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-5](How%20to%20connect%20to%20Enscale%20using%20PuTTY-5.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-5")

* Configure your basic session options and **save** it for future connections.

	* Enter the Host Name: **sshgateway.io**
	* Enter port number: **3022**
	* Name your session

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-6](How%20to%20connect%20to%20Enscale%20using%20PuTTY-6.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-6")

* Enter your username
* In the left hand pane select Connection > Data.

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-7](How%20to%20connect%20to%20Enscale%20using%20PuTTY-7.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-7")

If you would like to connect to the Enscale Gateway, enter your User ID.

If you would like to connect to a specific **node**, you will need a username in the following format: **nodeID-username**.

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-8](How%20to%20connect%20to%20Enscale%20using%20PuTTY-8.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-8")

* Add your private key

On the left-hand menu go to Connection > SSH > Auth and click Browse to find your Private key.

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-9](How%20to%20connect%20to%20Enscale%20using%20PuTTY-9.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-9")

* Save the session

Go back to **Session** and **Save** again.

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-10](How%20to%20connect%20to%20Enscale%20using%20PuTTY-10.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-10")

#### Connect to your Enscale environment

* Select the session name from your saved sessions and click Load to load your previously saved settings.

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-11](How%20to%20connect%20to%20Enscale%20using%20PuTTY-11.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-11")

* Click **Open**

![How%20to%20connect%20to%20Enscale%20using%20PuTTY-12](How%20to%20connect%20to%20Enscale%20using%20PuTTY-12.png "How%20to%20connect%20to%20Enscale%20using%20PuTTY-12")
