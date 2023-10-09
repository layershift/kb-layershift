---
title: 'SSH between Enscale nodes'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/ssh/ssh-between-enscale-nodes'
    'og:type': website
    'og:title': 'SSH between Enscale nodes |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/07.ssh/04.ssh-between-enscale-nodes/SSH between Enscale nodes-1.png'
    'og:image:type': image/png
    'og:image:width': 1106
    'og:image:height': 200
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'SSH between Enscale nodes |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/07.ssh/04.ssh-between-enscale-nodes/SSH between Enscale nodes-1.png'
    'article:published_time': '2023-10-08T17:15:45+01:00'
    'article:modified_time': '2023-10-08T17:15:45+01:00'
    'article:author': Layershift
media_order: 'SSH between Enscale nodes-1.png'
---

The [Enscale SSH gateway](https://kb.luca.uk.easy-server.com/enscale/ssh/enscale-ssh-access) provides convenient SSH access from outside the platform – via an interactive menu, or [directly to a specific node](https://kb.luca.uk.easy-server.com/enscale/ssh/enscale-ssh-access).

However, sometimes you need an SSH connection between nodes inside the platform. Perhaps to rsync or scp some files. The SSH gateway is not an option for this scenario, but all it takes is an SSH key and a little firewall tweak.

### Create SSH key

Open an SSH session (via the **gateway**) to the source node.

Once logged in, enter the user home directory (the home directory location varies by node type):

```
apache@apache2 ~ $ cd ~
apache@apache2 ~ $ pwd
/var/www
```

Check if you already have any SSH keys in place with:

```
apache@apache2 ~ $ ls -al ~/.ssh
total 12K
drwx------ 2 apache apache 4.0K Feb 29 12:05 .
drwxr-xr-x 6 root   root   4.0K Nov 19 21:43 ..
-rw------- 1 apache apache  428 Feb 29 12:05 authorized_keys
```

Now it’s time to create SSH key. This is performed with the following command:

```
apache@apache2 ~ $ ssh-keygen -t rsa -b 4096 -C `hostname`
# Creates a new ssh key, using the node hostname as label.
Generating public/private rsa key pair.
```

Now it’s time to create SSH key. This is performed with the following command:

```
apache@apache2 ~ $ ssh-keygen -t rsa -b 4096 -C `hostname`
# Creates a new ssh key, using the node hostname as label.
Generating public/private rsa key pair.
```

If you want to use more than one SSH key within the environment, specify a different key name (with full path) than the one suggested by ssh-keygen:

```
Enter file in which to save the key (/var/www/.ssh/id_rsa):
```

Once prompted for key password, skip it, unless you will use the SSH connection interactively.

```
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```

On successful creation, ssh-keygen will give you details of the newly created key:

```
Your identification has been saved in /var/www/.ssh/id_rsa.
Your public key has been saved in /var/www/.ssh/id_rsa.pub.
The key fingerprint is:
66:50:58:5e:03:83:f9:42:bf:fb:69:d4:a5:31:0b:d0 your-node-hostname
The key's randomart image is:
+--[ RSA 4096]----+
|       ==oo      |
|      =o.oE.     |
|     ..o..       |
|      ..o . o .  |
|       .S. o *   |
|       o. . +    |
|         o       |
|        . ..     |
|         oo      |
+-----------------+
```

The key is now ready. You will see 2 new files created in your .ssh directory – id_rsa (the private part), and id_rsa.pub (the public part).

The private part stays on the source node. Meanwhile the public part should be copied to wherever you want to be able to connect to (destination / target node).

Copy the public part of the key and append it on a new line in the authorized_keys file on the target node:

```
apache@apache2 ~ $ cat ~/.ssh/id_rsa.pub
ssh-rsa [...] apache2.j.layershift.co.uk
```

On the target node, once connected via Gateway, edit .ssh/authorized_keys with your favourite text editor or echo the key to the file:

```
apache@apache-target ~ $ echo “ssh-rsa [...] apache2.j.layershift.co.uk” >> ~/.ssh/authorized_keys
```

! If you want to use the key for any other purpose, such as **git**, you can add it to your **ssh-agent** to keep it there for as long as your SSH session is opened. To do so, issue:

```
apache@apache2 ~ $ eval $(ssh-agent -s)
Agent pid 24521
apache@apache2 ~ $ ssh-add .ssh/id_rsa
Identity added: .ssh/id_rsa (.ssh/id_rsa)
```

#### Firewalling nodes

Now you need to allow the target node to accept ssh connections from source node. This can be done with [Enscale Firewall custom rules management](https://www.virtuozzo.com/application-platform-docs/custom-firewall/).

First, check the internal IP of your source node, either from Enscale Dashboard, by expanding the cog button next to the node:

![SSH%20between%20Enscale%20nodes-1](SSH%20between%20Enscale%20nodes-1.png "SSH%20between%20Enscale%20nodes-1")

Or with ifconfig command:

```
apache@apache2 ~ $ ifconfig
[...]
venet0:0: flags=211<UP,BROADCAST,POINTOPOINT,RUNNING,NOARP>  mtu 1500
        inet 10.10.117.85  netmask 255.255.255.255  broadcast 10.10.117.85  destination 10.10.117.85
```

Your node IP address is assigned to `venet0:0` interface and starts with **10.10.**

Now, it’s time to allow the source node to connect via SSH to target node.

Once logged in via Enscale Gateway to target node, edit `/etc/sysconfig/iptables-custom` file:

```
apache@apache-target ~ $ vim /etc/sysconfig/iptables-custom
```

Insert the following rules:

```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
-I INPUT -p tcp -s <SOURCE_NODE_IP_ADDRESS> --dport 22 -j ACCEPT
COMMIT
#
```

Don’t forget to save your changes (e.g. with `:wq` command, in case of vim editor).

Now, you need to apply the newly defined rules with next command, so the custom firewall rule will automatically be added the common firewall ones:

```
apache@apache-target ~ $ sudo /usr/bin/jem firewall fwstart
{"result":"0","message":"Firewall has been started","log":""}
```

And check the firewall rule with:

```
apache@apache-target ~ $ ~ $ sudo /usr/bin/jem firewall list filter -vn
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     tcp  --  *      *       10.10.117.85         0.0.0.0/0            tcp dpt:22
[...]
```

Once the rule is in place, we can now test SSH connection. From the source node you can connect to our target node with `ssh jelastic@` command.

You have to use `jelastic` username as this is SSH user name:

```
apache@apache2 ~ $ ssh jelastic@10.10.126.248
The authenticity of host '10.10.126.248 (10.10.126.248)' can't be established.
RSA key fingerprint is xxx.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.10.126.248' (RSA) to the list of known hosts.
 
  Welcome to Jelastic shell
 
  This shell will assist you in managing Jelastic applications.
 
    ============================== ATTENTION ==============================
   Shell access is rather powerful and you can accidentally damage your application.
   So please pay special attention to the actions you perform here.
    ============================== ATTENTION ==============================
 
 
Last login: Mon Mar 21 09:48:57 2016
apache@apache-target ~ $
```

And that’s it! If you need any assistance with setting up firewall rules on your environment nodes, contact our [24/7 support team](https://www.layershift.com/support/?form=technical).


