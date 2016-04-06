# LDAP Addressbook Server for Roundcube

This Howto describes the setup of a simple LDAP addressbook server with [OpenLDAP](http://www.openldap.org) that should be ready for using with Roundcube "out of the box". The goal is to have an addressbook solution similar to the SQL based one, including public and private books, contact groups and configurable fields. On the other side it should be possible to connect with any LDAP addressbook client out there.

This Howto makes some simplifications that are maybe a good choice for a small home server, but not what professionals would prefer:

- the LDAP server runs on the same host as Roundcube does
- the static config file (`slapd.conf`) is used instead of the newer dynamic config directory
- security issues are not part of this Howto, nevertheless it is highly recommended to disallow connections from other hosts than needed
- this Howto is based and tested on *Debian Lenny* and *Ubuntu 10.10*, but other Distros (and OS?) should do it as well
- contacts and groups are located in the same base directory, since RC can probably use the contact groups even when a (strange) LDAP server do not support it (?)

## Installing the LDAP Server

Install at least the following packages (maybe they are called different on your distro?):

- `slapd`: the OpenLDAP server daemon
- `ldap-utils`: LDAP tools like ldapsearch and ldapadd
- `php5-ldap`: the PHP bindings later used by Roundcube

E.g. on Debian based systems do:

    $ sudo apt-get install slapd ldap-utils php5-ldap

Depending on your distribution (e.g. on *Debian Lenny*), you will be asked during the installation about:

- domain name = *localhost*
- organisation = *LDAP Addressbook Server*
- administrator password = *mypasswd*

The proposed answers for the domain name (also called 'suffix') fit well with this Howto: if you want to use another, you have to know (or even find out) how to adapt the following steps!
Please change the password to your favorite one!

E.g. on Debian based systems, you can redo this preconfiguration:

    $ sudo dpkg-reconfigure slapd

If you are not asked about the above, e.g. like on *Ubuntu 9.10* and later, you have to define everything in the configuration file (see below). If so, you have to generate a administrator password first:

    $ sudo slappasswd
    New password:
    Re-enter new password:
    {SSHA}bCiMXssO6JJ2ZsPikd1qjNuWhApr+fHr

Remember (or even copy) the last line for later use.

## Configuring the LDAP Server

OpenLDAP supports two types of configuration:

1. the static config file, usually `/etc/ldap/slapd.conf`
2. the newer dynamic config directory, usually `/etc/ldap/slapd.d/`

Some distros like *Debian Lenny* still preconfigure the config file.
Others like *Ubuntu 9.10* and later are using the config directory instead: in this case you have to change this default behaviour first!

E.g. in *Ubuntu 10.10* you have to edit the file */etc/default/slapd* and change the first entry:

    SLAPD_CONF=/etc/ldap/slapd.conf
    SLAPD_USER="openldap"
    SLAPD_GROUP="openldap"

In some distros the ldap config path can be different, e.g. in centos it is "/etc/openldap/slapd.conf".
By the way, remember the user and group of the slapd daemon, usually *openldap*.

Now you have to create/modify the config file `/etc/ldap/slapd.conf`:
- [slapd.conf](https://gist.github.com/rcubetrac/035af863abea7d89723225739a410e83#file-slapd-conf)
This example config file should just work for the Roundcube LDAP addressbook server described here, but maybe not for other LDAP solutions. Some words about this example configuration:
- compared to the default `slapd.conf` file of OpenLDAP, all non-relevant comments are removed.
- the nis schema is removed because the simple addressbook do not need it.
- if you use the proposed config file, open it and change the password (*rootpw*, use slappasswd to create it).

After you created/modified it, set restrictive permissions for the config file: since the password is stored inside, normal user must not be able to read it!
User and group must correspond with the ones you found above in */etc/default/slapd* or even with the ones your LDAP is running with.

    $ sudo chmod 640 /etc/ldap/slapd.conf
    $ sudo chown openldap.openldap /etc/ldap/slapd.conf

Restart the OpenLDAP server now, e.g. on Debian based systems do:

    $ sudo invoke-rc.d slapd restart

If you do not find any errors here, your LDAP server is ready now to become your LDAP addressbook server :-)


## Setup the LDAP Server

Once the OpenLDAP server is running, you can start to set it up. First of all, it could be a good choise to check if you can even access it:

    $ ldapsearch -xLLL -H ldap://localhost:389 -D cn=admin,dc=localhost -W -b dc=localhost
    Enter LDAP Password:
    No such object (32)

The password must correspond withe the *rootpw* in the config file, the -D option corresponds with the *rootdn* and the -b with the *suffix*. If you get *No such object (32)*, this means that the LDAP directory is still empty, thus is ready to be filled now.

We have to setup now a directory structure such that Roundcube can operate on it. Download the following shell script, configure the first few lines in it, and execute it with admin privileges on the server (use sudo or even run it as root): [rcabook-setup.sh](https://gist.github.com/rcubetrac/035af863abea7d89723225739a410e83)

You should get something like that:

    $ sudo bash rcabook-setup.sh
    This script prepares an openLDAP server for a simple
    addressbook, working "out of the box" with Roundcube:
    
      server: ldap://localhost:389
      org   : LDAP Addressbook Server
      config: /etc/ldap/slapd.conf
      suffix: dc=localhost
      rootdn: cn=admin,dc=localhost
    
    -create the openLDAP base directory: dc=localhost
      (as LDAP administator: cn=admin,dc=localhost)
      Enter LDAP Password:
    adding new entry "dc=localhost"
    
    -create addressbook base directory: ou=rcabook,dc=localhost
      (as LDAP administator: cn=admin,dc=localhost)
      Enter LDAP Password:
    adding new entry "ou=rcabook,dc=localhost"
    
    -create the addressbook user: cn=rcuser,ou=rcabook,dc=localhost
      (as LDAP administator: cn=admin,dc=localhost)
      Enter LDAP Password:
    adding new entry "cn=rcuser,ou=rcabook,dc=localhost"
    
    -create subdirectory for public contacts: ou=public,ou=rcabook,dc=localhost
      (as Roundcube user: cn=rcuser,ou=rcabook,dc=localhost)
    adding new entry "ou=public,ou=rcabook,dc=localhost"
    
    -create subdirectory for private addressbooks: ou=private,ou=rcabook,dc=localhost
      (as Roundcube user: cn=rcuser,ou=rcabook,dc=localhost)
    adding new entry "ou=private,ou=rcabook,dc=localhost"
    
    The LDAP addressbook is ready now for using:
      base_dn: ou=rcabook,dc=localhost
      bind_dn: cn=rcuser,ou=rcabook,dc=localhost
    
    Use the following command for reading and checking your setup:

      ldapsearch -xLLL -H ldap://localhost:389 -D cn=rcuser,ou=rcabook,dc=localhost -w rcpass -b ou=rcabook,dc=localhost

If you run the proposed ldap search query, you should get something like:

    $ ldapsearch -xLLL -H ldap://localhost:389 -D cn=rcuser,ou=rcabook,dc=localhost -w rcpass -b ou=rcabook,dc=localhost
    dn: ou=rcabook,dc=localhost
    ou: rcabook
    objectClass: top
    objectClass: organizationalUnit
    
    dn: cn=rcuser,ou=rcabook,dc=localhost
    cn: rcuser
    userPassword:: e1NTSEF9L3NGVmQzTlFud1IvbXNYN0ZDUTV0cjBiUWIyK3RxY0g=
    objectClass: organizationalRole
    objectClass: simpleSecurityObject
    
    dn: ou=public,ou=rcabook,dc=localhost
    ou: public
    objectClass: top
    objectClass: organizationalUnit
    
    dn: ou=private,ou=rcabook,dc=localhost
    ou: private
    objectClass: top
    objectClass: organizationalUnit

If you see at least this 4 entries, your LDAP addressbook server is now ready to become filled with contacts.


## Configuring Roundcube

The following example configurations (only the important fields are shown!) fits for a pbulic and a private LDAP addressbook working with the here described LDAP server setup:

```php
$config['ldap_public']['public'] = array(
    'name'              => 'Public LDAP Addressbook',
    'hosts'             => array('localhost'),
    'port'              => 389,
    'user_specific'     => false,
    'base_dn'           => 'ou=public,ou=rcabook,dc=localhost',
    'bind_dn'           => 'cn=rcuser,ou=rcabook,dc=localhost',
    'bind_pass'         => 'rcpass',
    'filter'            => '(objectClass=inetOrgPerson)',
    'groups'            => array(
        'base_dn'         => '',     // in this Howto, the same base_dn as for the contacts is used
        'filter'          => '(objectClass=groupOfNames)',
        'object_classes'  => array("top", "groupOfNames"),
    ),
);

$config['ldap_public']['private'] = array(
    'name'            => 'Private LDAP Addressbook',
    'hosts'           => array('localhost'),
    'port'            => 389,
    'user_specific'   => true,
    'base_dn'         => 'cn=%u,ou=private,ou=rcabook,dc=localhost',
    'bind_dn'         => 'cn=%u,ou=private,ou=rcabook,dc=localhost',
    'bind_pass'       => '',   // the user login password is used
    'filter'          => '(objectClass=inetOrgPerson)',
    'groups'          => array(
        'base_dn'        => '',     // in this Howto, the same base_dn as for the contacts is used
        'filter'         => '(objectClass=groupOfNames)',
        'object_classes' => array("top", "groupOfNames"),
    ),
);
```

Remark: the contact group features are included not before RC version 0.6
Remark: the `%x` replacement for the `base_dn` do not work before RC version 0.6


## Other Clients than Roundcube

There exists a lot of addressbook clients that can connect to a LDAP server. The most of them do not support contact groups yet, and the number of supported contact fields is often verry limited (please let me now if your experiences are different).

Usually you have to set the following fields:

- the hostname, or even the IP address
- the ldap port: 389
- the bind_dn: "cn=rcuser,ou=rcabook,dc=localhost"
- the bind_pw: "rcpass"
- the base_dn: "ou=public,ou=rcabook,dc=localhost"
- the filter: "(object_class=inetOrgPerson)"


## Microsoft Active Directory as Roundcube Addressbook
To use Microsoft AD (Active Directory) as Roundcube's Addressbook, add the section `$config['ldap_public']`

seen below to your `config.inc.php`.

MyAdLdap  : This is an arbitrary name.
Big Company, Inc : This is your addressbook name
masterserver.company.net : Active Directory server
CN=users,DC=company,DC=net : The Base DN for the users
ldap@company.net  : Active Directory user, with Read-Only capabilities over the whole directory
ADsecretpassword   : ldap@company.net 's Active Directory Password

```php
$config['ldap_public'] = array(
    'MyAdLdap' =>array (
        'name' => 'Big Company, Inc',
        'hosts' => array('masterserver.company.net'),
        'sizelimit' => 6000,
        'port' => 3268, # See comments below
        'use_tls' => false,
        'user_specific' => false,
        'base_dn' => 'CN=users,DC=company,DC=net',
        'bind_dn' => 'ldap@company.net',
        'bind_pass' => 'ADsecretpassword',
        'writable' => false,
        'ldap_version' => 3,
        'search_fields' => array(
           'mail',
           'cn',
        ),
        'name_field' => 'cn',
        'email_field' => 'mail',
        'surname_field' => 'sn',
        'firstname_field' => 'givenName',
        'sort' => 'sn',
        'scope' => 'list',
        'filter' => '(&(mail=*)(|(&(objectClass=user)(!(objectClass=computer)))(objectClass=group)))',
        'global_search' => true,
        'fuzzy_search' => true
    ),
);
```

## Important

When connecting to AD, you may need to use port 3268. Then again, not all LDAP fields are available in port 3268. Use whatever works. http://technet.microsoft.com/en-us/library/cc978012.aspx
