# Server Environment

WordPress will run on a minimum server environment. However, WordPress doesn't run optimally on the minimum system requirements. This section will cover the _recommended_ server environment for WordPress to run more effectively.

## Server

### Recommended Servers

WordPress recommends to use one of these servers:
* Apache 2.4 or higher
* NGINX 1.14

### Apache Configurations

#### .htaccess

### NGINX Configuration

## PHP 

### PHP Version

PHP `7.3` or greater is highly recommended. If you are in a legacy environment where you only have older PHP or MySQL versions, WordPress also works with PHP 5.6.20+ and MySQL 5.0+, but these versions have reached official End Of Life and as such may expose your site to security vulnerabilities.


### PHP Extensions

WordPress core makes use of PHP extensions. If the preferred extension is missing WordPress will either have to do more work to do the task the module helps with or, in the worst case, will remove functionality. Therefore the PHP extensions listed below are recommended.

* bcmath - Used to improve the performance of math calculations.
* curl - Performs remote request operations.
* exif - Works with metadata stored in images.
* filter - Used for securely filtering user input.
* fileinfo - Used to detect mimetype of file uploads
* mod_xml - Used for generating XML, such as for an XML sitemap.
* mysqli - Connects to MySQL for database interactions.
* libsodium - Generates random bytes.
* openssl - Permits SSL-based connections to other hosts.
* pcre - Increases performance of pattern matching in code searches.
* imagick - Provides better image quality for media uploads. See [WP_Image_Editor is incoming!](https://make.wordpress.org/core/2012/12/06/wp_image_editor-is-incoming/) for details. Smarter image resizing (for smaller images) and PDF thumbnail support, when Ghost Script is also available.
* xml - Used for XML parsing, such as from a third-party site.

For the sake of completeness, below is a list of the remaining PHP modules WordPress _may_ use in certain situations or if other modules are unavailable. These are fallbacks and not needed in an optimal environment, but installing them won't hurt.

* gd - If Imagick isn't installed, the GD Graphics Library is used as a functionally limited fallback for image manipulation.
* mcrypt - Generates random bytes when libsodium isn't available.
* xmlreader - Used for XML parsing.
* zlib - Gzip compression and decompression.

These extensions are used for file changes, such as updates and plugin/theme installation, when files aren't writeable on the server. The priority of the transports are: Direct, SSH2, FTP PHP Extension, FTP Sockets.

* ssh2
* sockets
* ftp

### System Packages

* ImageMagick - Required by Imagick extension
* Ghost Script - Enables Imagick/ImageMagick to generate PDF thumbnails for the media library. See [Enhanced PDF Support in WordPress 4.7](https://make.wordpress.org/core/2016/11/15/enhanced-pdf-support-4-7/) for details.

## Database

WordPress stores content, configuration, and other information inside of a database. The database for a WordPress website is where all of the WordPress website's user-defined data is stored. WordPress is primarily designed to use a MySQL or MySQL-related database server; WordPress officially only supports MySQL or MariaDB, a drop-in replacement for MySQL.

### MySQL

MySQL is a widely used relational database server. MySQL comes in both open-source and commercial distributions. Either distribution should work with MySQL. The commercial distribution has additional features not found in the open-source distribution; however, WordPress does not require or use the additional features. It is designed to run on either the open-source or the commercial distribution.

### MariaDB

MariaDB is a drop-in replacement for MySQL supported by WordPress. It's a fork of the open-source distribution of MySQL. MariaDB was originally created to maintain a more open-source version of MySQL, but it has grown into its own relational database server alternative to MySQL with features and changes not found in MySQL. Despite its differences, MariaDB is still a fully compatible replacement for MySQL and can generally seamlessly replace MySQL.

### Percona

Percona server is a drop-in replacement for MySQL, focused on performance. Although it's a drop-in replacement for MySQL, WordPress does not officially support Percona.

### Recommended Versions

WordPress recommends the following settings for your Database:

* MySQL 5.6 or greater
* MariaDB 10.1 or greater

### MySQL and MariaDB Configuration