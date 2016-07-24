# Creating a new release

How do we release a new version of Roundcube? This document aims to provide an answer.

## Versioning

Syntax: x.y.z

 * *x* = epic
 * *y* = major
 * *z* = minor

## 1. Creating a release branch

 * Copy current master into a release branch
```
git checkout master
git checkout -b release-x.y
git push origin release-x.y
git config branch.release-x.y.merge refs/heads/release-x.y
git config branch.release-x.y.remote origin
```
 * Remove development stuff:
```
git rm bin/dumpschema.sh bin/makedoc.sh tests
```
 * edit `CHANGELOG`: Add a "RELEASE x.y.z" title
 * edit `README`: remove the UNSTABLE disclaimer
 * bump up version in `index.php`
 * bump up version in `program/include/iniset.php`
 * bump up version in `program/lib/Roundcube/bootstrap.php`
 * commit the changes
```
git commit -m "Remove development stuff and update versions"
git push
```

## 2. Create Package

### Major Relase

The steps to take are basically

 * clone the release branch from GIT
 * compress the JavaScript and CSS files
 * remove test files and .git meta data
 * create package archive
 * distribute the release package on Github

The process of creating the tarball is packed in a Makefile. Get it from [gist.github.com](https://gist.github.com/2725894#file-makefile) and execute
```
    make [GITBRANCH=release-x.y VERSION=x.y] dependent framework
```
This will produce a tarball named roundcubemail-x.y.tar.gz which can be distributed.

### Minor Release or Hotfix

 * commit changes to the existing release branch
 * repeat the packaging and distribution process
 * adjust naming in case of a hotfix or patch
 * supply a patch in addition: 
```
git diff <last-rev> > ./roundcubemail-patch-x.y.z.patch
gzip ./roundcubemail-patch-x.y.z.patch
```
 * Distribute patch on SourceForge


## 2.1 Create "complete" package

Complete packages do not only contain the Roundcube sources but also have all dependencies
resovled and packed into the tarball. These packages don't require an additional run of
composer but represent a self-contained installation.

To create such a release package, use the above mentioned [Makefile](https://gist.github.com/2725894#file-makefile) and execute

```
make [GITBRANCH=release-x.y VERSION=x.y] complete
```

## 2.2 Signing release packages

The release tarballs are usually signed with GPG to provide a way for consumers to
verify their authencity. The process is to create a detacted ascii-armored signature
of the .tar.gz files. The Makefile already has a target for this action:
```
make [GPGKEY=r41C4F7D5] sign
```
Also verify the signatures before publishing them:
```
make verify
```

## 3. Tagging release in git

The differences between branches and tags are the following:

 * branch may be "patched" or "hotfixed"
 * a tag is just a snapshot and may not be altered
 * tags are signed with GPG
 * tags are the basis for publishing releases on Github

Tags are to be signed with a GPG key. This can be the developers/release
managers identity. So first, tell git which identity to use for signing:
```
git config [--global] user.signingkey 0ABCDEF123
```
Then create a signed tag (with the `-s` option):
```
git checkout release-x.y
git tag -s -a vy.y.z -m "Tagging files for x.y.z"
git push --tags
```

## 4. Publishing the release files

The previously built release files are not published on Github under [releases](https://github.com/roundcube/roundcubemail/releases).
Click the button "Draft a new relaase" and then select the previously created
(signed) tag from the drop-down field.

Give a release title "Roundcube Webmail x.y.z" and write a short summary of the
release and append the Changelog since the last release of that series.

Then, upload the release tarballs along with the signature files.
For beta versions, check the "This is a pre-release" box.

Finally, publish the release with a click on the according button.


## 5. Announcements

 * update downloads page on roundcube.net
 * create a new post on the roundcube.net news feed
 * post notification to announce@, dev@ and users@
 * post on Twitter (@roundcube) and G+
 