# User Documentation
While developing 

## Backing Up WordPress
WordPress has two major components -- the website files and the WordPress database. Although WordPress website files are required for WordPress to function at all, your personal WordPress website data is stored inside of the WordPress database. Losing the files for WordPress can cause your website to be down for an extended period of time; however, losing your WordPress database means your website is lost forever if you do not have a backup of the database or can somehow restore the database.

**Having a plan for backing up WordPress is extremely important. It is possibly more important than keeping WordPress secure in the first place. Even though your hosting provider may keep automatic backups, it is best to have multiple different backups from different time periods stored in different places. Ultimately, you are responsible for how well you backup your WordPress website.**

It's best practice to store backups in a different location than your site itself so they're not lost if something happens to the server. Let's look at a few options for managing backups.

### Manual Backups
The most basic way to backup your site is to manually create copies of its database and files, and then download them. You can make a `.zip` archive for the files and a `.sql` export for the database. They can be downloaded directly to your local machine or stored somewhere safe, like in cloud storage. [Creating Manual WordPress Backups](https://codex.wordpress.org/WordPress_Backups#Backing_Up_Your_WordPress_Site)

### Backup via Plugin
There are many WordPress plugins that will create backups for you automatically if you are not comfortable doing so manually. Again, remember to download the backups from your server once they are created. [WordPress backup plugins can be easily found by searching the plugin directory](https://wordpress.org/plugins/search.php?q=backup).

### Backup Services
There are also services that will take care of creating, downloading, and storing backup files for you. Most of these services have a cost but are typically reliable and easy to use.

### Backups and Hacked Websites
Backups are an extremely important part of recovering after a website has been attacked and altered by a malicious user. **Restoring from a clean backup predating the time a hack occurs is the only way to guarantee that there are no remaining malicious files and that there are no leftover changes to good files that could enable further attacks.**

#### Cautions About Automatic Backups
Many WordPress backup plugins provide automatic backups. Automating backups can make keeping a recent backup of WordPress extremely convenient; however, if you use a plugin that provides automatic backups of WordPress, you must take some extra steps to keep yourself safe.

Automatic backups can easily fill all of the disk space on your hosting account or server if old backups are not automatically deleted after a certain period of time.

It is also possible to have automatic backups create bad backups when, for example, some change or hack has happened to a WordPress website that goes undetected for long enough for the automatic backups to run. Depending on how long it takes to identify that a hack has occurred or there is some problem with WordPress, the automatic backup plugin may have enough time to overwrite any good backups that had been made before the hack or problem occurred.

Automatic backups can also push your hosting account or server's disk space beyond the limits your hosting provider has for automatically backing up your hosting account or server on their system, if they offer automated backups.

Some hosting providers also do not allow you to keep backups on your hosting account or server and may delete the backups without your consent after a certain period of time.

**Consider reviewing your hosting provider's policies on backups and the storage of backups. Many hosting providers can provide good advice and support for setting up thorough, multi-level backup solutions for WordPress.**

### Manually Backing Up WordPress
You are not required to use a WordPress backup plugin to backup WordPress. The WordPress files and database can be manually copied and exported using a variety of different tools and techniques depending on the levels of access you have to your hosting account's files and databases.

#### Use Hosting Provider's Control Panel or Tools
Most hosting providers use control panels or administrative tools that let you create different kinds of backups through their interfaces. Consult your hosting provider's documentation or contact their support team for assistance using their tools to generate backups of WordPress.

#### Backing Up WordPress Files
WordPress files can be backed up using any tool that allows you to access and to download files from your hosting account. These include but are not limited to FTP clients, command-line/shell clients, and web clients. Consult your hosting provider's documentation or contact their support team for assistance with using FTP, command-line, or web clients to access and to download your files to your computer.

#### Backing Up WordPress Database
The WordPress database is not stored in a file in your hosting account that can be easily or simply downloaded or copied. It must be exported using a database backup tool. Most hosting providers offer tools for accessing and backing up databases. If your hosting account does not have a database management tool, you can install phpMyAdmin, a popular, open-source tool for managing MySQL databases (the WordPress database is usually a MySQL database). [phpMyAdmin's makers have written documentation for installing phpMyAdmin](https://docs.phpmyadmin.net/en/latest/setup.html). After installing phpMyAdmin, you should be able to use your WordPress database username and database password from your wp-config.php file to login using phpMyAdmin.

**phpMyAdmin can be used to manage and make changes to your database in addition to backing up your database. Be careful not to accidentally edit your database through phpMyAdmin.**

To backup a database through phpMyAdmin, select the database in phpMyAdmin by clicking on the name of the database in the tree-view on the left-hand side of the phpMyAdmin page. phpMyAdmin should reload and show the tables in the currently selected database. Next, click on "Export" from the menu on the top of the page. There should be a Quick option and a Custom option for exporting the database. The Quick option is usually good enough for a basic backup. If you choose the Custom option, select all tables in the database, select SQL from the Format drop-down menu, check "Add DROP TABLE", and click Go. The database will then be downloaded through your Internet browser.