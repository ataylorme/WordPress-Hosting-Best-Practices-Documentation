# Reliability
This section will cover the basics on how to know if your site is up and creating a safety net in case it goes down.

## Backups
A WordPress site is composed of two main pieces:

<dl>
<dt>Code and Assets</dt>
<dd>WordPress itself, themes, plugins, images</dd>
<dt>A Database</dt>
<dd>A MySQL database which contains all of your posts, pages, comments, and links</dd>
</dl>

> Your WordPress database contains every post, every comment and every link you have on your blog. If your database gets erased or corrupted, you stand to lose everything you have written. There are many reasons why this could happen and not all are things you can control. With a proper backup of your WordPress database and files, you can quickly restore things back to normal.

###### source: [WordPress Backups](https://codex.wordpress.org/WordPress_Backups)

It's a good idea to keep copies, or backups, of both the database *and* the files for your WordPress site. This way if something ever happens to your site, like the server crashing, you can restore your backup to get the site up and running again. 

With that in mind it's best practice to keep backups in a different location than your site itself so they're not lost if something happens to the server. Let's look at a few options for managing backups.

### Manual Backups
The most basic way to backup your site is to manually create copies of its database and files and download them. You can make a `.zip` archive for the files and a `.sql` export for the database. They can be downloaded directly to your machine or stored somewhere safe, like a cloud storage. [Creating Manual WordPress Backups](https://codex.wordpress.org/WordPress_Backups#Backing_Up_Your_WordPress_Site)

### Backup via Plugin
There are many WordPress plugins that will create backups for you automatically if you are not comfortable doing so manually. Again, remember to download the backups from your server once they are created.

### Backup Services
There are also services that will take care of creating, downloading, and storing backup files for you. Most of these services have a cost but are typically reliable and easy to use.

## Monitoring
Site monitoring systems and services can notify you when your site isn't working properly.  They can often correct any issues, or help you to do so, before other people discover problems with your site.

### Uptime Monitoring
Uptime monitoring is traditionally done by checking one or more URLs on the site at regular intervals to make sure they are responding properly. While this can be set up manually there are plenty of services, many of which are free, that will take care of this for you.

### Performance Monitoring
While your site may be "up", how do you know that it's performing well? Performance monitoring is similar to uptime monitoring, but it also takes note of certain metrics that could indicate performance problems.  Metrics like "page load time" and "number of transactions" are monitored and reported regularly to help keep you ahead of performance issues.

## Version Control
Version control manages changes to individual components of a site over time. In the case of a WordPress site, version control keeps a history of the code files. In addition to regular backups, version control is a great safety net for your WordPress site. If something goes wrong you can go back in the history and restore the site to a previous state, perhaps before you installed a troublesome plugin.

A lot of WordPress hosts offer version control but there are third-party services and self hosted options as well.
