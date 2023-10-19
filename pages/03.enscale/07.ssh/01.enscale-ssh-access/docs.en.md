---
title: 'Enscale SSH Access'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/ssh/enscale-ssh-access'
    'og:type': website
    'og:title': 'Enscale SSH Access |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/07.ssh/01.enscale-ssh-access/Enscale SSH Access-1.png'
    'og:image:type': image/png
    'og:image:width': 513
    'og:image:height': 143
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Enscale SSH Access |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/07.ssh/01.enscale-ssh-access/Enscale SSH Access-1.png'
    'article:published_time': '2023-09-22T16:55:23+01:00'
    'article:modified_time': '2023-09-22T16:55:23+01:00'
    'article:author': Layershift
media_order: 'Enscale SSH Access-1.png,Enscale SSH Access-2.png,Enscale SSH Access-3.png,Enscale SSH Access-4.png,Enscale SSH Access-5.png,Enscale SSH Access-6.png'
---

### Why is SSH access useful?

The Enscale PaaS frees you from tedious server admin, so why would you want SSH access anyway?

Many popular frameworks now include CLI tools to perform various important tasks such as clearing the cache following code changes or easing site migrations. E.g. **Laravel’s Artisan**, **Drupal’s drush**, and **Symfony2’s** console to name just a few.

Of course, SSH access also gives you the freedom to install and run your own CLI code, such as Composer, the PHP dependency manager.

You might need to run your own custom **git** or **svn** commands; useful for conflict resolution, or if you need to push some changes from the server back to your repo – but note that any projects you create entirely via SSH will not appear within the Enscale dashboard (e.g. for auto-update purposes).

SSH access to database nodes enables you to import (or export) large .sql databases more easily, without needing to worry about PHP script limitations on phpMyAdmin/phpPgAdmin.

!!! Database command-line clients are not installed on Enscale application servers; you need to connect to the desired database server to access these commands (e.g. **mysql**, **mongo**, **psql**).

You can also use SSH to access application server level CLI tools such as **asadmin** or sanity check your Apache configuration file edits (`service httpd configtest`) before restarting the **httpd** service.

### Enscale SSH architecture

SSH access in Enscale is via an intermediary SSH Gateway, which keeps your individual servers more securely protected. The gateway uses key based authentication and then provides you with a simple text driven menu to access the desired node from any of your (running) environments.

![Enscale%20SSH%20Access-1](Enscale%20SSH%20Access-1.png "Enscale%20SSH%20Access-1")

### SSH connection settings

Username | Authentication | Host | Port | SSH fingerprint	
-------------- | ------------------  | ------ | ----- | ---------------------
Located in the dashboard, SSH Access settings (see below) | SSH key | sshgateway.io | 3022 | 73:e1:e2:8e:65:fe:7b:5e:2f:09:f9:d8:57:5e:a7:59(RSA)

!!! The key type must be RSA (DSA and Elliptic Curve keys such as ed25519 are not currently supported)

!! If you’ve previously connected to one of our old SSH gateway addresses, your SSH client may warn that the host key is already known to you by another name/address. The new sshgateway.io address is preferred because it automatically routes you to the nearest gateway for optimum performance.

### How to add your SSH key

!!! Need help generating your SSH key? Check out [how to generate your SSH key using PuTTYgen](https://kb.layershift.com/en/admin/pages/enscale/ssh/generating-enscale-ssh-keys-with-puttygen) blog post for a quick walkthrough or look up the `ssh-keygen` command available for Windows Powershell, Linux, and Mac OS.

* Log in to your [Enscale dashboard](https://app.enscale.cloud/)
* Select the desired environment and press **Settings**:

![Enscale%20SSH%20Access-2](Enscale%20SSH%20Access-2.png "Enscale%20SSH%20Access-2")

* From the menu, access **SSH Access** and press **Add Public SSH Key**:

![Enscale%20SSH%20Access-3](Enscale%20SSH%20Access-3.png "Enscale%20SSH%20Access-3")

* Enter a meaningful `Name` to help you identify this key in future, and copy/paste the SSH key into the `Key` box.

![Enscale%20SSH%20Access-4](Enscale%20SSH%20Access-4.png "Enscale%20SSH%20Access-4")

Repeat this process to add as many keys as needed, for each device that you wish to grant access to your Enscale environments.

### Connect to the SSH gateway

After you’ve added your keys, you’ll see the connection settings right above. Something like this:

	ssh 4856@sshgateway.io -p 3022

If you’re a Linux or Mac user, you can just click on that text in your dashboard and it’ll open up a terminal ssh session with those details on your behalf. However, if you’re using PuTTY or any other GUI based client (on your smartphone or tablet for example) that probably won’t work. So let’s take a moment to explain the important parts of that command in case you need to enter the connection settings manually:

* **4856** is the user. This will be different for you, so make sure to check your own dashboard!

* **sshgateway.io** is the hostname for the SSH gateway that you’re connecting to

* **3022** is the port number

!! The default port number for SSH is 22. You must change your SSH client settings to use **port 3022** for this connection or it will not work!

!!! If you have a separate ssh key for the Enscale gateway or the key is not recognized you might need to specify what key to use. Add -i to the ssh command. It will look like `ssh -i path/to/private/part 4856@sshgateway.io -p 3022`

Once connected you will see a menu listing all of your environments and their current status (stopped/running etc.). You can only access running environments. Simply select the desired environment to reach a list of individual nodes (virtual servers) contained within the environment.

### System user permissions

You are logged into each node as the primary system user for that given service. For example, on an Apache node you are logged in as the apache system user, and on a MySQL node you are logged in as the mysql system user etc. This simplifies issues such as file ownership/access, and is generally preferable for running application utilities such as **drush**.

You don’t have root level access, so cannot install or update system rpm’s – but because Enscale is a PaaS you don’t need to!

However, you have limited sudo permission to run selected commands such as `sudo service httpd restart`:

```
-bash-4.1$ service httpd configtest
Syntax OK
```

```
-bash-4.1$ service httpd restart
rm: cannot remove `/var/run/httpd/httpd.pid': Permission denied [FAILED]
Starting httpd: touch: cannot touch `/var/lock/subsys/httpd': Permission denied
```

```
-bash-4.1$ service httpd restart
rm: cannot remove `/var/run/httpd/httpd.pid': Permission denied [FAILED]
Starting httpd: touch: cannot touch `/var/lock/subsys/httpd': Permission denied
```

If you receive a password prompt when using **sudo** it means that command is not permitted: please contact us with your feedback if this is blocking something essential for your needs!

```
-bash-4.1$ sudo vim /etc/hosts
[sudo] password for apache:
```

### Enscale SSH access for scripts

The SSH gateway described above is great for human users, but because it’s interactive it’s not so easy for a script to connect and navigate. If you want to **scp**, **rsync**, or even use **SFTP** the menu system gets in your way. But don’t worry – we have a solution!

##### Find your Node ID

###### via Dashboard:

* Log in to your dashboard, and navigate to the desired environment

* Expand the UI to reveal the ID of the individual node you want to connect to:

![Enscale%20SSH%20Access-5](Enscale%20SSH%20Access-5.png "Enscale%20SSH%20Access-5")

###### via SSH gateway

* Connect to the SSH gateway as normal, and navigate the menus to the desired environment

* Make a note of the `nodeid` in the environment’s node list:

![Enscale%20SSH%20Access-6](Enscale%20SSH%20Access-6.png "Enscale%20SSH%20Access-6")

##### Connect

Establish a new SSH connection with the username in the format:
 `nodeid-uid@sshgateway.io -p 3022` (all other details are the same, including port number)

Authentication remains key-based (so you need to add the key via the dashboard as normal), but using this scheme you can create direct SSH connections for use in automated deployment scripts etc.

###### Examples

Using the example user ID from above (4856):

**SSH:**

* Apache: `ssh 518839-35526@sshgateway.io -p 3022`

**SFTP:**

* Apache: `sftp -P 3022 518839-35526@sshgateway.io `


!!! Your environment nodes are secured in a private network. SSH connection and authentication continues to be performed by the SSH gateway, even if using this “direct access” method. If authentication is successful the connection is transparently routed to the required server via the private network
