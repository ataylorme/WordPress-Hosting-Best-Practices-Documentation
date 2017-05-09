# Reliability
One of the key responsibilities of a website maintainer is the site's reliability. This section will cover the basics on how how to make sure your site is up and creating a safety net in case it goes down.

## Backups
A WordPress site is composed of two main pieces: the code/files, such as WordPress itself, themes and plugins, and the database, which holds all of your site's content.

> Your WordPress database contains every post, every comment and every link you have on your blog. If your database gets erased or corrupted, you stand to lose everything you have written. There are many reasons why this could happen and not all are things you can control. With a proper backup of your WordPress database and files, you can quickly restore things back to normal.

###### source: [WordPress Backups](https://codex.wordpress.org/WordPress_Backups)

It's a good idea to keep copies, or backups, of both the database and the files for your WordPress site. This way if something ever happens to your site, like the server crashing, you can restore your backup to get the site up and running again. 

With that in mind it's best practice to keep backups in a different location than your site itself that way they aren't lost when something happens to the server. Let's look at a few options for managing backups.

### Manual Backups
The most basic way to backup your site is to manually create copies of the database and files and download them. You can make a `.zip` archive for the files and a `.sql` export for the database. They can be downloaded directly to your machine or stored somewhere safe, like a cloud storage.

### Backup via Plugin
There are many WordPress plugins that will create backups for you automatically if you are not comfortable doing so manually. Again, remember to download the backups from your server once they are created.

### Backup Services
There are also services that will take care of creating backup files, downloading and storing them for you. Most of these services have a cost but are typically reliable and easy to use.

## Monitoring
Setting up monitoring for your site is important so you are notified of when it isn't working properly and can correct the issue before stakeholders, like a client or boss, or users encounter issues.

### Uptime Monitoring
Uptime monitoring is traditionally done by checking one or more URLs on the site at regular intervals to make sure they are working properly. While this can be setup manually there are plenty of services, many of which are free, that will take care of this for you - just be sure to set one up.

### Performance Monitoring
While your site may be up how do you know it's performing well? Performance monitoring is similar to uptime monitoring in that it checks the site at regular intervals but goes a step further by checking metrics like page load time.

## Version Control
Version control manages changes to items over time. In the case of a WordPress site version control keeps a history of the code files. Besides regular backups, version control is a great safety net for your WordPress site. If something goes wrong you can go back in the history and restore the site to a previous state, perhaps before you installed a troublesome plugin.

A lot of WordPress hosts offer version control but there are third-party services and self hosted options as well.