# Reliability
Once your site is up, how do you keep it that way? And what can you do if it goes down? In most cases, the same best practices apply to WordPress as with other web applications, but some differences and recommendations are detailed here.

## Backups
A WordPress site is composed of three (3) main components:

<dl>
<dt>Code</dt>
	<dd>WordPress core, zero (0) or more plugins, and one (1) or more themes _(but with only one theme active at a time)_ </dd>
<dt>Assets</dt>
 	<dd>Images, documents and other user-upload files, and maybe plugin or theme cache or configuration files</dd>
<dt>Database</dt>		  
	<dd>A set of tables containing your posts, pages, comments, links, settings, and other custom data created by plugins or themes.</dd>
</dl>

> Your WordPress database contains user-generated content and configuration, including every post, every comment and every link you have on your website. If your database gets erased or corrupted, you stand to lose everything you have written. There are many reasons why this could happen and not all are things you can control. With a proper backup of your WordPress database and files, you can quickly restore things back to normal.

It's recommended to keep and test regular backups of your WordPress sites using the system-level backup or snapshot infrastructure of your choice. One thing to be aware of is that the code, assets and database change in conjunction in WordPress but may be backed up separately. For this reason, it is a good idea to keep restore points that include backups of code, assets and database taken at the same point in time.

## Monitoring
Site monitoring systems and services can notify you when your site isn't working properly. They can often correct any minor issues, or help you to do so, before they become major issues.

### Uptime Monitoring
Uptime monitoring is traditionally done at the server level or by checking one or more URLs on the site at regular intervals to make sure they are responding properly. A combination of internal and external uptime monitoring is ideal for users, and there exist a variety of software and services to handle this for you.

### Performance Monitoring
While a site's services may be responding, to a user, a site being "up" means more than this to them. Performance monitoring is similar to uptime monitoring, but also takes note of certain metrics that could indicate trouble. Metrics like "page load time" and "slowest average transations" should be monitored and reported regularly to help keep you ahead of performance issues. Monitoring slow logs for problematic queries or requests can also help keep user sites stable. MySQL, PHP-FPM, and others provide options to capture these for monitoring.

## Version Control
Version control allows a user or host to store, view, or revert changes to individual components of a site over time. It's recommended to provide end users a way to manage their site over version control, as it encourages best practices and is a great extra safety net for their WordPress site.