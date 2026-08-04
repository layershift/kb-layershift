---
title: 'Docker Containers on Plesk'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://www.layershift.com/kb/managed-vps/docker/docker-on-plesk'
    'og:type': website
    'og:title': 'Docker Containers on Plesk | Layershift KB'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2026-06-24T18:46:05+01:00'
    'article:modified_time': '2026-06-24T18:46:05+01:00'
    'article:author': Layershift
media_order: 'OS_Panel.png,Extension Installation.png,Image_Selection.png,Image Version.png,AutoMemoryName.png,Volume Mappings.png,variablesPortsandVolumes.png,stack.png,demo-stack.png,container_settings.png,port_clash.png,restartcontainer.png,stack removal.png,COntext.png,ValkeySearch.png,ValkeyVersion.png,valkeyMemoryLimits.png,ValkeyENV.png,volumes.png,lb-recreate.png,UploadImage.png,RunLocal.png'
page-toc:
    active: true
---

Setting up a Dockerised container might seem complicated, but with Layershift and Plesk it's extremely easy!

### Prerequisites
 
You're likely to need at least 512MiB of free RAM per container, but this may need to be higher depending on workload and image. Keep in mind that each Docker container adds to the overall resource requirements for your server. You can upgrade resources easily at any time; just reach out to our Support team if you need to add more!

Every Layershift VPS includes regular automated backups. The entire server filesystem is backed up on a frequency and retention scheduled according to your server's backup plan, but depending on your particular Docker image you might want to make additional arrangements, for example some database containers may not be properly restorable from a filesystem backup.

Although this article will help you to get set up using Docker on Plesk, we recommend that you also read the [Plesk Documentation](https://docs.plesk.com/en-US/obsidian/administrator-guide/plesk-administration/using-docker.75823/#setting-up-nginx-to-proxy-requests-from-domains-to-a-container) on the topic for additional context and guidance. 

If you run into any issues along the way, our [24/7 Helpdesk will be happy to assist](https://help.layershift.com), but please note the [Support Scope](#support) section below.
 

## Installation
Docker comes pre-installed on all Layershift Plesk servers, so no need for installation. Just look to the left hand panel and you should see an option labelled Docker.   
   
If you are unable to see the extension, please contact our [helpdesk](https://help.layershift.com).


### Image Selection
Go to the Docker option in the left hand panel, then Run Container.

By default, Docker image search pulls images from [Docker Hub](https://hub.docker.com/), but you can also search other registries provided they're compatible with the `docker search` command (not all registries are) - for example `quay.io/keycloak/keycloak` will get you Keycloak from the Quay.io registry, whilst simply entering `valkey` will get you Valkey from Docker Hub.

Search for your desired application image > Select specific image > Select version. 
      
Below you can see the image results with the chosen option highlight in purple.      
   ![Valkey image search results, with the selected image highlighted in purple](ValkeySearch.png "ValkeySearch")


!!! We recommend to avoid `latest` and prefer named version tags instead (to easily identify which version you have deployed later).
	   
   ![Image tag search results including both numbered, named and latest versions](ValkeyVersion.png "ValkeyVersion")


#### Upload Image

If you have your own custom image, the image resides in an unsupported registry (one that doesn't support `docker search`), or in a private registry, you can upload an image created with [`docker save`](https://docs.docker.com/reference/cli/docker/image/save/) directly to the server:
 
Click on the Images tab, and then the Upload image button.
 
![Screenshot of the Plesk Docker extension. The Images tab is selected, and the Upload Image button at the top of that section is highlighted.](UploadImage.png "UploadImage")

Choose the file from your computer, and click Upload to add it to the list of local images stored on your server.

! Keep in mind that these images consume your VPS disk space, and can quickly add up (especially if you have multiple tags within each image).

Once the image is uploaded, you can run it by pressing the Run button as highlighted below:

![Screenshot showing highlighted run local play button from the Valkey search](RunLocal.png "RunLocal")



### Memory Limits and Autostart
We now set the container name, any desired memory_limits and auto restart. These are shown in the image below with the memory_limit set to 1024Mb and auto-restart activated.

![Screenshot of the container name prod-valkey-cache, a set memory_limit of 1024Mb and auto-restart tick box checked](valkeyMemoryLimits.png "valkeyMemoryLimits")


## Mapping
### Port Mapping

By default, Automatic port mapping selects an available host port for you. This is the recommended option for most deployments, as it helps avoid port conflicts.

Disable Automatic port mapping only if you need your container to be available on a specific host port. When using manual mapping, you can specify both the container port and the host port, and choose whether the port is accessible from the internet. The service is always accessible from the server itself (127.0.0.1).

!! If the host port you choose is already in use by another service or container, the container will fail to bind to that port. This is known as a port conflict. If this happens, select a different host port or enable Automatic port mapping.

A demonstration of resolving port conflicts is provided later in this guide under Domain Proxying.

Choosing a Host Port

If you are manually assigning a host port:

* Use the standard port expected by your application where possible (for example: 3036 for MySQL, 5432 for PostgreSQL, 6379 for Valkey etc.).
* If that port is already in use, choose another unused registered port (1024 - 49151).
  * Avoid well-known system ports (0 - 1023) and dynamic/ephemeral ports (49152 - 65535).
* On servers running other software, some ports are commonly already in use. For example, on a Plesk server, ports 3306 and 8443 are typically unavailable.

### Volume Mapping
By default, data written or changed inside your Docker container is **not persistent**! For some containers that's perfect, but for most you'll have at least *some* data that you want to keep hold of (e.g. if you're running a database server, you want to keep the files that represent the actual database).

A Docker volume is a directory on your server that you mount to a directory inside the container. The container can read and write to that directory, but cannot access anything above it (such as its parent directory).

! You must use absolute paths for the Host and Container volume paths

!!!! We recommend to save all of your Docker volumes under `/var/lib/docker/volumes` (which is their usual location) on the server (Host) side.

In the example below, we mount a server directory at `/var/lib/docker/volumes/valkeycache` to `/var/lib/valkey` inside the container, which allows us to retain the `/var/lib/valkey` data across Valkey redeploys (e.g. updating Valkey version).

![Screenshot of volume mapping with server directory /var/lib/docker/volumes/valkeycache on the left and container directory /var/lib/valkey on the right. There is a blank entry showing greyed out text with Host on the right and Container on the left](volumes.png "volumes")

!!! Docker volumes are excluded from backups created by Plesk's own backup tools; but your entire Layershift Managed VPS (including any Docker volumes) is backed up according to your selected [backup plan](../backups/full-filesystem-backups#retention-period-and-freq).

### Environmental Variables
Below you can examples of port, volume and environmental variable mapping.

![Screenshot showing Automatic Mapping in unticked, Manual Mapping set to port 6379 on both host and container with the port being inaccessible from the internet. Volume mapping, as per the above image. Various common Environmental Variables within generic values to demonstrate purpose](ValkeyENV.png "ValkeyENV")



## Docker-compose

Should you wish to run a docker-compose.yaml file and setup a whole stack like the below. There are multiple ways you can upload your compose file.

![Screenshot of a sample stack, including an NGINX load-balancer, 2 Apache application containers and a Postgres database container](stack.png "stack")

Click on Add Stack or the blue plus shown in the image above.
 
You can paste, upload or select the file depending upon your needs. Set the name, it must be in lower case but can container '-' and numbers

### Troubleshooting
If your Stack doesn't launch smoothly:
Review the docker compose up output

!!!! You can re-deploy an existing Stack via the vertical ellipsis (kebab menu) icon

Start the problem container (if it fails to start it may output an error)

Review the container's console log

#### Port Conflicts
One possible scenario, especially with third party Docker Compose files - since they don't know the rest of your setup, is that your Docker Compose is attempting to use a port that's already in use by another service or container.
 
![Screenshot of the load balancer container in the stacked, it is in a Stopped state](container_settings.png "container_settings")
 
We can see in the image above that the container is stopped, and by going into the highlighted Settings we can edit the container and fix it.
 
![Screenshot of Manual Mapping port entries and both options are set to 80](port_clash.png "port_clash")
 
We can see that there is a clash since something is already using port 80. So we can edit to a different port, save and restart the container. Click on Stopped and select Start.
 
If it fails, you will receive an error message in the top right corner of your dashboard.
 
![Image showing the Stopped state and the Start state of containers](restartcontainer.png "restartcontainer")
 
 
  
##   Firewall and Domain Proxy
### Firewall Checks

Please refer to [Plesk Documentation](https://docs.plesk.com/en-US/obsidian/administrator-guide/plesk-administration/plesk-for-linux-the-plesk-firewall.72046/) regarding firewall management.

Note that if a container is NOT set to "Make the port inaccessible to the internet" it will be accessible from the internet on that port, including if you have that port blocked in the firewall.

If you set the container port to be accessible, it creates the firewall rule for you. But we recommend that you check on the rule and confirm the correct port is open.

### Domain Proxying

Domain proxying is an extremely useful feature of Plesk Docker.

You can have all or part of your website served from a container.

This is achieved by having NGINX forward the URL to a mapped external container port.

For more information on setting this up, [please see the extensive Plesk documentation on the steps](https://docs.plesk.com/en-US/obsidian/administrator-guide/plesk-administration/using-docker.75823/#setting-up-nginx-to-proxy-requests-from-domains-to-a-container).

Please note that the above is for setting up docker as the site root.

Should you wish to only have a part of your website hosted through docker, for example a members area or for different departments, this can be quite easily achieved but does require some finesse.
example.com could take you to the home page, you can then have example.com/singapore or example.com/members
Since Plesk allows for the easy setup of subdomains, you can even have a container for accounting.example.com/compliance.

Where this can really shine is when combined with the previously mentioned Docker Stack. Behind the subdirectories listed above, you can have entire docker clusters and essentially a wholly different website including separate database.

To do this, setup a docker stack according to the instructions above, however you must include a mapped volume on the web facing container with the below within your yaml. Please note that since the yaml file will be contained in the directory "/usr/local/psa/var/modules/docker/stacks/your-stack-name/" you can have a relative path for the server side.

> volumes:
>       - ./nginx.conf:/etc/nginx/nginx.conf
      
Once your stack is started, delete ""/usr/local/psa/var/modules/docker/stacks/your-stack-name/nginx.conf". Since this did not exist at the time of the stacks creation, Docker helpfully made a directory there, but we need an nginx.conf file to redirect from the domains subdirectory to root within the stack. Therefore once you have removed the erroneously created folder, you will need to add a file there containing something similar to the below.  Upstream is required to point to application servers behind a load balancer, and in the case below the site would be example.com/dockertest/

> events { worker_connections 1024; }
> 
> http {
>     upstream my_apps {
>         server app-node-1:80;
>         server app-node-2:80;
>     }
> 
>     server {
>         listen 80;
> 
>         location /dockertest/ {
>             proxy_pass http://my_apps/;
>             proxy_set_header Host $host;
>             proxy_set_header X-Real-IP $remote_addr;
>             proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
>             proxy_set_header X-Forwarded-Proto $scheme;
>         }
>     }
> }
  
  
When that file is in place, recreate your web facing container.

![Screenshot of NGINX lb container details, with the hamburger many highlighted in purple and the Recreate button higlighted in green](lb-recreate.png "lb-recreate")

Et voila! You now have part of your website hosted on docker and completely separate from the rest of your website, this is excellent for both reducing attack surface, defense in depth as well as any operational considerations.

##  Removal
  
Stopping or removing a stack can be done through the highlighted button below.
  
![Screenshot of the demo-stack details, with purple highlighted hamburger menu showing the options Deploy, Watch, Stop and Destroy](stack%20removal.png "stack%20removal")


## Portainer

[Portainer](https://docs.portainer.io/) hides the complexity of managing containers behind an easy-to-use UI. By removing the need to use the CLI, write YAML or understand manifests, Portainer makes deploying apps and troubleshooting problems so easy that anyone can do it.
  
##   Support
Due to the extremely large number of images and versions available, we do not offer support for internal container issues.

We do offer support for the setup of Docker on Plesk, Plesk and server related issues you may experience while installing and operating your containers.
  
##   License

You do not need a license to manage the local Docker service running on your Layershift Plesk server.

A paid license option is available to enable you to manage Docker containers hosted on multiple different servers from a single interface (please contact billing@layershift.com for assistance), but managing containers hosted locally by a single Layershift Managed VPS is included at no additional cost.

# Going Further

## Customising Docker Images
Once you are comfortable with launching containers and stacks you may wish to customise your images. 

You can create a new image based on changes to an existing container by following [the steps outlined in the Plesk Documentation](https://docs.plesk.com/en-US/obsidian/administrator-guide/plesk-administration/using-docker.75823/#o77137)

! We recommend to use a meaningful tag name instead of `latest` (the default) because what is `latest` today will soon become outdated over time... You might use an incrementing version number or something containing the creation date as example alternatives.

## Creating Your Own Docker Image
Creating your own Docker image involves writing a `Dockerfile`, and then `building` it. 

!!!! Docker images are composed in layers, meaning that it's normal for one image to inherit / be built upon another - so you don't need to start from scratch. However, be mindful that as well as inheriting someone else's work, you're inheriting their bugs and security vulnerabilities too!

Please refer to [Docker's Building images guide](https://docs.docker.com/get-started/docker-concepts/building-images/) for more details.
