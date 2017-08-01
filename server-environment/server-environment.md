# Server Environment
WordPress will run on a minimum server environment. However, WordPress doesn't run optimally on the minimum system requirements. This section will cover the _recommended_ server environment for WordPress to run more effectively.

## PHP Version
PHP `7.0` or greater is highly encouraged but WordPress will run, with slower performance, on PHP `5.6` as well. For this reason PHP versions less than `7` are not recommended. See [WordPress and PHP7](https://make.wordpress.org/core/2015/09/10/wordpress-and-php7/) for details.

## PHP Extensions
WordPress core makes use of PHP extensions. If the the preferred extension is missing WordPress will either have to do more work to do the task the module helps with or, in the worst case, will remove functionality. Therefore the PHP extensions listed below are recommended.

* bcmath - Used to improve the performance of math calculations.
* curl - Performs remote request operations.
* filter - Used for securely filtering user input.
* mod_xml - Used for generating XML, such as for an XML sitemap.
* mysqli - Connects to MySQL for database interactions.
* libsodium - Generates random bytes.
* openssl - Permits SSL-based connections to other hosts.
* pcre - Increases performance of pattern matching in code searches.
* imagick - Provides better image quality for media uploads. See [WP_Image_Editor is incoming!](https://make.wordpress.org/core/2012/12/06/wp_image_editor-is-incoming/) for details. Smarter image resizing (for smaller images) and PDF thumbnail support, when Ghost Script is also available.
* xml - Used for XML parsing, such as from a third-party site.

For the sake of completeness, below is a list of the remaining PHP modules WordPress _may_ use in certain situations or if other modules are unavailable. These are fallbacks and not needed in an optimal environment, but installing them won't hurt.

* gd - If Imagick isn't installed, the GD Graphics Library is used as an alternative for image manipulation.
* mcrypt - Generates random bytes when libsodium isn't available.
* xmlreader - Used for XML parsing.
* zlib - Gzip compression and decompression.

These extensions are used for file changes, such as updates and plugin/theme installation, when files aren't writeable on the server. The priority of the transports are: Direct, SSH2, FTP PHP Extension, FTP Sockets.
* ssh2
* sockets
* ftp

## System Packages
* ImageMagick - Required by Imagick extension
* Ghost Script - Enables Imagick/ImageMagick to generate PDF thumbnails for the media library. See [Enhanced PDF Support in WordPress 4.7](https://make.wordpress.org/core/2016/11/15/enhanced-pdf-support-4-7/) for details.
