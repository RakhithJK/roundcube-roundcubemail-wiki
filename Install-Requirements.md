## Server Requirements

(for stable versions 1.3.x, 1.4.x and 1.5.x)

 * Apache, Lighttpd, Cherokee, Hiawatha or Nginx web server
 * Directory on the Web server allowed to run scripts
 * If using Apache, `.htaccess` support or configuration to override `DirectoryIndex`
 * PHP version 5.4.1 or greater (and < 8.0 **) with
    * PCRE (Perl-Compatible Regular Expressions)
    * DOM
    * JSON
    * XML
    * Mbstring
    * OpenSSL
    * Session support
    * Socket support
    * PHP Data Objects (PDO) with driver for either MySQL, PostgreSQL, SQL Server or SQLite
    * Internationalisation support (since Roundcube 1.5-rc)
    * Iconv (optional)
    * FileInfo (optional)
    * Zip (optional)
    * Pspell (optional)
 * PEAR packages distributed with Roundcube or external:
   * Mail_Mime 1.10.0 or newer
   * Net_SMTP 1.7.1 or newer
   * Net_Socket 1.2.1 or newer
   * Net_IDNA2 0.1.1 or newer
   * Auth_SASL 1.1.0 or newer
   * Net_Sieve 1.4.0 or newer (for managesieve plugin)
   * Crypt_GPG 1.6.1 or newer (for enigma plugin)
   * Net_LDAP2 2.2.0 or newer (for LDAP address books)
   * [kolab/Net_LDAP3](https://git.kolab.org/diffusion/PNL/php-net_ldap.git) 1.0.6 or newer (for LDAP address books)
 * php.ini options:
    * error_reporting E_ALL & ~E_NOTICE
    * memory_limit > 16MB (increase as suitable to support big mailboxes)
    * file_uploads enabled
    * session.auto_start disabled
    * suhosin.session.encrypt disabled
    * mbstring.func_overload disabled
 * If using MySQL or PostgreSQL, a database server and database user with permission to create tables
 * An IMAP server which supports IMAP 4 rev 1
 * A SMTP server

> ** PHP 8 will be supported with Roundcube 1.5

## Supported browsers (version 1.3.x)

 * Internet Explorer 10 (Windows 7)
 * Internet Explorer 11 (Windows 8)
 * Microsoft Edge (Windows 10)
 * Safari 9+ (Mac OS X)
 * Firefox 4+ (Windows XP, Linux)
 * Firefox 30+ (Windows, Mac OS X, Linux)
 * Google Chrome 52+ (Mac OS X, Windows, Linux)


## Tested browsers (version 1.2.x)

 * Internet Explorer 10 (Windows 8)
 * Internet Explorer 9 (Windows 7)
 * Internet Explorer 8 (Windows XP/7) - requires legacy_browser plugin since Roundcube 1.1
 * Internet Explorer 7 (Windows XP) - requires legacy_browser plugin since Roundcube 1.1
 * Safari 3+ (Mac OS X 10.5 and Windows XP)
 * Firefox 3.6 (Windows XP, Linux) - requires legacy_browser plugin since Roundcube 1.1
 * Firefox 4+ (Windows, Linux)
 * Google Chrome 9+ (Mac OS X, Windows 7, Linux)
