# Performance
This section will cover the basics on how to increase your site performance.

## Caching
WordPress can handle a lot of complex functionality but this comes at a cost. Tasks such as processing PHP, querying the database and collecting information from external APIs all take resources and time. Caching is simply saving the result of these potentially heavy tasks and reusing those results rather than calculating them again. Caches typically expire after a certain amount of time and are regenerated so the most recent content is displayed. When items are served from cache they have a faster response time, usually coming from memory, and take load off the server.

### Full Page Caching
Your WordPress sites do a lot of work. They process PHP, make external API requests, fetch content from the database and more. All of the work WordPress does is to output HTML, CSS and JavaScript for a browser to load. Generating this browser view takes time.

Full page caching is simply taking the resulting HTML, CSS and JavaScript WordPress produces for a page and saving the result so the work doesn't have to be repeated for the next site visitor.

If the pages on your WordPress site aren't changing for each visitor it is best practice to implement a full page cache. Some example might be an about page, or contact page. If your site is tailored to each user, such as a forum showing only new messages that interest each user, then full page caching might not be the best fit.

If full page caching is implemented properly WordPress won't have to do any work until the cache expires, at which point WordPress will generate the HTML, CSS and JavaScript for the browser - and the full page cache will retain those new results until the designated time expires.

When working with caching it's important to adjust the cache duration depending on the site's needs or the needs for the individual page. For example, an e-commerce template showing the best selling products may need a short cache so the list is updated every minute. Alternatively, a single product page, which isn't changing often, can have a longer cache.

The cache can also be purged even if it hasn't expired. This should be done if you publish new content. If possible only purge the cache the new content effects, rather than purging the entire cache.

### Object Caching

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
