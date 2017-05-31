# Performance
This section will cover the basics on how to increase your site performance.

## Caching
WordPress can handle a lot of complex functionality but this comes at a cost. Tasks such as processing PHP, querying the database and collecting information from external APIs all take resources and time. Caching is simply saving the result of these potentially heavy tasks and reusing those results rather than calculating them again. Caches typically expire after a certain amount of time and are regenerated so the most recent content is displayed. When items are served from cache they have a faster response time, usually coming from memory, and take load off the server.

### Full Page Caching

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
