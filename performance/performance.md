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
