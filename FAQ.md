# Frequently Asked Questions

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
