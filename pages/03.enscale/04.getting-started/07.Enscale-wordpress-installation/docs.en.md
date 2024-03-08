---
title: 'Enscale WordPress Installation'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'To create a new environment with a manual installation of WordPress you will have to take the following steps: Deploy new environment Create a new environment with the desired resources: 2. The environment you create should have at least one application server (Apache,Nginx) and a database server (Mysql/Mariadb) 3. After the environment was created, you ...'
metadata:
    description: 'To create a new environment with a manual installation of WordPress you will have to take the following steps: Deploy new environment Create a new environment with the desired resources: 2. The environment you create should have at least one application server (Apache,Nginx) and a database server (Mysql/Mariadb) 3. After the environment was created, you ...'
    'og:url': 'https://www.layershift.com/kb/enscale/getting-started/enscale-wordpress-installation'
    'og:type': website
    'og:title': 'Enscale WordPress Installation | Layershift KB'
    'og:description': 'To create a new environment with a manual installation of WordPress you will have to take the following steps: Deploy new environment Create a new environment with the desired resources: 2. The environment you create should have at least one application server (Apache,Nginx) and a database server (Mysql/Mariadb) 3. After the environment was created, you ...'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2024-03-04T10:09:10+00:00'
    'article:modified_time': '2024-03-04T14:33:37+00:00'
    'article:author': Layershift
published: true
---

To create a new environment with a manual installation of WordPress you will have to take the following steps:

## Deploy new environment

* Create a new environment with the desired resources:

![Enscale%20WordPress%20Installation-1](Enscale%20WordPress%20Installation-1.png)

* The environment you create should have at least one application server (Apache,Nginx) and a database server (Mysql/Mariadb)

![Enscale%20WordPress%20Installation-3](Enscale%20WordPress%20Installation-3.png)

![Enscale%20WordPress%20Installation-4](Enscale%20WordPress%20Installation-4.png)

* After the environment was created, you will receive an email with login credentials for the database server. Keep those at hand, as we will need them soon.

## Upload and deploy the WordPress archive

* Next, we will proceed to upload the WordPress archive to the server. You can download the default WordPress installer from [here](https://wordpress.org/latest.zip).

* In the lower left corner you will see the **Deployment Manager** option.

* Here, click the **Upload** button, and select the newly downloaded archive.

* From here, check the WordPress-master.zip archive, and click **Upload** as shown in the following images:

![Enscale%20WordPress%20Installation-5](Enscale%20WordPress%20Installation-5.png)

* After the archive was deployed successfully, in the top right corner you will be prompted with the following message. Please click the **Open in Browser** button.

![Enscale%20WordPress%20Installation-6](Enscale%20WordPress%20Installation-6.png)

## Configure WordPress

* Now we will proceed to create the database that will be used for the new **WordPress installation**.

* From the email you received, please select the one regarding the database server. It will contain a link to the database server, the user name (root) and the user password. Using these, please connect to the database server. From here, select the **Databases** tab on the top side, set the database name, and click **Create** as shown here:

![Enscale%20WordPress%20Installation-7](Enscale%20WordPress%20Installation-7.png)

* After the database was created, we will proceed to create a database user.

* To do so, we will have to click the database we created, and go to the privileges tab on the top bar. From here, click **Add User account** on the bottom left, and proceed to create the user. We strongly recommend you to use a unique username and a strong password (should contain uppercase letter, lowercase letters, numbers, special character).

![Enscale%20WordPress%20Installation-8](Enscale%20WordPress%20Installation-8.png)

* Now switch back to the WordPress installation page and connect the new database to the server using the following settings:

**Database Name:** the database name you created
**Username:** my_user
**Password:** password created for the mysql user
**Database host:** server name from email (node####-XXX.j.layershift.co.uk)

![Enscale%20WordPress%20Installation](Enscale%20WordPress%20Installation-9.png)

* Create the administrator username, and password. We strongly recommend you to use a unique username and a strong password (should contain uppercase letter, lowercase letters, numbers, special character)

![Enscale%20WordPress%20Installation-10](Enscale%20WordPress%20Installation-10.png)

Congratulations! You have successfully installed WordPress on your new Enscale Environment.


