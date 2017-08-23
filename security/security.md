# Security
The goal of the page is to inform users who manage a WordPress site about general security best practices both in terms of environment level items, such as file permissions, as well as application level items, such as setting up proper user roles, so they have a better foundation for security than setting up WordPress somewhere with no additional configuration.

## Ban Multiple Login Attempts

#### Username Enumeration
Providing your username to a would be brute force attacker is half of the problem. Using a command line for loop with a simple curl, you can query a WordPress site and list our the usernames simply querying the author page and trying all the ID's. to test this out, visiting yourdomain.com/?author=$number where $number is the user ID will show your username right in the URL. To stop this behavior, you can either add a rule to your .htaccess to block it, or just use functions.php to redirect them to your homepage.

*.htaccess*
```
RewriteCond %{REQUEST_URI} !^/wp-admin [NC]
RewriteCond %{QUERY_STRING} author=\d
RewriteRule ^ - [L,R=403]
```
This code will force a 403 error if the author slug is queried in your URL. 

*functions.php*
#### Redirect author page to homepage
```php
add_action( 'template_redirect', 'no_viewing_author_pages' );

function no_viewing_author_pages() {
    # If the author archive page is being queried to discover usernames, redirect to homepage
    if ( is_author() ) {
        wp_safe_redirect( get_home_url(), 301 );
        exit;
    }
}
```
This function would just redirect them to the Home page when they attempt to query the author slug.

### Server Level

### Plugins

## File System

### File Permissions

### User Accounts

### Uploads vs. Core Files

## WordPress Users and Roles
