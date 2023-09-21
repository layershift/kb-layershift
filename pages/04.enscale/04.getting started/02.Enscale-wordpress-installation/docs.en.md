---
title: 'Enscale WordPress Installation'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://kb.luca.uk.easy-server.com/enscale/getting%20started/enscale-wordpress-installation'
    'og:type': website
    'og:title': 'Enscale WordPress Installation |  Layershift KB'
    'og:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/04.getting started/02.Enscale-wordpress-installation/Jelastic WordPress Installation-9.png'
    'og:image:type': image/png
    'og:image:width': 598
    'og:image:height': 419
    'og:author': Layershift
    'twitter:card': summary_large_image
    'twitter:title': 'Enscale WordPress Installation |  Layershift KB'
    'twitter:site': '@layershift'
    'twitter:creator': '@layershift'
    'twitter:image': 'https://kb.luca.uk.easy-server.com/user/pages/04.enscale/04.getting started/02.Enscale-wordpress-installation/Jelastic WordPress Installation-9.png'
    'article:published_time': '2023-08-31T13:33:55+01:00'
    'article:modified_time': '2023-08-31T13:33:55+01:00'
    'article:author': Layershift
media_order: 'Jelastic WordPress Installation-9.png,Jelastic WordPress Installation-8.png,Jelastic WordPress Installation-10.png,Jelastic WordPress Installation-1.png,Jelastic WordPress Installation-2.png,Jelastic WordPress Installation-3.png,Jelastic WordPress Installation-7.png,Jelastic WordPress Installation-5.png,Jelastic WordPress Installation-6.png,Jelastic WordPress Installation-4.png'
published: true
---

To create a new environment with a manual installation of WordPress you will have to take the following steps:

### Deploy new environment

* Create a new environment with the desired resources:

![Enscale%20WordPress%20Installation-1](Jelastic%20WordPress%20Installation-1.png "Enscale%20WordPress%20Installation-1")

* The environment you create should have at least one application server (Apache,Nginx) and a database server (Mysql/Mariadb)

![Enscale%20WordPress%20Installation-3](Jelastic%20WordPress%20Installation-3.png "Enscale%20WordPress%20Installation-3")

![Enscale%20WordPress%20Installation-4](Jelastic%20WordPress%20Installation-4.png "Enscale%20WordPress%20Installation-4")

* After the environment was created, you will receive an email with login credentials for the database server. Keep those at hand, as we will need them soon.

### Upload and deploy the WordPress archive

* Next, we will proceed to upload the WordPress archive to the server. You can download the default WordPress installer from [here](https://wordpress.org/latest.zip).

* In the lower left corner you will see the **Deployment Manager** option.

* Here, click the **Upload** button, and select the newly downloaded archive.

* From here, check the WordPress-master.zip archive, and click **Upload** as shown in the following images:

![Enscale%20WordPress%20Installation-5](Jelastic%20WordPress%20Installation-5.png "Enscale%20WordPress%20Installation-5")

* After the archive was deployed successfully, in the top right corner you will be prompted with the following message. Please click the **Open in Browser** button.

![Enscale%20WordPress%20Installation-6](Jelastic%20WordPress%20Installation-6.png "Enscale%20WordPress%20Installation-6")

### Configure WordPress

* Now we will proceed to create the database that will be used for the new **WordPress installation**.

* From the email you received, please select the one regarding the database server. It will contain a link to the database server, the user name (root) and the user password. Using these, please connect to the database server. From here, select the **Databases** tab on the top side, set the database name, and click **Create** as shown here:

![Enscale%20WordPress%20Installation-7](Jelastic%20WordPress%20Installation-7.png "Enscale%20WordPress%20Installation-7")

* After the database was created, we will proceed to create a database user.

* To do so, we will have to click the database we created, and go to the privileges tab on the top bar. From here, click **Add User account** on the bottom left, and proceed to create the user. We strongly recommend you to use a unique username and a strong password (should contain uppercase letter, lowercase letters, numbers, special character).

![Enscale%20WordPress%20Installation-8](Jelastic%20WordPress%20Installation-8.png "Enscale%20WordPress%20Installation-8")

* Now switch back to the WordPress installation page and connect the new database to the server using the following settings:

**Database Name:** the database name you created
**Username:** my_user
**Password:** password created for the mysql user
**Database host:** server name from email (node####-XXX.j.layershift.co.uk)

![Enscale%20WordPress%20Installation](Jelastic%20WordPress%20Installation-9.png "Enscale%20WordPress%20Installation-9")

* Create the administrator username, and password. We strongly recommend you to use a unique username and a strong password (should contain uppercase letter, lowercase letters, numbers, special character)

![Enscale%20WordPress%20Installation-10](Jelastic%20WordPress%20Installation-10.png "Enscale%20WordPress%20Installation-10")

Congratulations! You have successfully installed WordPress on your new Enscale Environment.


