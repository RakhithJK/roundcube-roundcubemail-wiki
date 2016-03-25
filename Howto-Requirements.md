## Server Requirements

(for stable version 1.1)

 * Apache, Lighttpd (>=1.4.13 for SSL), Cherokee, Hiawatha or Nginx web server
 * Directory on the Web server allowed to run scripts
 * If using Apache, .htaccess support or configuration to override DirectoryIndex
 * PHP version 5.3.7 or greater with
    * PCRE (Perl-Compatible Regular Expressions)
    * DOM
    * JSON
    * XML
    * Session support
    * Socket support
    * PHP Data Objects (PDO) with driver for either MySQL, PostgreSQL or SQLite (required)  
      _Note: MySQL database driver requires PHP 5.3 or newer_
    * iconv (recommended)
    * OpenSSL (recommended)
    * Mbstring (optional)
    * !FileInfo (optional)
    * Mcrypt (optional)
    * Zip (optional)
    * Pspell (optional)
 * PEAR packages distributed with Roundcube or external:
   * Mail_Mime 1.9.0 or newer
   * Net_SMTP 1.6.3 or newer (get latest from https://github.com/pear/Net_SMTP/)
   * Net_IDNA2 0.1.1 or newer
   * Auth_SASL 1.0.6 or newer
   * Net_Sieve 1.3.2 or newer (for managesieve plugin)
   * Crypt_GPG 1.2.0 or newer (for enigma plugin)
   * Net_LDAP2 2.0.12 or newer (for LDAP address books)
   * [kolab/Net_LDAP3](https://git.kolab.org/diffusion/PNL/php-net_ldap.git) dev-master (for LDAP address books)
 * php.ini options:
    * error_reporting E_ALL & ~E_NOTICE (or lower)
    * memory_limit > 16MB (increase as suitable to support large attachments)
    * file_uploads enabled (for attachment upload features)
    * session.auto_start disabled
    * zend.ze1_compatibility_mode disabled
    * suhosin.session.encrypt disabled
    * mbstring.func_overload disabled
    * magic_quotes_runtime disabled
    * magic_quotes_sybase disabled
 * If using MySQL or PostgreSQL, a database server and database user with permission to create tables
    * If using MySQL 5.0.2 or later, disable STRICT_TRANS_TABLES and STRICT_ALL_TABLES
 * OpenSSL and Socket modules for PHP required to connect to secure IMAP or IMAPS, for secure SMTP and to use the spell checker
    * Additionally, the CURL module for PHP is required for spell checking with TinyMCE (HTML WYSIWYG Editor).
 * An IMAP server which supports IMAP 4 rev 1
 * An SMTP server (recommended) or PHP configured for mail delivery

## Browser Requirements

 * JavaScript enabled
 * Accept cookies
 * Support for XMLHttpRequest
 * CSS2 Support

## Tested browsers

 * Internet Explorer 7 (Windows XP) - _requires legacy_browser plugin since Roundcube 1.1_
 * Internet Explorer 8 (Windows XP/7) - _requires legacy_browser plugin since Roundcube 1.1_
 * Internet Explorer 9 (Windows 7)
 * Internet Explorer 10 (Windows 8)
 * Safari 3+ (Mac OS X 10.5 and Windows XP)
 * Firefox 3.6 (Windows XP, Linux) - _requires legacy_browser plugin since Roundcube 1.1_
 * Firefox 4+ (Windows, Linux)
 * Google Chrome 9+ (Mac OS X, Windows 7, Linux)

## Browsers reported to work

 * Camino 1.5.x (Mac OS X 10.4)
 * Opera 9.25 (Windows Server 2003, Windows XP, and FreeBSD 6)
 * Opera 9.30 (Wii, TinyMCE is non-functional)
 * Opera 9.60 (Windows XP)
 * Opera 11.x (Windows XP/7, Mac OS X)
 * SeaMonkey v2.8 (Windows XP/7, Linux)