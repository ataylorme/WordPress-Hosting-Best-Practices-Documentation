# Performance
This section will cover the basics on how to increase your site performance.

## Caching
WordPress can handle a lot of complex functionality but this comes at a cost. Tasks such as processing PHP, querying the database and collecting information from external APIs all take resources and time. Caching is simply saving the result of these potentially heavy tasks and reusing those results rather than calculating them again. Caches typically expire after a certain amount of time and are regenerated so the most recent content is displayed. When items are served from cache they have a faster response time, usually coming from memory, and take load off the server.

### Full Page Caching
Your WordPress sites do a lot of work. They process PHP, make external API requests, fetch content from the database and more. All of the work WordPress does is to output HTML, CSS and JavaScript for a browser to load. Generating this browser view takes time.

Full page caching is simply taking the resulting HTML, CSS and JavaScript WordPress produces for a page and saving the result so the work doesn't have to be repeated for the next site visitor.

If the pages on your WordPress site aren't changing for each visitor it is best practice to implement a full page cache. Some example might be an about page, or contact page. If your site is tailored to each user, such as a forum showing only new messages that interest each user, then full page caching might not be the best fit.

If full page caching is implemented properly WordPress won't have to do any work until the cache expires, at which point WordPress will generate the HTML, CSS and JavaScript for the browser - and the full page cache will retain those new results until the designated time expires.

![Full Page Caching Response Example](/assets/full-page-caching-response-example.png)

When working with caching it's important to adjust the cache duration depending on the site's needs or the needs for the individual page. For example, an e-commerce template showing the best selling products may need a short cache so the list is updated every minute. Alternatively, a single product page, which isn't changing often, can have a longer cache.

The cache can also be purged even if it hasn't expired. This should be done if you publish new content. If possible only purge the cache the new content effects, rather than purging the entire cache.

### Object Caching
> In 2005, WordPress introduced its internal object cache — a way of automatically storing any data from the database (not just objects) in PHP memory to prevent unnecessary queries. However, out of the box, WordPress will discard all of those objects at the end of the request, requiring them to be rebuilt from scratch for the next page load.

###### source: [scalewp.io](https://www.scalewp.io/object-caching/)

What does this mean? Think of a standard WordPress homepage displaying the most recent posts. Each of these posts has quite a bit of information associated with it WordPress must look up such as the author, categories, tags, excerpt, etc. Out of the box WordPress will throw this information away after each request and fetch it again for the next visitor to the site.

A persistent object cache gives WordPress a place to store data for re-use. Like other forms of caching this data will expire after a given amount of time. While these objects are cached, however, PHP execution time is improved while lessening the load on the database.

Since object cache stores full objects the cached items are reuseable across multiple pages and work for authenticated traffic - a benefit full page caching doesn't provide.

![WordPress Object Caching Diagram](/assets/wordpress-object-caching-example.png)

> Transients are inherently sped up by caching plugins, where normal Options are not. A memcached plugin, for example, would make WordPress store transient values in fast memory instead of in the database. For this reason, transients should be used to store any data that is expected to expire, or which can expire at any time. Transients should also never be assumed to be in the database, since they may not be stored there at all.

###### source: [WordPress Codex](https://codex.wordpress.org/Transients_API)

A good example is a social media widget. A plugin may call out to a third-party API to fetch the latest social content. Rather than doing this on every page load the results can be stored in a transient. WordPress will store transients, these forms of expiring options, in the datbase. In most cases fetching the latest social posts from the database is faster than calling out to the social media API but object caching can improve this further. Rather than store those items in the database WordPress will make use of the persistent object cache, usually a fast memory store.

Persistent object caching can speed up WordPress and is offered my many managed WordPress hosts or can be set up independently. You will also need a plugin to connect WordPress to the object cache. There are many [available on the plugin directory](https://wordpress.org/plugins/search/object+cache/)

### Op-code Caching (a.k.a server-side caching)
As mentioned in the section on full page caching, WordPress processes PHP scripts as part of producing the HTML, CSS and JavaScript for a browser to load. It takes time for the web server to read each PHP script WordPress needs, to compile the script and to run the PHP script. By default, the web server has to do this process for every single visit to every single page. Full page caching can reduce how much the web server has to do this depending on what kind of full page caching is used, but there may still be some PHP scripts that have to be read, compiled, and run for every single visit. For example, WordPress caching plugins still have to check if they need to rebuild their caches. PHP scripts also have to be read, compiled, and run for WordPress to generate any dynamic, uncached content like comments or the page for a WooCommerce store and for WordPress to show the admin dashboard. Using op-code caching can help speed up your server since it can run WordPress without having to read and compile PHP scripts for every single page visit.

Op-code caching stores a compiled copy of every PHP script in the server's memory (RAM). When the web server starts processing PHP scripts for WordPress, the web server checks the op-code cache for a cached copy of the PHP script. If there is a cached copy, the web server can skip straight to running the PHP script using the cached copy instead of having to read and compile the script again. Skipping reading and compiling PHP scripts can greatly improve the web server's resource usage and enable WordPress to serve many more requests than it might have been able to otherwise.

Op-code caching can make web servers use fewer resources when running WordPress; however, like with full page caching, op-code caching can cause changes to WordPress, such as installing or removing plugins and themes or updating WordPress, from showing up right away. It can be useful to manually purge the op-code cache after making any changes to the PHP files that make up WordPress.

### Fragment Caching

## Content Distribution Network (CDN)
Content distribution networks are made up of global endpoints that can provide caching closer to the end user. Caching items at physical locations closer to the end user improve performance and latency by decreasing the round-trip network time. Examples of items that can be cached by a CDN are static assets (CSS< JavaScript, and images), REST API responses, and full page cache responses.

## PHP

PHP (PHP: Hypertext Preprocessor) is a popular programming language on the internet. PHP turns dynamic content, like that in WordPress, into HTML, CSS, and JavaScript that web browsers can read. WordPress is written in PHP. All of its core files and scripts are PHP scripts, and a server must have PHP in order for WordPress to be able to run.

PHP is an interpreted language. WordPress and other programs written in PHP do not have to be compiled ahead of time before they can be run. This means the same PHP code can run on any platform that can run PHP. Interpreted languages do tend to have slower performance than compiled languages; however, much work has been done to improve PHP in this regard.

PHP's configuration has a very large impact on how well WordPress will run and if WordPress can run at all. For example, many older versions of PHP are no longer compatible with WordPress. In addition, properly configuring PHP is critical for ensuring WordPress can properly function.

### Version

The current major version of PHP is PHP 7. If possible, PHP 7 should be used to run WordPress. As of the writing of this document, PHP 7 is the only major version of PHP still receiving active development and support. The makers of PHP eventually retire versions of PHP as they continue to add new features to PHP. Sometimes the features that are added make new versions of PHP significantly different than older versions. It is all part of PHP growing as a programming language. The newer versions of PHP also have performance improvements and security patches that older versions of PHP do not have and likely will never receive.

Servers running older versions of PHP should be upgraded to the newest version of PHP if possible. However, extreme care must be taken when upgrading the version of PHP. Older websites built to use older versions of PHP are usually also not readily or completely compatible with newer versions of PHP. If the newest version of WordPress is being used, there should not be any compatibility issues with WordPress; however, 3rd-party plugins or themes may not be compatible with the newest version of PHP. 

**Always test your PHP website in a non-production environment if possible. Testing in a non-production environment allows you to find any issues you will have without causing your website to be unavailable or have errors when people visit your website.**

Upgrading PHP can be a somewhat time-consuming process depending on the hosting server's configuration, and the upgrade also often cannot be easily reversed if issues are discovered after upgrading.

**If you are uncomfortable with or do not know how to upgrade PHP, you should contact your hosting provider. Hosting providers can usually help with upgrading to a newer version of PHP.**

If upgrading to PHP 7 is not immediately possible, upgrading to PHP 5.6 should be done as soon as possible. PHP 5.6 is the oldest version of PHP 5 that is still receiving security patches. Older versions of PHP are not having their bugs and vulnerabilities patched. They should be considered insecure and can make websites more vulnerable. A plan to upgrade to PHP 7 should still be developed. PHP 7 offers significant improvements in performance over PHP 5. It also is receiving active updates and security patches and will receive development for years to come. PHP 5.6's security patches end in 2018. More information about the support versions of PHP can always be found [on PHP's supported versions page](http://php.net/supported-versions.php)

### Configuration

#### Memory Limits

#### File Upload Sizes

## Database Engines

### MySQL

### MariaDB

### Percona
