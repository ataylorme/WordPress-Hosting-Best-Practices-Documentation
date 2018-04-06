# Reliability
Once your site is up, how do you keep it that way?  And what can you do if it goes down?

## Backups
A WordPress site is composed of three (3) main components:

<dl>
<dt>Code</dt>
	<dd>WordPress core, zero (0) or more plugins, and one (1) or more themes _(but with only one theme active at a time)_ </dd>
<dt>Assets</dt>
 	<dd>Images, documents and other user-upload files, and maybe plugin or theme cache or configuration files</dd>
<dt>Database</dt>		  
	<dd>A MySQL database containing your posts, pages, comments, links, settings, and more</dd>
</dl>

> Your WordPress database contains every post, every comment and every link you have on your blog. If your database gets erased or corrupted, you stand to lose everything you have written. There are many reasons why this could happen and not all are things you can control. With a proper backup of your WordPress database and files, you can quickly restore things back to normal.

###### source: [WordPress Backups](https://codex.wordpress.org/WordPress_Backups)

It's a good idea to make regular copies, or backups, of your WordPress site *and* its database.  This safety net ensures that you'll be able to restore your backups to get up and running again in very little time.

## Monitoring
Site monitoring systems and services can notify you when your site isn't working properly.  They can often correct any minor issues, or help you to do so, before they become major issues.

### Uptime Monitoring
Uptime monitoring is traditionally done by checking one or more URLs on the site at regular intervals to make sure they are responding properly. While this can be set up manually there are plenty of services, many of which are free, that will take care of this for you.

### Performance Monitoring
While your site may be "up", how do you know that it's performing well? Performance monitoring is similar to uptime monitoring, but it also takes note of certain metrics that could indicate trouble.  Metrics like "page load time" and "number of transactions" are monitored and reported regularly to help keep you ahead of performance issues.

## Version Control
Version control manages changes to individual components of a site over time. In the case of a WordPress site, version control keeps a history of the code files. In addition to regular backups, version control is a great safety net for your WordPress site. If something goes wrong you can go back in the history and restore the site to a previous state, perhaps before you installed a troublesome plugin.

A lot of WordPress hosts offer version control but there are third-party services and self hosted options as well.
