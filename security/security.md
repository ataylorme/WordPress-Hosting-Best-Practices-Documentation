# Security
The goal of the page is to inform users who manage a WordPress site about general security best practices both in terms of environment level items, such as file permissions, as well as application level items, such as setting up proper user roles, so they have a better foundation for security than setting up WordPress somewhere with no additional configuration.

WordPress is extremely committed to providing a secure experience for WordPress site admnistrators and their users. More information about WordPress's official stance on security and a general discussion about WordPress's overall aims for security can be found on [WordPress.org's section about WordPress itself](https://wordpress.org/about/security/).

The following sections of this guide will provide instructions on how to keep WordPress secure. This guide borrows heavily from the WordPress Codex's guide on [Hardening WordPress](https://codex.wordpress.org/Hardening_WordPress). Although both the WordPress Codex and this guide cover security, this guide should be viewed as the authoritative best practices document for security for WordPress.

Hosting providers will usually take measures to provide varying degrees of secure environments by default; however, security for your WordPress website is ultimately your responsibility. Keeping any system, not just WordPress, secure is a continuous work. Good security requires careful planning and periodic maintenance.

Security largely consists of reducing risk and planning for recovery. Most security plans focus on minimizing the risk of unauthorized access only, but risk can never be successfully reduced to zero. As long as there is some risk, you must plan for recovery so that if something were to happen your website is not completely lost and your website can be quickly restored to normal operation.

Security is also about more than WordPress. It is also about making sure your hosting environment is secure and your personal online practices and behaviors keep you safe. Good security depends on the technology in use and the people using the technology. Obsolete or out-of-date technology can have bugs or vulnerabilities that can put your WordPress website at risk. People's bad online practices can also put your WordPress website as risk. It is important to make sure that not only do you keep the technology you use up-to-date and maintained but also that you are being safe when using the Internet and when using your WordPress website or hosting service.

## Ban Multiple Login Attempts

One of the most common kinds of attacks targeting Internet services is brute force login attacks. This attack is extremely simple to carry out thanks to the power of computers. In this attack, a malicious user tries to guess your WordPress website's admin username and password. The malicious user does not need to know anything about your WordPress website or your login information to do this attack. Using computers, you can make thousands of guesses per second. Maliciuos software developers have also written programs that do the guessing for you, and these programs use sophisticated tricks and techniques that can make strong-looking passwords really easy to guess.

The best protection against this kind of attack is to use a truly strong password. The strongest passwords are relatively long and randomly generated. There are several services and programs called password managers that you can use to generate and save passwords. Using a password manager makes having strong passwords much easier. For most of these programs, you only need to know a single password to open the password manager itself. They also usually encrypt their password databases so others cannot access them; this is much more secure than storing your passwords in a notebook or a Word document, for example. WordPress also will generate a strong random password for you, but you have to store the password somewhere if you want to be able to log into the WordPress admin dashboard later.

There additional steps that can be taken to protect WordPress against multiple login attempts. These steps largely boil down to adding an additional layer of authentication and to limiting logins to the WordPress admin dashboard. Additional layers of authentication and limiting logins can be implemented at the server level or through WordPress plugins.

Some of the following recommendations have been borrowed from [the WordPress Codex's guide on Brute Force Attacks](https://codex.wordpress.org/Hardening_WordPress).

### Notes About Usernames
Some WordPress security guides recommend using unique usernames for WordPress administrator accounts. While well-intentioned, WordPress's REST API allows anyone to view many of the users for your WordPress website. You can see this for yourself by putting /wp-json/wp/v2/users on the end of your WordPress website's URL. The output will be formatted for programs to use, but it should still be somewhat readable.

### Server Level

#### Password Protect wp-login.php
Adding a second password to wp-login.php requires all users to provide a password before being able to login into WordPress. This protects WordPress by adding a second username and password brute force attackers must guess before they can start guessing WordPress login information. Password protecting wp-login.php requires setting up a .htpasswd file. Your hosting provider may have tools that do this for you, especially if they use popular web panel software like cPanel or Plesk. The .htpasswd can be setup manually if you have access to the files on your hosting account. There are several tools, [such as this one](http://www.htaccesstools.com/htpasswd-generator/), on the Internet that will help you with generating a .htpasswd file. After you generate the file, you can put it in the same folder as your website or in a folder outside of your website's public folder. Once you have created the .htpasswd file, you have to tell the web server where to find the file. The configuration will be different depending on the web server you are using. Basic configuration examples for Apache and nginx, two of the most popular web servers, can be found below.

**Please be careful when making these changes. Errors in .htaccess files or in nginx configuration can cause WordPress to not load properly or the web server to show a 500 Internal Error. It is recommended to make a copy of any files you are going to edit before you make any changes. If you do get errors after saving changes, undo the changes or restore the backup copy of the files that were changed.**

##### Apache .htaccess code for password-protecting wp-login.php
The following code goes in the .htaccess file located within the same folder as WordPress. The .htaccess file is a hidden file. You may have to enable showing hidden files in the application you use to access your website files.

**Note that .htaccess code will be applied to any subfolders in the same folder as the .htaccess file. This means that WordPress websites located in subfolders of another WordPress website may be affected by this change.**

```
# Stop Apache from serving .ht* files
<Files ~ "^\.ht">
Order allow,deny
Deny from all
</Files>

# Protect wp-login
<Files wp-login.php>
AuthUserFile ~/.htpasswd   #<----- Change this to the path to where you put the .htpasswd file
AuthName "Private access"
AuthType Basic
require user mysecretuser  #<----- Change mysecretuser to be the username you used when generating the .htpasswd file
</Files>
```

##### Nginx code for password-protecting wp-login.php
The following code should be placed inside of the server block within nginx's configuration.

```
location /wp-login.php {
    auth_basic "Administrator Login";
    auth_basic_user_file .htpasswd;
}
```

#### Limit access to wp-login.php by IP address

If password-protecting wp-login.php is not a good fit, it is possible to restrict access to the Wordpress admin dashboard login to specific IP addresses. This can completely lockdown and prevent unauthorized logins to the WordPress admin dashboard, but this restriction can make accessing the WordPress admin dashboard less convenient for legitimate users.

**Many Internet Service Providers change the IP addresses for their customers frequently. If your ISP changes your IP address, you would have to manually update the whitelist of authorized IP addresses before you could login to the WordPress admin dashboard.**

The following sections show how to restrict access to wp-login.php with the Apache and nginx web servers.

**Please be careful when making these changes. Errors in .htaccess files or in nginx configuration can cause WordPress to not load properly or the web server to show a 500 Internal Error. It is recommended to make a copy of any files you are going to edit before you make any changes. If you do get errors after saving changes, undo the changes or restore the backup copy of the files that were changed.**

##### Apache .htaccess code for restricting access to wp-login.php by IP address
The following code goes in the .htaccess file located within the same folder as WordPress. The .htaccess file is a hidden file. You may have to enable showing hidden files in the application you use to access your website files.

**Note that .htaccess code will be applied to any subfolders in the same folder as the .htaccess file. This means that WordPress websites located in subfolders of another WordPress website may be affected by this change.**

```
<Files wp-login.php>
order deny,allow
allow from x.x.x.x
deny from all
</Files>
```

x.x.x.x should be replaced with your IP address. You can find your public-facing IP address by [searching Google for "my ip address"](https://www.google.com/search?q=my%20ip%20address). It is important to use your public-facing IP address, which may be different from your computer's local network IP address. The public-facing IP address is the address WordPress and the web server sees when you visit your website.

##### Nginx code for restricting access to wp-login.php by IP address
Add a location block inside of your server block with the following code.

```
error_page  403
location /wp-login.php {
  allow   x.x.x.x;
  allow   x.x.x.x;
  deny    all;
}
```

### ModSecurity and Multiple Login Attempts
Your host may already have protections against brute force login attacks for WordPress. Many hosting companies deploy the popular ModSecurity web application firewall package on their servers. ModSecurity monitors the requests visitors to your WordPress website make and blocks requests that match certain rules about what is and what is not legitimate activity. Your hosting provider should be able to provide more information about whether or not they use ModSecurity and what protections they have enabled if they do.

### Plugins
There are several plugins that will prevent brute force login attacks on WordPress with minimal configuration. [Plugins can be found in the WordPress plugin](https://wordpress.org/plugins/tags/brute-force/).

**You should review a plugin before installing it to make sure it is actively maintained by its developer and is up to date with the current version fo WordPress. You should also understand the changes the plugin will make to WordPress when you install it.**

### Two-Factor Authentication
Two-factor authentication, also know as 2FA or two-step authentication, is a login scheme that uses a separate, second form of authentication when a user attempts to login to a service with two-factor authentication enabled. The exact two-factor authentication setup varies from service to service, but it usually involves entering in a code or interacting with an application on a smartphone when attempting to login to a service. WordPress does not have two-factor authentication by default; however, [there are several plugins that provide two-factor authentication for self-hosted WordPress websites](http://wordpress.org/plugins/tags/two-factor-authentication).

Two-factor authentication is useful because if someone obtains the password to your account, they still cannot login without the second authentication form. Google, for example, has two-factor authentication for user accounts. When two-factor authentication is enabled, Google requires you to enter in a single-use, unique code sent to your smartphone or makes you interact with your smartphone after you attempt to login to your Google account on a device or computer you have not previously used to login. If someone somehow got your Google account's password, the unauthorized user could not access your account because the unauthorized user could not provide the code or do the necessary interactions since those things are tied to your smartphone. You also are immediately notified when someone is accessing your Google account because you would receive the single-use, unique code or the prompt to interact with your smartphone for the login.

Two-factor authentication can make logging into services less convenient, since access to the second form of authentication (your smartphone, in the example with Google) is required to login. For critical services, though, two-factor authentication greatly improves the security of your accounts.

## File System

### File Permissions

### User Accounts

### Uploads vs. Core Files

## WordPress Users and Roles
