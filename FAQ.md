# Frequently Asked Questions

## How to export multiple email messages at once?

It is possible with `zipdownload` plugin. With the plugin enabled and its `zipdownload_selection` option configured, you will be able to download multiple selected messages in one archive file. A new More > Download menu will contain three new options. Note that maximum size of the archive can be specified in configuration (from version 1.4-beta).

### Configuring the `zipdownload` plugin

The plugin is already shipped with the Roundcube packages but not enabled by default because it adds some requirements to the webserver Roundcube is installed on.

1. Make sure your PHP installation includes the [Zip](http://php.net/manual/en/book.zip.php) extension.
2. [Enable the plugin](/roundcube/roundcubemail/wiki/Plugin-API#installing-and-activating-plugins) by adding "zipdownload" to the list of plugins in Roundcube's `config/config.inc.php` file.
3. Enable the `zipdownload_selection` option by setting up the plugin config:
   1. Copy the plugin config file `plugins/zipdownload/config.inc.php.dist` into `config/zipdownload.inc.php`
   2. Edit the copied file and set `$config['zipdownload_selection'] = true;`


## "server certificate verification failed" on Composer install

This error can appear when installing Roundcube's dependencies via Composer, including the `kolab/Net_LDAP3` package from git.kolab.org.

The certificate on git.kolab.org is issued by the intermediate CA COMODO RSA Domain Validation Secure Server CA. This CA has to be among the installed CA certificates on the server issuing the request to git.kolab.org. While this is already the case for most systems, some distributions might not have that CA certificate installed by default. When it is not, connection fails. The following command adds the missing certificate:

Do as root:
```
echo -n | openssl s_client -connect git.kolab.org:443 | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p'| tee '/usr/local/share/ca-certificates/git_kolab_org.crt'
```
followed by
```
update-ca-certificates
```
