---
title: 'Overview of Enscale backups'
taxonomy:
    category:
        - docs
aura:
    pagetype: website
    description: 'Ensure your data can be reliably backed up using a combination of automated Enscale backups and periodic logical backups.'
metadata:
    description: 'Ensure your data can be reliably backed up using a combination of automated Enscale backups and periodic logical backups.'
    'og:url': 'https://www.layershift.com/kb/enscale/backups/overview-of-enscale-backups'
    'og:type': website
    'og:title': 'Overview of Enscale backups | Layershift KB'
    'og:description': 'Ensure your data can be reliably backed up using a combination of automated Enscale backups and periodic logical backups.'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2026-02-18T11:07:01+00:00'
    'article:modified_time': '2026-02-18T11:07:01+00:00'
    'article:author': Layershift
---

The main purpose of this article is to explain how our Enscale backups work and to provide hints and suggestions to ensure your data can be reliably restored.

To understand this topic it is important to understand the difference between filesystem and logical backups:

# Filesystem backups (managed by Layershift)

Our standard managed backup service performs regular filesystem backups – this takes backups of your Enscale filesystem, including all files and directories inside each of your environments. Backups are made by taking a block-level copy of the filesystem without needing to understand the file content to be able to reliably restore its data.

## Benefits

  * **Highly efficient:** There is very low overhead when taking filesystem backups which means no noticeable impact to application performance.
  * **Regular snapshots:** The highly sophisticated incremental backup mechanism reduces the amount of time necessary to create each individual recovery point.
  * **Quick restores:** We can restore individual files or directories (without needing to restore any unnecessary additional data, such as log files) and there is very low overhead, so we can restore backups very quickly.
  * **Restore at any time:** Restores can be performed at any time, including while new backups are being taken.

## Limitations

  * **Databases:** Reliable filesystem backups of databases can sometimes only be taken when the database server is either not running or is temporarily locked and connections flushed during the backup process. We cannot stop your database during every backup as availability is critical to most of customers so we recommend that you take your own periodic logical backups of any critical data (see below for details) to ensure it can be reliably restored.
   **Additional Note:** Simply locking tables and flushing connections may not be enough in some cases, for example, [PostgreSQL manual recommends fully stopping the database server before taking a filesystem backup](https://www.postgresql.org/docs/current/backup-file.html))
  * **Non-portability:** These backups can only typically be restored onto the same platform and software stack versions.

**Layershift** take filesystem backups **4 times per day** and keep them for **14 days**, offering **56 individual restore points**. These backups are included free of charge, without any storage limits and are also covered by our robust [Enscale PaaS SLA](https://www.layershift.com/legal/). For your security, we store all filesystem backups on a secure, high-speed private backup network which is completely isolated from the rest of the platform.

## How do I request a restore of Layershift backups?

Restores of filesystem backups are available free of charge 24x7x365 via our support team who manage the process for you to ensure the fastest and most successful recovery. Unlike many of our competitors, we can restore individual files or directories, instead of overwriting your entire environment – this means restores are fast and flexible (e.g. you choose if we should overwrite existing files or restore to a separate location).

If you need a restore, simply open a [support ticket](../../../support) and let us know which files need to be restored and approximately which recovery point (from the last 2 weeks) and our support team will begin right away.

## How long does a restore take?

The restore process typically involves 2 steps:

1. Restore the relevant node(s) within our backup system
2. Copy the required data from the restored nodes to your live nodes

The time required for step 1 depends on the amount of data stored on the node being restored, whilst the time required for step 2 can vary substantially depending on the type of data being recovered (e.g. database restores require an SQL dump, copy to the destination node, and SQL import).

Overall, a typical ballpark guide is about 1 hour per 100GB of data.

# Logical backups using native tools (managed by you)

A logical backup is a backup taken using native tools designed to read logical data (e.g. a database ‘SELECT’) and to output it in a logical format (e.g. an SQL dump) including additional information (e.g. database schemas). This allows you to restore the data on any system that understands the backup format, sometimes including other types of servers (simple SQL without any server-specific information can usually be imported into any SQL-aware database server).

As an example, ‘mysqldump’ is a popular tool used to create logical backups of MySQL / MariaDB databases. Each logical backup contains all of the information necessary to reliably re-import your data into any other MySQL or MariaDB server running the same or a higher version.

## Benefits

  * **Using native tools:** Using native tools designed for backing up a specific type of data will usually give you the most reliable, efficient and complete backups of the data you can take – this allows you to easily perform a full or partial restore.
  * **Best practice:** As these tools are developed by experts in their field, they usually offer several best-practice methods to perform backups and include accurate official and community documentation explaining the differences.
  * **Reliability:** Backups can usually be restored to any system using the same or newer versions of the software you backed up (e.g. MySQL 5.1 dumps taken using mysqldump can be reliably restored to MySQL / MariaDB 5.5).
  * **Flexibility:** Logical backups are flexible as you can backup only the data you require (e.g. specific database tables) and they can be taken at any time you desire (e.g. right before you perform a major software update, or to ensure there is no costly disruption during peak business periods).

## Limitations

  * **Performance**: These backups are usually taken by querying the server software storing the data (such as MongoDB) which can add significant extra overhead when compared to our filesystem backups, thus resulting in less efficient backups – these perform much slower as the server software usually needs to convert the data before output.
  * **Diskspace**: Logical backups usually take more diskspace than a filesystem backup, so you should consider how frequently you take these and the number of restore points to keep.
  * **Complexity**: Before performing a logical backup it is important to decide on the most appropriate type of tool to use and how to use it. For example, when backing up InnoDB tables in MySQL / MariaDB a full table scan is performed which can fill your buffer pool with the entire contents of all of your tables and so it’s important to consider your server configuration to ensure this does not occur or is handled in a controlled manner.


To help you identify a suitable logical backup tool, please see our related article “[Logical backups for Enscale Cloud](../logical-backups-for-enscale-cloud-servers)“.

## Where to store logical backups

We recommend storing logical backups locally in your Enscale environment for several reasons:

  * **Retention:** Our automated filesystem backups will take a copy of any logical backup stored inside your environments within a maximum of 6 hours and keep this for 14 days – we can easily restore this to any of your environments upon request and you can then re-import it into your database software.
  * **Reliable:** As your logical backup file doesn’t change once created, it can be backed up reliably by our automated filesystem backups.
  * **Security:** Your data remains within our secure private backup network, no additional encryption is necessary to keep your data secure.
  * **Efficient:** Creating backups locally is much faster than creating backups over a network connection – this can reduce the server resources (CPU & RAM) needed to perform the backup and ensure your application runs with minimal performance degradation as the backups complete more quickly.
  * **No traffic charges:** You will incur no additional traffic charges which could otherwise be incurred when transferring data elsewhere.

## Example

You take a weekly logical backup of your MariaDB database using ‘mysqldump’ and store this in your Enscale environment; within 6 hours your entire environment is backed up by our automatic backup system, including your logical backup. If you require a restore within 14 days of deleting the logical backup file from your environment we can restore your mysqldump as a file in any of your environments which you can safely re-import into virtually any version of MariaDB or MySQL.

**Additional Note:** Filesystem backups in combination with periodic logical backups offer a very high success rate for restoring any data.

Don’t forget to read our related article, “[Logical backups for Enscale Cloud Servers](../logical-backups-for-enscale-cloud-servers)“ for some suggested logical backup tools and some hints & tips.
