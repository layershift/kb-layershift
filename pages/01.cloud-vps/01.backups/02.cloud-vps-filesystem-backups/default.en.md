---
title: 'Cloud VPS full filesystem backups'
---

We take full filesystem backups of our Cloud VPS hosting services at least once every 6 hours (and as often as hourly if you request this on our [Enterprise Care Pack](http://www.layershift.com/about/care-packs)).

These backups comprise of your entire server filesystem, including everything inside your VPS – all files and directories, databases, emails, DNS records, configuration files including Plesk, etc.  We take backups at block-level to ensure the fastest possible backup time and no noticeable impact to performance.

##### {c:#27739a} Benefits of the full filesystem backups {/c}


* **Restore only required data**: Unlike many other providers, we can restore individual files/directories, databases, emails, configuration files, etc. without overwriting your entire VPS.
* **Highly efficient**: There is very low overhead when taking filesystem backups which means no noticeable impact to application performance.
* **Regular snapshots**: The highly sophisticated incremental backup mechanism reduces the amount of time necessary to create each individual recovery point.
* **Quick restores**: We can restore individual files or directories (without needing to restore any unnecessary additional data, such as log files, which can take much longer) and there is very low overhead, so we can restore backups very quickly.
* **Restore at any time**: Restores can be performed at any time, including while new backups are being taken.
* **Reliable database backups**: We have proven many times our ability to restore MySQL/MariaDB databases using these backups without any loss of data.

**Layershift backups are included free of charge** in accordance with the Care Pack you are using (Essential is included free of charge with our Cloud VPS range, Enhanced is included free of charge with our Cloud VPS Extreme range):



<table style="width:100%; margin-left:auto;margin-right:auto">
<thead>
<tr><th>Care Pack:</th>
<th>Essential</th>
<th>Enhanced</th>
<th>Enterprise</th>
</tr>
</thead>
<tbody>
<tr><td>Backup Frequency</td>
<td>Every 6 hours</td>
<td>Every 6 hours</td>
<td>Up to hourly</td>
</tr>

<tr><td>Full Backup Restore Points</td>
<td>28</td>
<td>56</td>
<td>56-336</td>
</tr>

<tr><td>Backup Retention</td>
<td>7 days</td>
<td>14 days</td>
<td>14 days</td>
</tr>
</tbody></table>


There are **no storage limits** and all backups are covered by our robust [Managed Hosting SLA](http://www.layershift.com/legal/ManagedHostingServiceLevelAgreement.pdf).

<span class="highlight"><b>For your security, we store all filesystem backups on a secure, high-speed private backup network which is completely isolated from the rest of the platform.</b></span>

##### {c:#27739a} How do I request a restore of Layershift backups? {/c}

**Restores of filesystem backups are available free of charge 24x7x365** via our support team who manage the process for you to ensure the fastest and most successful recovery. Unlike many of our competitors, we can restore individual files or directories, instead of overwriting your entire environment – this means restores are fast and flexible (e.g. you choose if we should overwrite existing files or restore to a separate location).

If you need a restore, simply open a [support ticket](https://www.layershift.com/support/) and let us know which files need to be restored and approximately which recovery point (from the last 2 weeks) and our support team will begin right away.