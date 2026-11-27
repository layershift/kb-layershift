---
title: 'Custom Images'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
metadata:
    'og:url': 'https://www.layershift.com/kb/managed-vps/docker/custom-images'
    'og:type': website
    'og:title': 'Custom Images | Layershift KB'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2026-08-14T17:01:15+01:00'
    'article:modified_time': '2026-08-14T17:01:15+01:00'
    'article:author': Layershift
---

## Customising Docker Images
Once you are comfortable with launching containers and stacks you may wish to customise your images. 

You can create a new image based on changes to an existing container by following [the steps outlined in the Plesk Documentation](https://docs.plesk.com/en-US/obsidian/administrator-guide/plesk-administration/using-docker.75823/#o77137)

!!!! We recommend to use a meaningful tag name instead of `latest` (the default) because what is `latest` today will soon become outdated over time... You might use an incrementing version number or something containing the creation date as example alternatives.

## Creating Your Own Docker Image
Creating your own Docker image involves writing a `Dockerfile`, and then `building` it. 

!!!! Docker images are composed in layers, meaning that it's normal for one image to inherit / be built upon another - so you don't need to start from scratch. However, be mindful that as well as inheriting someone else's work, you're inheriting their bugs and security vulnerabilities too!

Please refer to [Docker's Building images guide](https://docs.docker.com/get-started/docker-concepts/building-images/) for more details.
