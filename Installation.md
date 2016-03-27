# How to install Roundcube

## Introduction

So you've read up on what Roundcube is, and what it can do.  But of course, you can't really know if you like it or not, unless you install it and use it for yourself for a week or two.  This document will help guide you through a standard installation of Roundcube.  We recommend you read this guide to familiarize yourself with how to install Roundcube, but for those who just want to get up and going, there is a shell script at the bottom to automate the installation and have you running almost instantly.

### Other tutorials

There's a nice [how-to](http://www.hmailserver.com/forum/viewtopic.php?t=5591) about the installation of Roundcube on a Windows box with IIS6 and hMailServer. *NOTE:* Make sure you set temp_dir in main.inc.php to an absolute path as otherwise users may run into issues with attaching files to emails.

## Installation

### Get Roundcube!

To get started, you need to download Roundcube. The easiest way to get it is to visit http://www.roundcube.net and click on "Downloads".  Download the archive file containing Roundcube (name should end in `.tar.gz`) and extract its contents (on Windows, with WinZip or 7-Zip, on Mac/Unix with `tar xfz roundcubemail-xx.tar.gz` or `gunzip -c roundcube-xx.tar.gz | tar xf -`) in the current directory.

### Install dependecies

If you didn't download the "complete" package, 3rd party libraries still need to be installed or updated for your Roundcube installation. This is done using [Composer](https://getcomposer.org):

 1. Get composer from [getcomposer.org](https://getcomposer.org/download/)
 2. Rename the `composer.json-dist` file into `composer.json`
 3. if you want to use LDAP address books, enable the LDAP libraries in your `composer.json` file by moving the items from "suggest" to the "require" section:  
```
"require": {
  ...
  "pear-pear.php.net/net_ldap2": ">=2.0.12",
  "kolab/Net_LDAP3": "dev-master"
}
```  
  4. run `php composer.phar install --no-dev`

> Please note that this requires shell access to the webserver. If you don't have that,
> download the "complete" package and copy the `vendor` directory into the Roundcube
> installation directory. That already contains all the dependencies you'd otherwise
> install with Composer.

### Get it ready

Now that we've got our files, we can upload the whole directory to the web server (using your favorite [scp or FTP program](http://www.pcwdld.com/top-10-free-tftp-servers)) in case you're not already working there.

Roundcube needs to save some temp files and it also writes logs. Therefore make sure that the following directories (and the files within) are writable by the web server user:
 * `temp`
 * `logs`

### Database Configuration

Next thing we need to do is decide what database backend we'll use. The most common is MySQL but others are PostgreSQL and SQLite. 
So once you decide, create a database with any name you want and grant privileges to a separate database user. It's recommended not to use an existing user or root.

With MySQL you can set up the database by issuing the following commands:
```
CREATE DATABASE roundcubemail;
GRANT ALL PRIVILEGES ON roundcubemail.* TO username@localhost IDENTIFIED BY 'password';
```
(of course you have to replace the database, username and password accordingly)

See the `INSTALL` file for information about setting up PostgreSQL or SQLite

If you are using MySQL, be sure to flush the users privileges when you add a new user or you will get a database connection error:
```
FLUSH PRIVILEGES;
```
Note that preconfigured database tables are included in the SQL folder. Import or restore your version or you may get a 500 Error.

### Configuring Roundcube

After uploading the files point your browser to `http://url-to-roundcube/installer/` to start the install wizard.
The first page shows some requirements, and when you click "START INSTALLATION", the installer checks if everything is there. In case you see some red *NOT OK* messages, you need to install or enable something. Follow the links or find out more by searching your web site for your server's operating system or http://www.php.net.

Once your web server is ready to run Roundcube you can start creating the config files on the next step. Click "NEXT" to get there.
Get through the form and change the settings according to your needs.  Don't forget to enter the database credentials within the "Database Setup" section.  
All the config parameter are described with a few words. If you don't know that a setting means, find out more on the [[Configuration]] page or just trust the defaults.

When finished the configuration hit the "CREATE CONFIG" button at the bottom of the page. You now get a text box on top of your browser window showing the configuration. Copy the content of that text box and save it into a file named `config.inc.php` and copy/upload that into the `config/` directory of your Roundcube installation. _Warning:_ Pasting directly into an editor such as nano may not work due to word-wrapping. Please use vi or download the file directly instead.

Finally click "CONTINUE" and get to the last step of the install process. Now your configuration is being verified tested against your webserver.  
Click the "Initialize database" button in you're requested to in order to create the necessary tables in your database.

If there are no red *NOT OK* messages, you can also try to send a mail in order to test the SMTP settings.

Last but not least you have to remove the whole installer directory from the webserver. If this remains active it can expose the configuration including passwords.

### Protect your installation

Access through your webserver to at least the following directories should be denied:
 * `/config`
 * `/temp`
 * `/logs`

Roundcube use .htaccess files to protect this directories, be sure to allow override of the `Limit` directives to get them taken into account.

## Conclusion

This is a very basic setup to get you up and running with Roundcube in less than twenty minutes.  There are plenty of other options, and a lot more options to investigate. See [wiki:Howto_Config] or browse the [forums](http://www.roundcubeforum.net) for other tricks and modifications, as well as support if you just can't get it working.

Have fun with your new Roundcube installation!!

## Troubleshooting

*500 Internal Server Error*::
   This is a very common problem.  The likely cause is AllowOverride Apache directive is in effect. Try to comment all the lines in .htaccess in the document root and then uncomment one line at a time to find which directives in .htaccess cause the error. If these directives protect some critical files from downloading, ask your hoster or administrator to give you more AllowOverride rights or include the problem directives from .htaccess file into administrator maintained configuration file.

*Using MySQL - Database Error | Failed Connection*
   Make sure your database connection string is correct. If you are using MySQL 4.1 or above, your client libraries may not support the new password encryption protocol:
   http://dev.mysql.com/doc/refman/5.0/en/old-client.html

*Other Issues*
   If you're still having trouble after following the steps above, check out the [support page](http://roundcube.net/support) where you'll find information about our forum or the mailing list. We also answered some [Frequently Asked Questions](FAQ/) concerning Roundcube.

## Shell Script

> Coming Soon