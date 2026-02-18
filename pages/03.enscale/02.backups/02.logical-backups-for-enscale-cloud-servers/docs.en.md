---
title: 'Logical backups for Enscale Cloud Servers'
taxonomy:
    category:
        - docs
visible: true
aura:
    pagetype: website
    description: 'Tools and documentation for creating reliable logical backups of your MySQL, MariaDB, PostgreSQL, MongoDB and CouchDB on Enscale PaaS'
metadata:
    description: 'Tools and documentation for creating reliable logical backups of your MySQL, MariaDB, PostgreSQL, MongoDB and CouchDB on Enscale PaaS'
    'og:url': 'https://www.layershift.com/kb/enscale/backups/logical-backups-for-enscale-cloud-servers'
    'og:type': website
    'og:title': 'Logical backups for Enscale Cloud Servers | Layershift KB'
    'og:description': 'Tools and documentation for creating reliable logical backups of your MySQL, MariaDB, PostgreSQL, MongoDB and CouchDB on Enscale PaaS'
    'og:image': 'https://www.layershift.com/kb/user/images/ls-kb.jpg'
    'og:image:type': image/jpeg
    'og:image:width': 1200
    'og:image:height': 630
    'og:author': Layershift
    'article:published_time': '2026-02-18T11:08:31+00:00'
    'article:modified_time': '2026-02-18T11:08:31+00:00'
    'article:author': Layershift
---

We’ve explained the [difference between filesystem and logical backups](../overview-of-enscale-backups) in a Enscale backups overview and now we will provide links to documentation, tools and hints & tips regarding creating reliable logical backups on our Enscale Platform-as-a-Service.

The following types of data do not **usually** need additional logical backups as they can be reliably restored from Layershift managed backups in most cases:

* Most plain text data (e.g. scripts, logs, configuration files)
* Most binary data which is not changing during the backup process (e.g. images, videos)
* Your entire directory structure, ownership and permissions
* Databases which maintain consistency during filesystem without first stopping the server or locking and flushing tables (e.g. CouchDB)

If you are unsure if your data can be reliably backed up using filesystem backups (also commonly referred to as physical backups), please consult vendor documentation for the software you are using to identify recommended backup methods.

**Additional Note:** **In most cases we can restore your data reliably from our free filesystem backups** but in some cases you should consider whether it’s worthwhile creating your own logical backups too.

# Suggested logical backup tools and documentation

## MySQL / MariaDB backups

In the majority of cases, we can reliably restore MySQL / MariaDB databases from filesystem backups.

If you choose to take logical backups, be aware that most logical backup tools designed for MySQL or MariaDB can be used to backup both database servers.

* [MariaDB Backup and Restore Overview](https://mariadb.com/kb/en/backup-and-restore-overview/) (from MariaDB docs; includes mysqldump, mysqlhotcopy, XtraBackup)
* [MySQL Backup and Recovery](https://dev.mysql.com/doc/refman/5.5/en/backup-and-recovery.html) (chapter from MySQL Reference Manual)
* [MySQL Database Backup Methods](https://dev.mysql.com/doc/refman/5.5/en/backup-methods.html) (subsection of the chapter above)

In general, most data can be re-imported into any same version of MySQL / MariaDB, and in many cases can also be imported into newer versions of MySQL / MariaDB.

## PostgreSQL backups

When PostgreSQL is running with a write journal it is usually safe to rely upon filesystem backups, without creating any additional logical backups.

If you choose to take logical backups, the most commonly used tools for PostgreSQL are pg_dump and pg_dumpall:

* [PostgreSQL 18: Backup and Restore](https://www.postgresql.org/docs/18/backup.html) (chapter from PostgreSQL 18 manual)

## MongoDB backups

Sometimes it’s not possible for us to reliable restore MongoDB databases using physical backups. If you want to create reliable logical backups, you can do so by setting up replication and stopping the replicated database periodically so our filesystem backups can take a backup of it while the database is stopped, or alternatively you can create a logical backup.

The most common logical backup and restore method for MongoDB is using mongodump:

* [Backup and Restore with MongoDB Tools](http://docs.mongodb.org/manual/tutorial/back-up-and-restore-with-mongodb-tools/) (from MongoDB Manual)

## CouchDB backups

Backups of CouchDB should work just fine using our filesystem backups:

!!! Actually, you can copy a live database file from the OS at anytime without problem. Doesn’t matter if its being updated, or even if its being compacted, the CouchDB never-overwrite storage format ensures it should just work without issue.

# Tips and recommendations

* **Create logical backups as infrequently as possible** as they can use a lot of server resources (CPU / RAM / Disk I/O) which can increase your cloudlet usage and negatively impact your application’s performance.
* **Store logical backups locally** in your Enscale environment wherever possible as our filesystem backups will reliably take a copy of these (within a maximum of 6 hours of the backup file appearing, retained for 14 more days after you delete the backup file).
* **Rotate your logical backups** to minimise the amount of diskspace consumed by your Enscale environment and keep your costs low.
* Identify the **most appropriate backup method** for each aspect of your application rather than just the easiest to implement – it will save you time over the longer term.
* Consider the **difference between ‘hot’** backup methods (e.g. taking a backup while the database server is running) **and ‘cold’ backup methods** (e.g. taking a backup while the DB server is stopped) as the optimal method can vary depending on the type of database server used, how it’s configured and your business needs.
* **Only create logical backups of business critical data** (reduced resource consumption, faster backups).

If you are unsure if your data can be reliably backed up using filesystem backups (also commonly referred to as physical backups), please consult vendor documentation for the software you are using.