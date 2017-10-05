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

### Server Level

### Plugins

## File System

### File Permissions

### User Accounts

### Uploads vs. Core Files

## WordPress Users and Roles
