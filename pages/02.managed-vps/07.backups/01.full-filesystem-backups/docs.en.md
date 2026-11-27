---
title: 'Full filesystem backups'
visible: true
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'Backing up hosting data is vital, so we take full filesystem backups on our Cloud VPS services included for free. See all benefits to learn more.'
metadata:
    description: 'Backing up hosting data is vital, so we take full filesystem backups on our Cloud VPS services included for free. See all benefits to learn more.'
    'og:url': 'https://www.layershift.com/kb/managed-vps/backups/full-filesystem-backups'
    'og:type': website
    'og:title': 'Full filesystem backups | Layershift KB'
    'og:description': 'Backing up hosting data is vital, so we take full filesystem backups on our Cloud VPS services included for free. See all benefits to learn more.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2025-04-11T16:32:12+01:00'
    'article:modified_time': '2025-04-11T16:32:12+01:00'
    'article:author': Layershift
---

We take full filesystem backups of each Managed VPS based on the backup package.

These backups comprise of your entire server filesystem, including everything inside your VPS – all files and directories, databases, emails, DNS records, configuration files including Plesk, etc.  We take backups at block-level to ensure the fastest possible backup time and no noticeable impact to performance.

# Benefits

* **Restore only required data**: Unlike many other providers, we can restore individual files/directories, databases, emails, configuration files, etc. without overwriting your entire VPS.
* **Highly efficient**: There is very low overhead when taking filesystem backups which means no noticeable impact to application performance.
* **Regular snapshots**: The highly sophisticated incremental backup mechanism reduces the amount of time necessary to create each individual recovery point.
* **Quick restores**: We can restore individual files or directories (without needing to restore any unnecessary additional data, such as log files, which can take much longer) and there is very low overhead, so we can restore backups very quickly.
* **Restore at any time**: Restores can be performed at any time, including while new backups are being taken.
* **Reliable database backups**: We have proven many times our ability to restore MySQL/MariaDB databases using these backups without any loss of data.

# Retention Period and Frequency

Backup Package | Silver | Gold | Titanium
--------- | --------- | -------- | ----------
Backup Frequency | Weekly | Daily | Every 4 hours
Backup Restore Points | 1-2 | 14 | 89 (tiered retention)
Backup Retention | 10 days | 14 days | 3 months (tiered retention)

!!! * There are **no storage limits** or additional storage fees.
!!! * All backups are covered by our robust Managed Hosting SLA

!!!! * For your security, filesystem backups are stored on a secure, high-speed, private backup network.
!!!! * For added redundancy, a second copy is made on an off-site immutable (cannot be altered or deleted) storage.

# Restoring from backups

Backup restoration is available free of charge 24x7x365, with each incident managed by our support team to ensure the fastest and most successful recovery (in many cases our engineers can help to fix minor issues, avoiding the need to restore from backup).

If you need a restore, simply [open a support ticket](https://help.layershift.com) as normal and let us know:
* Which files and/or databases need to be recovered
* The approximate time that an incident occurred, or the site was last known working
* A brief description of the problem
* Your most recent invoice number to validate the authenticity of your request as the server owner
