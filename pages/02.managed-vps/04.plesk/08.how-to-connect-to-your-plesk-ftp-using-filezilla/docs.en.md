---
title: 'How to connect to your Plesk FTP server'
visible: true
media_order: 'How to connect to your Plesk FTP server - base.png,How to connect to your Plesk FTP using Filezilla - Certificate.png,How to connect to your Plesk FTP using Filezilla - Sites Manager.png'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'Learn how to connect to your Plesk FTP server using Filezilla FTP client.'
metadata:
    description: 'Learn how to connect to your Plesk FTP server using Filezilla FTP client.'
    'og:url': 'https://www.layershift.com/kb/managed-vps/plesk/how-to-connect-to-your-plesk-ftp-using-filezilla'
    'og:type': website
    'og:title': 'How to connect to your Plesk FTP server | Layershift KB'
    'og:description': 'Learn how to connect to your Plesk FTP server using Filezilla FTP client.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2025-07-10T13:37:30+01:00'
    'article:modified_time': '2025-07-10T13:37:30+01:00'
    'article:author': Layershift
menu: 'Connect to FTP server'
---

To get started you need to identify the connection parameters first. FTP connection requires user, password and a host to connect to.

# Identify your FTP user/pass

FTP users are subscription specific. These can be handled in Plesk, in the subscription’s  FTP access section.

You can create new FTP users here, you can reset the passwords, you can delete FTP users , except the main user.

![Plesk FTP users](How%20to%20connect%20to%20your%20Plesk%20FTP%20server%20-%20base.png)
# Establish the FTP host

FTP protocol establishes the permissions and location on the server based on username and password. Given that it is unimportant what you use for Host, as long as it resolves to the server.

You can use the IP, the domain name, FTP subdomain name and so on. Ideally you could use the VPS hostname as its certificate will always be valid.

In case of Filezilla this is unimportant, because it follows the Trust On First Use model.

# Set up the FTP connection with Filezilla
![Filezilla Sites Manager](How%20to%20connect%20to%20your%20Plesk%20FTP%20using%20Filezilla%20-%20Sites%20Manager.png)

Once you hit the Connect ,  Trust On First Use kicks in and you will have to accept and store the certificate :

![Filezilla Certificate Prompt](How%20to%20connect%20to%20your%20Plesk%20FTP%20using%20Filezilla%20-%20Certificate.png)

# Potential problems and solutions

* Time-out problems. The VPS has several firewalls, active and passive firewall, you router capability may be limited, in either case please contact support. They will be able to determine the cause and adapt the FTP/firewall for your needs. When submitting the ticket it is ideal to include the Filezilla log.

* Upload corruption. This is rarely the case, but you can play around with binary/ascii setups in Filezilla > Transfer > Transfer Type. If you contact support they can establish from the logs which type you have to use specifically.

* Expired / outdated certificate: By default, Plesk enforces FTPS, which requires a working SSL certificate on the destination host. The simplest solution is to use the VPS host name, as its certificate is configured to automatically renew itself before expiring.

* FTPS and Windows explorer: Windows explorer does not have FTPS capabilities; it is recommended to use a dedicated FTP client like Filezilla to ensure that the connection is secure.
