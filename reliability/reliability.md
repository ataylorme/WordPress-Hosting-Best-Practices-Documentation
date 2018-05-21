# Reliability
Once your site is up, how do you keep it that way?  And what can you do if it goes down?

## Backups
A WordPress site is composed of three (3) main components:

<dl>
<dt>Code</dt>
	<dd>WordPress core, zero (0) or more plugins, and one (1) or more themes.</dd>
<dt>Assets</dt>
 	<dd>Images, documents and other user-upload files, and maybe plugin or theme cache or configuration files.</dd>
<dt>Database</dt>		  
	<dd>A MySQL database containing your posts, pages, comments, links, settings, and more.</dd>
</dl>

> Your WordPress database contains every post, every comment and every link you have on your blog. If your database gets erased or corrupted, you stand to lose everything you have written. There are many reasons why this could happen and not all are things you can control. With a proper backup of your WordPress database and files, you can quickly restore things back to normal.

###### source: [WordPress Backups](https://codex.wordpress.org/WordPress_Backups)

It's a good idea to make regular copies, or backups, of your WordPress site *and* its database.  This safety net ensures that you'll be able to restore your backups to get up and running again in very little time.

It's best practice to store backups in a different location than your site itself so they're not lost if something happens to the server. Let's look at a few options for managing backups.

### Manual Backups
The most basic way to backup your site is to manually create copies of its database and files, and then download them. You can make a `.zip` archive for the files and a `.sql` export for the database. They can be downloaded directly to your local machine or stored somewhere safe, like in cloud storage. [Creating Manual WordPress Backups](https://codex.wordpress.org/WordPress_Backups#Backing_Up_Your_WordPress_Site)

### Backup via Plugin
There are many WordPress plugins that will create backups for you automatically if you are not comfortable doing so manually. Again, remember to download the backups from your server once they are created.

### Backup Services
There are also services that will take care of creating, downloading, and storing backup files for you. Most of these services have a cost but are typically reliable and easy to use.

## Monitoring
Site monitoring systems and services can notify you when your site isn't working properly.  They can often correct any minor issues, or help you to do so, before they become major issues.

### Uptime Monitoring
Uptime monitoring is traditionally done by checking one or more URLs on the site at regular intervals to make sure they are responding properly. While this can be set up manually there are plenty of services, many of which are free, that will take care of this for you.

### Performance Monitoring
While your site may be "up", how do you know that it's performing well? Performance monitoring is similar to uptime monitoring, but it also takes note of certain metrics that could indicate trouble.  Metrics like "page load time" and "number of transactions" are monitored and reported regularly to help keep you ahead of performance issues.

## Version Control
Version control is a way of tracking the changes made to files over time by different people, such as the code for a website or another application. It allows people to track the revision history of code and to revert or apply changes easily via the command line. It is also a good way to debug your website if something goes wrong, as you can quickly restore to a previous state of the site's code without restoring from a full backup.

A lot of WordPress hosts offer version control but there are third-party services and self hosted options as well.
