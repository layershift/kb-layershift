---
title: 'Website staging with Plesk Obsidian'
media_order: 'Screenshot from 2023-07-23 08-07-13.png,Screenshot from 2023-07-29 07-12-08.png,Screenshot from 2023-07-29 07-22-47.png,Screenshot from 2023-07-29 07-14-13.png,Screenshot from 2023-07-29 07-19-16.png,Screenshot from 2023-07-29 07-07-46.png,Screenshot from 2023-07-23 08-10-29.png,Screenshot from 2023-07-23 08-16-35.png,Screenshot from 2023-07-29 07-04-22.png,Screenshot from 2023-07-29 07-06-30.png,Screenshot from 2023-07-23 07-31-53.png,Screenshot from 2023-07-23 07-32-54.png,Screenshot from 2023-07-23 07-39-23.png,Screenshot from 2023-07-23 07-45-55.png,Screenshot from 2023-07-23 07-42-04.png'
---

# Website staging with Plesk Obsidian  

All good developers know it’s important to test your code before publishing it to live, and the easiest way to do this is using a website staging environment. This allows you to ensure your code is stable and tested, to prevent unwanted outages due to glitches which can affect your users and cost your business money.  Plesk Panel allows you to setup a website staging environment to check that everything runs smoothly before pushing your code into production.  

### The action plan  

Before proceeding with this you should decide where you want to host the staging environment. You have three options: use the same webspace, create a new one or upload it to an FTP account on another server.  

#### 1. Host it in your current webspace  

If you decide to host the staging website in the same webspace you will need to first create a new domain or a subdomain. We will quickly guide you through these steps.  

##### Creating a new domain  

To add a new domain to your existing webspace simply go to `Websites & Domains` and select `Add Domain`:  

![Screenshot%20from%202023-07-23%2007-31-53](Screenshot%20from%202023-07-23%2007-31-53.png "Screenshot%20from%202023-07-23%2007-31-53")

Next, as a way of creating the website, click on `Blank website` and then select which domain name you wish to use, choose the correct webspace in case there are multiple ones and set up hosting type and settings depending on your needs.

![Screenshot%20from%202023-07-23%2007-32-54](Screenshot%20from%202023-07-23%2007-32-54.png "Screenshot%20from%202023-07-23%2007-32-54")

##### Creating a subdomain

If you already possess a domain, it's a straightforward process to add a new subdomain to it and employ it for testing purposes (e.g., staging.yourdomainname.com or something similar). To create this new subdomain, access the Websites & Domains section and choose the option to Add Subdomain.

![Screenshot%20from%202023-07-23%2007-39-23](Screenshot%20from%202023-07-23%2007-39-23.png "Screenshot%20from%202023-07-23%2007-39-23")

Once arrived at this step, make sure that the **Parent domain** filed is set on the desired domain and set the desired subdomain name:

![Screenshot%20from%202023-07-23%2007-42-04](Screenshot%20from%202023-07-23%2007-42-04.png "Screenshot%20from%202023-07-23%2007-42-04")

#### 2. Use a separate webspace on the same server

Go to `Websites & Domains` and select `Add Domain`:

![Screenshot%20from%202023-07-23%2007-31-53](Screenshot%20from%202023-07-23%2007-31-53.png "Screenshot%20from%202023-07-23%2007-31-53")

Enter the name of your domain and opt for creating a new webspace. You may choose an IP address to host the domain (though it's not mandatory, as you can safely use the same IP). Provide your preferred login credentials (or stick with the automatically generated ones), which will grant you FTP and SSH access.

![Screenshot%20from%202023-07-23%2007-45-55](Screenshot%20from%202023-07-23%2007-45-55.png "Screenshot%20from%202023-07-23%2007-45-55")

### Copy the website

Now that you’ve decided on the location of your staging environment and configured it, the next step involves copying everything from the production environment to the staging environment. This can be achieved by following the subsequent steps:

#### How to copy your website's files?

1. Go to the **Websites & Domains**, find the website you want to copy, then select **Website Copying**.

![Screenshot%20from%202023-07-23%2008-07-13](Screenshot%20from%202023-07-23%2008-07-13.png "Screenshot%20from%202023-07-23%2008-07-13")

2. Select the file destination option:

   * Website in Plesk:
	
	Choose the target domain for the copy from the provided list of site names in the dropdown menu. You have the option to retain or delete any pre-existing files on the destination server 		before the copy process. However, it's essential to be aware that if there are any files with identical names on the destination server, they will always be replaced during the copying process.
    
    ![Screenshot%20from%202023-07-23%2008-10-29](Screenshot%20from%202023-07-23%2008-10-29.png "Screenshot%20from%202023-07-23%2008-10-29")
    
   * On another server, using the FTP storage option. 
   
   In this case, you need to specify the server’s host name and credentials for connecting to the external FTP account.

   ![Screenshot%20from%202023-07-23%2008-16-35](Screenshot%20from%202023-07-23%2008-16-35.png "Screenshot%20from%202023-07-23%2008-16-35")
		
   Use the Active mode option in the FTP connection method field. If you can’t manage to connect to the external FTP account, try again with the Passive mode enabled.

#### Don't forget about your databases!

If your website relies on a database, it's necessary to copy it to the staging environment. To accomplish this, please follow the provided instructions:

* Select `Databases` from the left main menu:

![Screenshot%20from%202023-07-29%2007-04-22](Screenshot%20from%202023-07-29%2007-04-22.png "Screenshot%20from%202023-07-29%2007-04-22")

* Choose the Webspace where your website is hosted:

![Screenshot%20from%202023-07-29%2007-06-30](Screenshot%20from%202023-07-29%2007-06-30.png "Screenshot%20from%202023-07-29%2007-06-30")

* Find the database(s) you need to copy and click the `Copy` icon:

![Screenshot%20from%202023-07-29%2007-07-46](Screenshot%20from%202023-07-29%2007-07-46.png "Screenshot%20from%202023-07-29%2007-07-46")

* Next, you’ll need to choose the destination of the database copy

	 * If your want to copy the database to a new or existing database on the same server, select the destination server, Webspace and enter a new database name or select from existing 		databases:

	**Additional Note** : We recommend you use the “create a full copy box” if you want the full database copied, or deselecting this option if you only want the database structure to be copied (such as if you are planning to populate the database with test data).
	
	![Screenshot%20from%202023-07-29%2007-12-08](Screenshot%20from%202023-07-29%2007-12-08.png "Screenshot%20from%202023-07-29%2007-12-08")

	* If you want to publish the database to a separate server, you will need to specify the host name (or IP address) of the remote server to create the new database or overwrite an existing database:
    
	![Screenshot%20from%202023-07-29%2007-14-13](Screenshot%20from%202023-07-29%2007-14-13.png "Screenshot%20from%202023-07-29%2007-14-13")

* Once you click the `Ok` button, the database copying process will start immediately.

* Once the copy has completed, you should modify your site’s scripts in the website staging environment so they connect to the copied database, such as by modifying connection strings to connect to a new database name, username and password.

### From website staging to production

When the site copy in the staging environment is updated and ready to go live, you can publish it:

* Access `Plesk Dashboard` and click on `Website & Domains` tab:

![Screenshot%20from%202023-07-29%2007-19-16](Screenshot%20from%202023-07-29%2007-19-16.png "Screenshot%20from%202023-07-29%2007-19-16")

* Locate the address of your production site in the list of domains, access `Hosting Settings` and update the document root directory with the one of the staging site:

![Screenshot%20from%202023-07-29%2007-22-47](Screenshot%20from%202023-07-29%2007-22-47.png "Screenshot%20from%202023-07-29%2007-22-47")

All the modifications you have implemented on the site are now accessible and visible to external users.


 
