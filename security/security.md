# Security
The goal of the page is to inform users who manage a WordPress site about general security best practices both in terms of environment level items, such as file permissions, as well as application level items, such as setting up proper user roles, so they have a better foundation for security than setting up WordPress somewhere with no additional configuration.

**The most important thing to do for WordPress security is keeping WordPress itself and all installed plugins and themes up to date. It also is important to make sure that you are using themes and plugins that are actively receiving updates.**

WordPress is extremely committed to providing a secure experience for WordPress site administrators and their users. More information about WordPress's official stance on security and a general discussion about WordPress's overall aims for security can be found on [WordPress.org's section about WordPress itself](https://wordpress.org/about/security/).

The following sections of this guide will provide instructions on how to keep WordPress secure. This guide borrows heavily from the WordPress Codex's guide on [Hardening WordPress](https://codex.wordpress.org/Hardening_WordPress). Although both the WordPress Codex and this guide cover security, this guide should be viewed as the authoritative best practices document for security for WordPress.

Hosting providers will usually take measures to provide varying degrees of secure environments by default; however, security for your WordPress website is ultimately your responsibility. Keeping any system, not just WordPress, secure is a continuous work. Good security requires careful planning and periodic maintenance.

Security largely consists of reducing risk and planning for recovery. Most security plans focus on minimizing the risk of unauthorized access only, but risk can never be successfully reduced to zero. As long as there is some risk, you must plan for recovery so that if something were to happen your website is not completely lost and your website can be quickly restored to normal operation.

Security is also about more than WordPress. It is also about making sure your hosting environment is secure and your personal online practices and behaviors keep you safe. Good security depends on the technology in use and the people using the technology. Obsolete or out-of-date technology can have bugs or vulnerabilities that can put your WordPress website at risk. People's bad online practices can also put your WordPress website as risk. It is important to make sure that not only do you keep the technology you use up-to-date and maintained but also that you are being safe when using the Internet and when using your WordPress website or hosting service.

## Ban Multiple Login Attempts

One of the most common kinds of attacks targeting Internet services is brute force login attacks. This attack is extremely simple to carry out thanks to the power of computers. In this attack, a malicious user tries to guess your WordPress website's admin username and password. The malicious user does not need to know anything about your WordPress website or your login information to do this attack. Using computers, you can make thousands of guesses per second. Malicious software developers have also written programs that do the guessing for you, and these programs use sophisticated tricks and techniques that can make strong-looking passwords really easy to guess.

The best protection against this kind of attack is to use a truly strong password. Using a password manager makes having strong passwords much easier. If you would like to learn more about password managers, [Wikipedia has an article about password managers in general] (https://en.wikipedia.org/wiki/Password_manager). It also has a [list of password managers] (https://en.wikipedia.org/wiki/List_of_password_managers) if you would like to find one to use.

There additional steps that can be taken to protect WordPress against multiple login attempts. These steps largely boil down to adding an additional layer of authentication and to limiting logins to the WordPress admin dashboard. Additional layers of authentication and limiting logins can be implemented at the server level or through WordPress plugins.

Some of the following recommendations have been borrowed from [the WordPress Codex's guide on Brute Force Attacks](https://codex.wordpress.org/Hardening_WordPress).

### Notes About Usernames
Some WordPress security guides recommend using unique usernames for WordPress administrator accounts. While well-intentioned, WordPress's REST API allows anyone to view many of the users for your WordPress website. You can see this for yourself by putting /wp-json/wp/v2/users on the end of your WordPress website's URL. The output will be formatted for programs to use, but it should still be somewhat readable.

### Server Level

#### Password Protect wp-login.php
For individual WordPress websites experiencing ongoing and frequent brute force login attacks, adding a second password to wp-login.php using HTTP Basic Authentication can help protect the website while reducing the attack's impact on the hosting server. If you are hosting your own WordPress websites, your hosting provider may have tools that do this for you, especially if they use popular web panel software like cPanel or Plesk. This method is not really appropriate for WordPress hosts with large numbers of websites they are hosting. Other security methods, like ModSecurity rules or other web application firewalls, may be more appropriate for preventing this kind of attack on a larger scale.

#### Limit access to wp-login.php by IP address

If password-protecting wp-login.php is not a good fit for an individual WordPress website, it is possible to restrict access to the Wordpress admin dashboard login to specific IP addresses. This can completely lockdown and prevent unauthorized logins to the WordPress admin dashboard, but this restriction can make accessing the WordPress admin dashboard less convenient for legitimate users. Like password protecting wp-login.php using HTTP Basic Authentication, this protection is usually not a good fit for a hosting company to apply across an entire platform or server. It is usually best applied individually to WordPress websites experiencing ongoing and frequent brute force attacks that cannot be easily addressed through other means.

**Many Internet Service Providers change the IP addresses for their customers frequently. If your ISP changes your IP address, you would have to manually update the whitelist of authorized IP addresses before you could login to the WordPress admin dashboard.**

### ModSecurity and Multiple Login Attempts
ModSecurity is a popular web application firewall for dynamically blocking malicious requests. ModSecurity monitors the requests visitors make for any websites and blocks requests that match certain rules about what is and what is not legitimate activity. If you purchased hosting from an existing hosting provider, your hosting provider probably already has ModSecurity configured, often with their own custom-tailored rules. In this case, contact your hosting provider for more information about how they are using ModSecurity to protect your WordPress websites.

For hosting companies, ModSecurity is an extremely powerful tool for protecting servers. However, it is relatively complex and can be difficult to configure. Given that ModSecurity monitors all web traffic, changes to ModSecurity rules can easily result in legitimate web activity being blocked by ModSecurity. Caution is recommended when making any modifications to ModSecurity. Hosting providers looking to use ModSecurity or to change their configuration should research ModSecurity further or consult with ModSecurity experts.

### Captchas
Captchas are tests that help to prevent bots from being able to complete website forms, such as the WordPress admin dashboard login. A Captcha is usually a test that requires some level of human input before the form can be submitted. There are several plugins that can be used to add Captchas to WordPress forms and to the WordPress admin dashboard login page as well. These tools can also help protect against brute force login attacks while still providing a more convenient login experience for WordPress users.

### Plugins
There are several plugins that will prevent brute force login attacks on WordPress with minimal configuration. [Plugins can be found in the WordPress plugin](https://wordpress.org/plugins/tags/brute-force/).

**You should review a plugin before installing it to make sure it is actively maintained by its developer and is up to date with the current version fo WordPress. You should also understand the changes the plugin will make to WordPress when you install it.**

### Two-Factor Authentication
Two-factor authentication, also know as 2FA or two-step authentication, is a login scheme that uses a separate, second form of authentication when a user attempts to login to a service with two-factor authentication enabled. The exact two-factor authentication setup varies from service to service, but it usually involves entering in a code or interacting with an application on a smartphone when attempting to login to a service. WordPress does not have two-factor authentication by default; however, [there are several plugins that provide two-factor authentication for self-hosted WordPress websites](http://wordpress.org/plugins/tags/two-factor-authentication).

Two-factor authentication is useful because if someone obtains the password to your account, they still cannot login without the second authentication form. Google, for example, has two-factor authentication for user accounts. When two-factor authentication is enabled, Google requires you to enter in a single-use, unique code sent to your smartphone or makes you interact with your smartphone after you attempt to login to your Google account on a device or computer you have not previously used to login. If someone somehow got your Google account's password, the unauthorized user could not access your account because the unauthorized user could not provide the code or do the necessary interactions since those things are tied to your smartphone. You also are immediately notified when someone is accessing your Google account because you would receive the single-use, unique code or the prompt to interact with your smartphone for the login.

Two-factor authentication can make logging into services less convenient, since access to the second form of authentication (your smartphone, in the example with Google) is required to login. For critical services, though, two-factor authentication greatly improves the security of your accounts.

## File System

The setup of your hosting account's file system can have a large impact on the security of WordPress. Setting proper file persmissions and ownership is extremely important for ensuring unauthorized users cannot access or modify WordPress's files.

### File Permissions

**This section on file permissions focuses entirely on file permissions on Linux servers. If you are using a Windows server, please consult with your hosting provider or a Windows server administrator for help setting the proper permissions.**

Linux file permissions consist primarily of three components -- the permissions the owner of the file or folder has, the permissions members of the group that owns the file or folder have, and the permissions that anyone else has for accessing or modifying the file and folder. The three permission components are usually represented using three numbers in order of the owner's permission level, the group's permission level, and everyone's permission level. _There is technically a fourth component, but that is beyond what we need to know to secure WordPress. It will not be discussed here._

There are three kinds of access each for the user, the group, and everyone else. They are read access, write access, and execute access. Read access lets you read the contents of the file or the directory. Write access lets you modify the file or the directory. And execute access lets you run the file like a program or a script.

#### Numeric Representation of File Permissions
Linux stores these different kinds of access internally as bits (i.e. in binary form). They are commonly represented in human-readable form as the numbers 4 (read access), 2 (write access), and 1 (execute access). These numbers are added together to represent different combinations of the three kinds of access you can have. 

#### Symbolic Representation of File Permissions
Some programs will represent the different kinds of access using letters instead of numbers. When using symbols, the kinds of access are still read access, write access, and execute access. Instead of numbers, the kinds of access are represented using "r" (read access), "w" (write access), "x" (execute access). These three letters are combined together (e.g. "rwx", "rw", "wx", etc.) to represent the different combinations of the three kinds of access you can have.

#### Examples of Linux File Permissions
| Symbolic         | Numeric         | Permissions                                                                                  |
|:----------------:|:---------------:|:--------------------------------------------------------------------------------------------:|
|    ----------    |       000       | no permissions                                                                               |
|    -r--------    |       400       | read only for user                                                                           |
|    -rw-------    |       600       | read & write only for user                                                                   |
|    -rwx------    |       700       | read, write, & execute only for user                                                         |
|    -rwxr-xr-x    |       755       | read, write, & execute for user, only read & execute for group and everyone else             |
|    -rw-r--r--    |       644       | read & write for user, only read for group and everyone else                                 |
|    -rwxrwxrwx    |       777       | read, write, and execute for user, group, and everyone else **Do not use. Security Risk.**   |

#### Recommend Default Linux File Permissions

The default recommended file permissions for WordPress are 755 (-rwxr-xr-x) for folders and 644 (-rw-r--r--) for files. These permissions will ensure that WordPress can function properly while protecting WordPress from having its files modified by malicious or unauthorized users.

### User Accounts

### Uploads vs. Core Files

## WordPress Users and Roles

## Backing Up WordPress
WordPress has two major components -- the website files and the WordPress database. Although WordPress website files are required for WordPress to function at all, your personal WordPress website data is stored inside of the WordPress database. Losing the files for WordPress can cause your website to be down for an extended period of time; however, losing your WordPress database means your website is lost forever if you do not have a backup of the database or can somehow restore the database.

**Having a plan for backing up WordPress is extremely important. It is possibly more important than keeping WordPress secure in the first place. Even though your hosting provider may keep automatic backups, it is best to have multiple different backups from different time periods stored in different places. Ultimately, you are responsible for how well you backup your WordPress website.**

### Backups and Hacked Websites
Backups are an extremely important part of recovering after a website has been attacked and altered by a malicious user. **Restoring from a clean backup predating the time a hack occurs is the only way to guarantee that there are no remaining malicious files and that there are no leftover changes to good files that could enable further attacks.**

### WordPress Backup Plugins
There are several plugins for backing up WordPress files and databases. Backup plugins can let you make convenient, full backups through the WordPress admin dashboard. Some support automatic backups. [WordPress backup plugins can be easily found by searching the plugin directory](https://wordpress.org/plugins/search.php?q=backup). Most plugins allow you to manually create backups that you can then download to your local computer.

#### Cautions About Automatic Backups
Many WordPress backup plugins provide automatic backups. Automating backups can make keeping a recent backup of WordPress extremely convenient; however, if you use a plugin that provides automatic backups of WordPress, you must take some extra steps to keep yourself safe.

Automatic backups can easily fill all of the disk space on your hosting account or server if old backups are not automatically deleted after a certain period of time.

It is also possible to have automatic backups create bad backups when, for example, some change or hack has happened to a WordPress website that goes undetected for long enough for the automatic backups to run. Depending on how long it takes to identify that a hack has occurred or there is some problem with WordPress, the automatic backup plugin may have enough time to overwrite any good backups that had been made before the hack or problem occurred.

Automatic backups can also push your hosting account or server's disk space beyond the limits your hosting provider has for automatically backing up your hosting account or server on their system, if they offer automated backups.

Some hosting providers also do not allow you to keep backups on your hosting account or server and may delete the backups without your consent after a certain period of time.

**Consider reviewing your hosting provider's policies on backups and the storage of backups. Many hosting providers can provide good advice and support for setting up thorough, multi-level backup solutions for WordPress.**

### Manually Backing Up WordPress
You are not required to use a WordPress backup plugin to backup WordPress. The WordPress files and database can be manually copied and exported using a variety of different tools and techniques depending on the levels of access you have to your hosting account's files and databases.

#### Use Hosting Provider's Control Panel or Tools
Most hosting providers use control panels or administrative tools that let you create different kinds of backups through their interfaces. Consult your hosting provider's documentation or contact their support team for assistance using their tools to generate backups of WordPress.

#### Backing Up WordPress Files
WordPress files can be backed up using any tool that allows you to access and to download files from your hosting account. These include but are not limited to FTP clients, command-line/shell clients, and web clients. Consult your hosting provider's documentation or contact their support team for assistance with using FTP, command-line, or web clients to access and to download your files to your computer.

#### Backing Up WordPress Database
The WordPress database is not stored in a file in your hosting account that can be easily or simply downloaded or copied. It must be exported using a database backup tool. Most hosting providers offer tools for accessing and backing up databases. If your hosting account does not have a database management tool, you can install phpMyAdmin, a popular, open-source tool for managing MySQL databases (the WordPress database is usually a MySQL database). [phpMyAdmin's makers have written documentation for installing phpMyAdmin](https://docs.phpmyadmin.net/en/latest/setup.html). After installing phpMyAdmin, you should be able to use your WordPress database username and database password from your wp-config.php file to login using phpMyAdmin.

**phpMyAdmin can be used to manage and make changes to your database in addition to backing up your database. Be careful not to accidentally edit your database through phpMyAdmin.**

To backup a database through phpMyAdmin, select the database in phpMyAdmin by clicking on the name of the database in the tree-view on the left-hand side of the phpMyAdmin page. phpMyAdmin should reload and show the tables in the currently selected database. Next, click on "Export" from the menu on the top of the page. There should be a Quick option and a Custom option for exporting the database. The Quick option is usually good enough for a basic backup. If you choose the Custom option, select all tables in the database, select SQL from the Format drop-down menu, check "Add DROP TABLE", and click Go. The database will then be downloaded through your Internet browser.

#### WordPress uses security keys

The wp-config.php file uses security keys (AUTH_KEY, SECURE_AUTH_KEY, LOGGED_IN_KEY, and NONCE_KEY) to ensure better encryption of information stored in the user's cookies. A good security key should be long (60 characters or longer), random and complicated enough. Hosters should verify that the security keys are set up and that they at least contain alphabetic and numeric characters.

**WordPress Security Key Generator https://api.wordpress.org/secret-key/1.1/salt/ can be used to change your security keys.**

#### Database prefix

WordPress database tables have the same names in all WordPress installations. When the standard wp_ prefix to the database tables' names is used, the whole WordPress database structure is not a secret. Hosters should verify that the prefix to the database tables' names is other than wp_. To secure an existing WordPress installation, turn on the maintenance mode, deactivate all plugins, change the prefix in the configuration file, change the prefix in the database, then re-activate all plugins, refresh the permalink structure, and finally turn off the maintenance mode.
