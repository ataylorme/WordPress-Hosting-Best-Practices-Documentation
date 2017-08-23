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
As mentioned in the section on full page caching, WordPress processes PHP scripts as part of producing the HTML, CSS and JavaScript for a browser to load. It takes time for the web server to read each PHP script WordPress needs, to compile the script and to run the PHP script. By default, the web server has to do this process for every single visit to every single page. Full page caching can reduce how much the web server has to do this depending on what kind of full page caching is used, but there may still be some PHP scripts that have to be read, compiled, and run for every single visit.

Having to read and compile PHP scripts for every single visit can be extremely taxing on a web server. It would be like if every time someone asked you a question, you had to read a book in a different language, translate that book into your own language, and then answer the question, without taking any notes or remembering what the book said after you answered the question.

Op-code caching lets the web server take notes and remember what it has read between each time the web server is asked a question. Op-code caching stores a compiled copy of every PHP script in the server's memory (RAM). When the web server starts processing PHP scripts for WordPress, the web server checks the op-code cache for a cached copy of the PHP script. If there is a cached copy, the web server can skip straight to running the PHP script using the cached copy instead of having to read and compile the script again. Skipping reading and compiling PHP scripts can greatly improve the web server's resource usage and enable WordPress to serve many more requests than it might have been able to otherwise.

Op-code caching can make web servers use fewer resources when running WordPress; however, like with full page caching, op-code caching can cause changes to WordPress, such as installing or removing plugins and themes or updating WordPress, from showing up right away. It can be useful to manually purge the op-code cache after making any changes to the PHP files that make up WordPress.

### Fragment Caching

## Content Distribution Network (CDN)

## PHP

### Version

### Configuration

#### Memory Limits

#### File Upload Sizes

## Database Engines

### MySQL

### MariaDB

### Percona
