## How to report issues?

So you think you found an issue, huh? - First off, we really appreciate all feedback we get. To handle all the traffic, we ask you to setup a ticket on our trac (you are already on it, reading this) and take into account all of the following when you're creating it.  _You'll need to register for an account before you'll be able to create new tickets._

*I know this is probably a pain to read, but please do it so we can straighten out all issues sooner than later.*

### Most current version

Please understand that Roundcube is a very young project. So because development never stops and in order to ease the burden on us, we hereby ask you to test your issues always against the latest available version from [git](/roundcube/roundcubemail) or click this link directly [Latest version from master](https://github.com/roundcube/roundcubemail/archive/master.zip)

### Check list

 * What's your PHP version? (Please make sure this is up to date!)
 * What's your mail server? (Please make sure this is up to date!)
 * What browser/operating system did you use, any special settings/plugins?
 * What did the logs say? (*see below*, How to use the logs?)
 * Is the behavior reproducible? (*see below*, Samples)

### Keeping your system up to date

Roundcube is tested in current environments, so if for example your mailserver has not been updated in over a year, please do this *first* to confirm your issue.

Mailserver issues are not the only thing to keep in mind - PHP updates are there for several reasons. Performance, security and features. We test against _recent_ version of PHP 5, so please update it first and confirm your issue.

### How to use the logs?

#### How to enable them?

Roundcube has a configuration option which logs all errors to a log file located in `<webmail>/logs/` (assuming `<webmail>` is the directory of your Roundcube install).

The debug_level in `config/config.inc.php` should look like this (1 = logging):

    $config['debug_level'] = 1;

Chances are good that there is a more detailed explanation of what went wrong in the `errors` log file inside the above mentioned logs directory. If you see a blank screen, that indicates a PHP fatal error. Check the web server's default error log for details.

#### Enable debug logging

You may be asked to provide debug log data for IMAP, SMTP, LDAP or SQL protocols. In order to enable those, add one or multiple of the following options to your main config file:

```php
  // Log SQL queries to <log_dir>/sql or to syslog
  $config['sql_debug'] = true;
  
  // Log IMAP conversation to <log_dir>/imap or to syslog
  $config['imap_debug'] = true;
  
  // Log LDAP conversation to <log_dir>/ldap or to syslog
  $config['ldap_debug'] = true;
    
  // Log SMTP conversation to <log_dir>/smtp or to syslog
  $config['smtp_debug'] = true;
```

#### How to read them?

The logs give you plenty of info when it comes to problems, please consider solving the problem first and then if all fails create a ticket. You may also use our [mailing lists](http://lists.roundcube.net) and [forums](http://roundcubeforum.net/) where people may be able to help you especially when the issue is related to the configuration of your environment, rather than Roundcube itself.

### Samples

Even though there are tons of RFCs on email, it seems to be a rather 'lax standard by how different mailservers and mailclients interpret it. If you find out that a problem can be reproduced with a certain email, please attach this email to a ticket in our bugtracker.

### Patches

Yes, we like patches - even if we may not apply them word by word they give us an idea and jumpstart us on your issue. We also credit accordingly. :)

If you'd like to contribute a patch, please fork our [git repository](https://github.com/roundcube/roundcubemail), commit the modifications to your fork and then submit a pull request directly via Github.

### Translations

For translation updates or corrections please go directly to our [transifex.com](https://www.transifex.com/projects/p/roundcube-webmail/) page and correct them there. We'll periodically sync them back to our git repositories.


### Debugging Roundcube

To debug Roundcube, we suggest you use [Xdebug](http://xdebug.org).

Xdebug has the ability to profile PHP code. The profiler is very detailed and allows you to see how much time is spend in certain parts of the code.

#### Installation & Setup

```
  pecl install xdebug
  echo "zend_extension=xdebug.so" >> /etc/php/php.ini
```

The second command is optional and depends on your PHP installation, etc..

If you do not have the `pecl` command available, you can get it by installing [PEAR](http://pear.php.net/). For more notes on installing Xdebug, please check out [the official documentation](http://www.xdebug.org/docs/install).

#### Configure Xdebug

The following should be added to `php.ini` or your `xdebug.ini`:
```
    xdebug.profiler_enable=1
    xdebug.profiler_output_dir=/tmp
```
Please be adviced, that the files Xdebug creates can eat a lot of disk space fast. So make sure to disable it when you're done debugging so you don't run out of disk space.