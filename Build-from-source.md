# Build Roundcube from Source

Building Roundcube from source is pretty similar to [[Creating a new release]].  
Let's list the individual steps with a short description:

#### 1. Fetch the source from github

```sh
git clone git://github.com/roundcube/roundcubemail.git roundcubemail-git
```

#### 2. Switch to the according branch

```sh
cd roundcubemail-git
git checkout tags/1.1.5
```
(check out whatever tag or branch you desire)

#### 3. Install JavaScript dependencies

(for git master and versions >= 1.3 only)

```sh
bin/install-jsdeps.sh
```

#### 4. Compress Javascript files and add cache-buster tokens to images referenced from CSS styles

```sh
bin/jsshrink.sh
bin/updatecss.sh
```

#### 5. Optionally compress CSS files as well

```sh
bin/cssshrink.sh
```

#### 6. Remove development stuff, installer and git files

```sh
rm transifexpull.sh package2composer.sh importgettext.sh exportgettext.sh README.md INSTALL UPGRADING, LICENSE, CHANGELOG
rm -rf tests/ public_html/ installer/ .git* .tx*
```

#### 7. Download and configure [Composer](https://getcomposer.org)

```sh
curl -sS https://getcomposer.org/installer | php -- --install-dir=/tmp/
cp composer.json-dist composer.json
```

#### 8. Optionally, add dependencies for LDAP modules in order to enable LDAP address books in Roundcube

```sh
php /tmp/composer.phar require pear-pear.php.net/net_ldap2:~2.1.0 kolab/net_ldap3:dev-master --no-update
```

#### 9. Install PHP dependencies using Composer

```sh
php /tmp/composer.phar install --prefer-dist --no-dev
```

The `roundcubemail-git` directory now contains a complete Roundcube installation ready for deployment or packaging.
