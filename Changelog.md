# CHANGELOG

## RELEASE 1.3.9

- Fix TinyMCE download location(s) (#6694)
- Fix bug where a message/rfc822 part without a filename wasn't listed on the attachments list (#6494)
- Fix handling of empty entries in vCard import (#6564)
- Fix bug in parsing some IMAP command responses that include unsolicited replies (#6577)
- Fix PHP 7.2 compatibility in debug_logger plugin (#6586)
- Fix so ANY record is not used for email domain validation, use A, MX, CNAME, AAAA instead (#6581)
- Fix so mime_content_type check in Installer uses files that should always be available (i.e. from program/resources) (#6599)
- Fix missing CSRF token on a link to download too-big message part (#6621)
- Fix bug when aborting dragging with ESC key didn't stop the move action (#6623)
- Fix bug where next row wasn't selected after deleting a collapsed thread (#6655)

## RELEASE 1.3.8

- Fix PHP warnings on dummy QUOTA responses in Courier-IMAP 4.17.1 ([#6374](/roundcube/roundcubemail/issues/6374))
- Fix so fallback from BINARY to BODY FETCH is used also on [PARSE] errors in dovecot 2.3 (#[6383](/roundcube/roundcubemail/issues/6383))
- Enigma: Fix deleting keys with authentication subkeys (#[6381](/roundcube/roundcubemail/issues/6381))
- Fix invalid regular expressions that throw warnings on PHP 7.3 (#[6398](/roundcube/roundcubemail/issues/6398))
- Fix so Classic skin splitter does not escape out of window (#[6397](/roundcube/roundcubemail/issues/6397))
- Fix XSS issue in handling invalid style tag content (#[6410](/roundcube/roundcubemail/issues/6410))
- Fix compatibility with MySQL 8 - error on 'system' table use
- Managesieve: Fix bug where `show_real_foldernames` setting wasn't respected (#[6422](/roundcube/roundcubemail/issues/6422))
- New_user_identity: Fix `%fu`/`%u` vars substitution in user specific LDAP params (#[6419](/roundcube/roundcubemail/issues/6419))
- Fix support for "allow-from <uri>" in `x_frame_options` config option (#[6449](/roundcube/roundcubemail/issues/6449))
- Fix bug where valid content between HTML comments could have been skipped in some cases (#[6464](/roundcube/roundcubemail/issues/6464))
- Fix multiple VCard field search (#[6466](/roundcube/roundcubemail/issues/6466))
- Fix session issue on long running requests (#[6470](/roundcube/roundcubemail/issues/6470))

## RELEASE 1.3.7

- Fix PHP Warning: Use of undefined constant IDNA_DEFAULT on systems without php-intl ([#6244](/roundcube/roundcubemail/issues/6244))
- Fix bug where some parts of quota information could have been ignored ([#6280](/roundcube/roundcubemail/issues/6280))
- Fix bug where some escape sequences in html styles could bypass security checks
- Fix bug where some forbidden characters on Cyrus-IMAP were not prevented from use in folder names
- Fix bug where only attachments with the same name would be ignored on zip download ([#6301](/roundcube/roundcubemail/issues/6301))
- Fix bug where unicode contact names could have been broken/emptied or caused DB errors ([#6299](/roundcube/roundcubemail/issues/6299))
- Fix bug where after "mark all folders as read" action message counters were not reset ([#6307](/roundcube/roundcubemail/issues/6307))
- Enigma: [EFAIL] Don't decrypt PGP messages with no MDC protection ([#6289](/roundcube/roundcubemail/issues/6289))
- Fix bug where some HTML comments could have been malformed by HTML parser ([#6333](/roundcube/roundcubemail/issues/6333))

## RELEASE 1.3.6

 * Fix parsing date strings (e.g. from a Date: mail header) with comments ([#6216](/roundcube/roundcubemail/issues/6216))
 * Fix PHP 7.2: count(): Parameter must be an array in enchant-based spellchecker ([#6234](/roundcube/roundcubemail/issues/6234))
 * Fix possible IMAP command injection and type juggling vulnerabilities ([#6229](/roundcube/roundcubemail/issues/6229))
 * Enigma: Fix key selection for signing
 * Enigma: Enable keypair generation on Internet Explorer 11
 * Fix `check_request()` bypass in places using `get_uids()` [CVE-2018-9846](https://www.cvedetails.com/cve/CVE-2018-9846/) ([#6238](/roundcube/roundcubemail/issues/6238))
 * Fix bug where usernames without domain part could be malformed or converted to lower-case on logon ([#6224](/roundcube/roundcubemail/issues/6224))


## RELEASE 1.3.5

 * Managesieve: Fix bug where text: syntax was forced for strings longer than 1024 characters ([#6143](/roundcube/roundcubemail/issues/6143))
 * Managesieve: Fix missing Save button in Edit Filter Set page of Classic skin ([#6154](/roundcube/roundcubemail/issues/6154))
 * Fix duplicated labels in Test SMTP Config section ([#6166](/roundcube/roundcubemail/issues/6166))
 * Fix PHP Warning: exif_read_data(...): Illegal IFD size ([#6169](/roundcube/roundcubemail/issues/6169))
 * Enigma: Fix key generation in Safari by upgrade to OpenPGP 2.6.2 ([#6149](/roundcube/roundcubemail/issues/6149))
 * Fix security issue in remote content blocking on HTML image and style tags ([#6178](/roundcube/roundcubemail/issues/6178))
 * Added 9pt and 11pt to the list of font sizes in HTML editor
 * Fix handling encoding of HTML tags in "inline" JSON output ([#6207](/roundcube/roundcubemail/issues/6207))
 * Fix bug where some unix timestamps were not handled correctly by rcube_utils::anytodatetime() ([#6212](/roundcube/roundcubemail/issues/6212))

## RELEASE 1.3.4

 * Fix a couple of warnings on PHP 7.2 ([#6098](/roundcube/roundcubemail/issues/6098))
 * Fix bug where contacts search could skip some records ([#6130](/roundcube/roundcubemail/issues/6130))
 * Fix possible information leak - add more strict sql error check on user creation ([#6125](/roundcube/roundcubemail/issues/6125))
 * Fix broken long filenames when using imap4d server - workaround server bug ([#6048](/roundcube/roundcubemail/issues/6048))
 * Fix so temp_dir misconfiguration prints an error to the log ([#6045](/roundcube/roundcubemail/issues/6045))
 * Fix untagged COPYUID responses handling - again ([#5982](/roundcube/roundcubemail/issues/5982))
 * Fix PHP warning "idn_to_utf8(): INTL_IDNA_VARIANT_2003 is deprecated" with PHP 7.2 ([#6075](/roundcube/roundcubemail/issues/6075))
 * Fix bug where Archive folder wasn't auto-created on login with create_default_folders=true
 * Fix performance issue when parsing malformed and long Date header ([#6087](/roundcube/roundcubemail/issues/6087))
 * Fix syntax error in mssql.initial.sql ([#6097](/roundcube/roundcubemail/issues/6097))
 * Fix bug where contacts export by selection returned no more than 10 entries ([#6103](/roundcube/roundcubemail/issues/6103))
 * Fix searching contacts by address in LDAP source ([#6084](/roundcube/roundcubemail/issues/6084))
 * Fix X-Frame-Options: ALLOW-FROM support, remove custom click-jacking protection ([#6057](/roundcube/roundcubemail/issues/6057))


## RELEASE 1.3.3

- Fix decoding of mailto: links with + character in HTML messages ([#6020](/roundcube/roundcubemail/issues/6020))
- Fix false reporting of failed upgrade in `installto.sh` ([#6019](/roundcube/roundcubemail/issues/6019))
- Fix file disclosure vulnerability caused by insufficient input validation [CVE-2017-16651] ([#6026](/roundcube/roundcubemail/issues/6026))
- Fix mangled non-ASCII characters in links in HTML messages ([#6028](/roundcube/roundcubemail/issues/6028))

## RELEASE 1.3.2

 * Improve detection for Egde browser and add pointer event support ([#5922](/roundcube/roundcubemail/issues/5922))
 * Fix bug where pink image was used instead of a thumbnail when image resize fails ([#5933](/roundcube/roundcubemail/issues/5933))
 * Fix so files size/count limit is verified (client-side) also on drag-n-drop uploads ([#5940](/roundcube/roundcubemail/issues/5940))
 * Fix invalid template loading on a message error in preview frame ([#5941](/roundcube/roundcubemail/issues/5941))
 * Fix bug where HTML messages could have been rendered empty on some systems ([#5957](/roundcube/roundcubemail/issues/5957))
 * Fix wording of "Mark previewed messages as read" to "Mark messages as read" ([#5952](/roundcube/roundcubemail/issues/5952))
 * Enigma: Fix decryption of messages encoded with non-ascii charset ([#5962](/roundcube/roundcubemail/issues/5962))
 * Fix missing cursor in HTML editor on mail reply ([#5969](/roundcube/roundcubemail/issues/5969))
 * Fix (again) bug where image data URIs in css style were treated as evil/remote in mail preview ([#5580](/roundcube/roundcubemail/issues/5580))
 * Fix bug where mail search could return empty result on servers without SORT capability ([#5973](/roundcube/roundcubemail/issues/5973))
 * Fix bug where assets_path wasn't added to some watermark frames
 * Fix so untagged COPYUID responses are also supported according to RFC6851 ([#5982](/roundcube/roundcubemail/issues/5982))
 * Fix issue caused by non-default session.cookie_lifetime setting ([#5961](/roundcube/roundcubemail/issues/5961))
 * Fix Edge encoding bug when pasting text into the HTML editor, update to TinyMCE 4.5.8 ([#5885](/roundcube/roundcubemail/issues/5885))
 * Fix handling of unknown Content-Disposition type ([#6002](/roundcube/roundcubemail/issues/6002))
 * Fix truncated folder name on messages list in multi-folder mode, for folders with non-ascii characters ([#6004](/roundcube/roundcubemail/issues/6004))
 * Fix bug where removing the last subfolder did not hide toggle button on its parent record ([#6007](/roundcube/roundcubemail/issues/6007))
 * Fix bug where ghost messages could be added to the list after fast delete ([#5941](/roundcube/roundcubemail/issues/5941))

## RELEASE 1.3.1

 * Add Preferences > Mailbox View > Main Options > Layout ([#5829](/roundcube/roundcubemail/issues/5829))
 * Password: Fix compatibility with PHP 7+ in cpanel_webmail driver ([#5820](/roundcube/roundcubemail/issues/5820))
 * Managesieve: Fix parsing dot-staffed lines in multiline text ([#5838](/roundcube/roundcubemail/issues/5838))
 * Managesieve: Fix AM/PM suffix in vacation time selectors
 * Managesieve: Fix bug where 'exists' operator was reset to 'contains' ([#5899](/roundcube/roundcubemail/issues/5899))
 * Remove non-printable characters from filenames on download/display ([#5880](/roundcube/roundcubemail/issues/5880))
 * Fix decoding non-ascii attachment names from TNEF attachments ([#5646](/roundcube/roundcubemail/issues/5646), [#5799](/roundcube/roundcubemail/issues/5799))
 * Fix uninitialized string offset warnings and make sure `random_bytes()` has the requested length ([#5788](/roundcube/roundcubemail/issues/5788))
 * Fix bug where HTML messages with @media styles could moddify style of page body ([#5811](/roundcube/roundcubemail/issues/5811))
 * Fix style issue on selected and unfocused message that is part of a thread ([#5798](/roundcube/roundcubemail/issues/5798))
 * Fix bug where a.button style from managesieve plugin could impact other elements ([#5800](/roundcube/roundcubemail/issues/5800))
 * Fix position of selected icon for (Mailvelope) Encrypt button
 * Fix fatal error when using DMY- or MDY-based date format in PostgreSQL ([#5808](/roundcube/roundcubemail/issues/5808))
 * Fix bug where errors were not printed when using `bin/update.sh` ([#5834](/roundcube/roundcubemail/issues/5834))
 * Fix PHP 7.2 warnings on `count()` use ([#5845](/roundcube/roundcubemail/issues/5845))
 * Fix bug where Chrome could not upload the same file that was selected before ([#5854](/roundcube/roundcubemail/issues/5854))
 * Fix duplicate messages on the list after deleting messages on the next to the last page ([#5862](/roundcube/roundcubemail/issues/5862))
 * Fix bug where messages count was not updated after delete when imap_cache is set ([#5872](/roundcube/roundcubemail/issues/5872))
 * Fix potential XSS vulnerability with malformed HTML message markup
 * Fix sending message with "Too many public recipients" dialog buttons ([#5924](/roundcube/roundcubemail/issues/5924))
 * Bring back double-click behavior on the message list which was removed in 1.3.0 ([#5823](/roundcube/roundcubemail/issues/5823))
 * Enigma: Fix decrypting an encrypted+signed message when signature verification fails ([#5914](/roundcube/roundcubemail/issues/5914))

## RELEASE 1.3.0

 * Update to TinyMCE 4.5.7
 * Fix bug where invalid recipients could be silently discarded ([#5739](/roundcube/roundcubemail/issues/5739))
 * Fix conflict with `_gid` cookie of Google Analytics ([#5748](/roundcube/roundcubemail/issues/5748))
 * Print error from CLI scripts when system/exec function is disabled ([#5744](/roundcube/roundcubemail/issues/5744))
 * Fix bug where comment notation within style tag would cause the whole style to be ignored ([#5747](/roundcube/roundcubemail/issues/5747))
 * Fix bug where it wasn't possible to scroll folders list in Edge ([#5750](/roundcube/roundcubemail/issues/5750))
 * Fix folders list sorting on Windows - if php-intl is available ([#5732](/roundcube/roundcubemail/issues/5732))
 * Fix addressbook searching by gender ([#5757](/roundcube/roundcubemail/issues/5757))
 * Fix prevention from using % and * characters in folder name ([#5762](/roundcube/roundcubemail/issues/5762))
 * Fix POST parameter reflection in default_charset selector ([#5768](/roundcube/roundcubemail/issues/5768))
 * Enigma: Fix compatibility with assets_dir
 * Managesieve: Skip redundant LISTSCRIPTS command
 * Fix SQL syntax error on MariaDB 10.2 ([#5774](/roundcube/roundcubemail/issues/5774))
 * Fix bug where zipdownload ignored files with the same name ([#5777](/roundcube/roundcubemail/issues/5777))
 * Fix bug where it wasn't possible to set timezone to auto-detected value ([#5782](/roundcube/roundcubemail/issues/5782))

## RELEASE 1.3-rc

 * "Flattened" the larry theme: fresher look by removing shadows and gradients
 * Support logging to php://stdout ([#5721](/roundcube/roundcubemail/issues/5721))
 * Add support for DelSp=Yes in format=flowed messages ([#5702](/roundcube/roundcubemail/issues/5702))
 * Update to jQuery 3.2.1
 * Update to TinyMCE 4.5.6
 * Plugin API: Call message_part_structure hook for sub-parts of multipart/alternative message ([#5678](/roundcube/roundcubemail/issues/5678))
 * Enigma: Always use detached signatures ([#5624](/roundcube/roundcubemail/issues/5624))
 * Enigma: Fix handling of messages with nested PGP encrypted parts ([#5634](/roundcube/roundcubemail/issues/5634))
 * Minimize unwanted message loading in preview frame on drag ([#5616](/roundcube/roundcubemail/issues/5616))
 * Fix failing database schema check in all engines except mysql ([#5730](/roundcube/roundcubemail/issues/5730))
 * Fix autocomplete popup closing with click outside the input, don't handle Tab key as Enter ([#5606](/roundcube/roundcubemail/issues/5606))
 * Fix jsdeps.json synchronization on update, warn about missing requirements of install-jsdeps.sh ([#5598](/roundcube/roundcubemail/issues/5598))
 * Fix missing thread expand icon on search result in widescreen mode ([#5613](/roundcube/roundcubemail/issues/5613))
 * Fix bug where image data URIs in css style were treated as evil/remote in mail preview ([#5580](/roundcube/roundcubemail/issues/5580))
 * Fix bug where external content in src attribute of input/video tags was not secured ([#5583](/roundcube/roundcubemail/issues/5583))
 * Fix PHP error on update of a contact with multiple email addresses when using PHP 7.1 ([#5587](/roundcube/roundcubemail/issues/5587))
 * Fix bug where mail content frame couldn't be reset in some corner cases ([#5608](/roundcube/roundcubemail/issues/5608))
 * Fix bug where some classic skin images were not displayed in IE/Edge ([#5614](/roundcube/roundcubemail/issues/5614))
 * Fix bug where signature couldn't be added above the quote in Firefox 51 ([#5628](/roundcube/roundcubemail/issues/5628))
 * Fix regression where groups with email address were resolved to its members' addresses
 * Fix update of group name in the contacts list header on group rename ([#5648](/roundcube/roundcubemail/issues/5648))
 * Add rewrite rule to disable access to /vendor/bin folder in `.htaccess` ([#5630](/roundcube/roundcubemail/issues/5630))
 * Fix bug where it was too easy accidentally move a folder when using the subscription checkbox ([#5655](/roundcube/roundcubemail/issues/5655))
 * Managesieve: Fix parser issue with empty lines between comments ([#5657](/roundcube/roundcubemail/issues/5657))
 * Managesieve: Fix possible defect in handling `\r\n` in scripts ([#5685](/roundcube/roundcubemail/issues/5685))
 * Fix/rephrase "unsaved changes" warning when cancelling a draft ([#5610](/roundcube/roundcubemail/issues/5610))
 * Fix XSS issue in handling of a style tag inside of an svg element [CVE-2017-6820]
 * Fix bug where settings/upload.inc could not be used by plugins ([#5694](/roundcube/roundcubemail/issues/5694))
 * Fix regression in LDAP fuzzy search where it always used prefix search instead ([#5713](/roundcube/roundcubemail/issues/5713))
 * Fix bug where namespace prefix could not be truncated on folders list if show_real_foldernames=true ([#5695](/roundcube/roundcubemail/issues/5695))
 * Fix undesired effects when postgres database uses different timezone than PHP host ([#5708](/roundcube/roundcubemail/issues/5708))
 * Installer: Fix DB schema initialization on MS SQL Server
 * Fix bug where base_dn setting was ignored inside group_filters ([#5720](/roundcube/roundcubemail/issues/5720))
 * Password: Fix security issue in virtualmin and sasl drivers [CVE-2017-8114]

## RELEASE 1.3-beta

 * Nicely handle contact deletion on contact edit ([#5522](/roundcube/roundcubemail/issues/5522))
 * vcard_attachments: Add possibility to attach contact vCard to composed message ([#4997](/roundcube/roundcubemail/issues/4997))
 * Preserve message internal/received date on import in mbox format ([#5559](/roundcube/roundcubemail/issues/5559))
 * Zipdownload: Fix date format in mbox "From line"
 * Possibility to display QR code for contacts data ([#5030](/roundcube/roundcubemail/issues/5030))
 * Added identicon plugin
 * Widescreen layout aka three column view ([#5093](/roundcube/roundcubemail/issues/5093))
 * Unify automatic marking as \Seen in preview pane, full-page and extwin views ([#5071](/roundcube/roundcubemail/issues/5071))
 * Disable double-click on the list when preview pane is on ([#5199](/roundcube/roundcubemail/issues/5199))
 * Support hostname and hostname:port in force_https option ([#5511](/roundcube/roundcubemail/issues/5511))
 * Support ALLOW-FROM in x_frame_options ([#5122](/roundcube/roundcubemail/issues/5122))
 * Allow to omit a subject when sending an email ([#5068](/roundcube/roundcubemail/issues/5068))
 * Warn about too many disclosed recipients in composed email [max_disclosed_recipients] ([#5132](/roundcube/roundcubemail/issues/5132))
 * identity_select: Support Received header ([#5085](/roundcube/roundcubemail/issues/5085))
 * Plugin API: Added get_compose_responses hook ([#5457](/roundcube/roundcubemail/issues/5457))
 * Display error when trying to upload more files than specified in max_file_uploads ([#5483](/roundcube/roundcubemail/issues/5483))
 * Add missing sql upgrade file for 'ip' column resize in session table ([#5465](/roundcube/roundcubemail/issues/5465))
 * Do not show inline images of unsupported mimetype ([#5463](/roundcube/roundcubemail/issues/5463))
 * Password: Added replacement variables support in password_pop_host ([#5539](/roundcube/roundcubemail/issues/5539))
 * Password: Don't store passwords in temp files when using dovecotpw ([#5531](/roundcube/roundcubemail/issues/5531))
 * Password: Added LDAP PPolicy driver ([#5364](/roundcube/roundcubemail/issues/5364))
 * Password: Added cpanel_webmail driver ([#5549](/roundcube/roundcubemail/issues/5549))
 * Password: Added possibility to nicely redirect from other plugins on password expiration ([#5468](/roundcube/roundcubemail/issues/5468))
 * Implement separate action to mark all messages in a folder as \Seen ([#5006](/roundcube/roundcubemail/issues/5006))
 * Implement marking as \Seen in all folders or in a folder and its subfolders ([#5076](/roundcube/roundcubemail/issues/5076))
 * Archive: Don't reload messages list when it's not needed ([#5225](/roundcube/roundcubemail/issues/5225))
 * Archive: Add option to automatically mark archived messages as \Seen ([#5142](/roundcube/roundcubemail/issues/5142))
 * Improve randomness of password salts and random hashes ([#5266](/roundcube/roundcubemail/issues/5266))
 * Password/cPanel: Add support for hash authentication and reseller accounts ([#5252](/roundcube/roundcubemail/issues/5252))
 * Support host-specific imap_conn_options/smtp_conn_options/managesieve_conn_options ([#5136](/roundcube/roundcubemail/issues/5136))
 * Center and scale images in attachment preview frame ([#5421](/roundcube/roundcubemail/issues/5421))
 * Added max_message_size option enforced when attaching files to a composed message ([#4993](/roundcube/roundcubemail/issues/4993))
 * Added Search button in quick search menus ([#5312](/roundcube/roundcubemail/issues/5312))
 * Implement "one click" attachment/messages/photo upload ([#5024](/roundcube/roundcubemail/issues/5024))
 * Squirrelmail_usercopy: Add option to define character set of data files
 * Removed useless 'created' column from 'session' table ([#5389](/roundcube/roundcubemail/issues/5389))
 * Dropped legacy browsers support ([#5167](/roundcube/roundcubemail/issues/5167))
    - Removed legacy_browser plugin
    - Removed hacks for IE < 10
    - Update to jQuery 3.1.1 and jQuery-UI 1.12.0
    - compile .min.js files with ECMASCRIPT5 option
 * Require PHP >= 5.4
 * Add possibility to preview and download attachments in mail compose ([#5053](/roundcube/roundcubemail/issues/5053))
 * Add possibility to rename attachments in mail compose ([#4996](/roundcube/roundcubemail/issues/4996))
 * Remove backward compatibility "layer" of bc.php ([#4902](/roundcube/roundcubemail/issues/4902))
 * Support WEBP images in mail messages ([#5362](/roundcube/roundcubemail/issues/5362))
 * Support MathML in HTML message preview ([#5182](/roundcube/roundcubemail/issues/5182))
 * Rename Addressbook to Contacts ([#5233](/roundcube/roundcubemail/issues/5233))
 * Remove PHP mail() support, smtp_server is required now ([#5340](/roundcube/roundcubemail/issues/5340))
 * Display full message subject in onmouseover on truncated subject in mail view ([#5346](/roundcube/roundcubemail/issues/5346))
 * Enigma: Support GnuPG 2.1 ([#5313](/roundcube/roundcubemail/issues/5313))
 * Enigma: Support key generation for multiple identities ([#5383](/roundcube/roundcubemail/issues/5383))
 * Enigma: Import keys from key-server(s) ([#5286](/roundcube/roundcubemail/issues/5286))
 * Enigma: Search missing public keys on a key-server in mail compose ([#5286](/roundcube/roundcubemail/issues/5286))
 * Enigma: Delete user keys when using deluser.sh script
 * Enigma: Fix redundant list-secret-keys/list-public-keys calls on signing/encryption
 * Enigma: Implement PGP encryption and signing in one go ([#5302](/roundcube/roundcubemail/issues/5302))
 * Enigma: Display signature verification status for encrypted+signed messages ([#5302](/roundcube/roundcubemail/issues/5302))
 * Display different attachment icon on encrypted messages
 * Display different confirmation text when moving messages to Trash ([#5220](/roundcube/roundcubemail/issues/5220))
 * Indicate that a collapsed thread has flagged children ([#5013](/roundcube/roundcubemail/issues/5013))
 * Implemented message/rfc822 attachment preview
 * Update to jsTimezoneDetect 1.0.6
 * Managesieve: Add (optional) RAW script editor ([#5414](/roundcube/roundcubemail/issues/5414))
 * Managesieve: Add option to automatically set vacation :from address ([#5428](/roundcube/roundcubemail/issues/5428))
 * Managesieve: Support 'string' test from variables extension [RFC 5229] ([#5248](/roundcube/roundcubemail/issues/5248))
 * Managesieve: Support 'duplicate' extension [RFC 7352]
 * Managesieve: Unhide advanced rule controls if there are inputs with errors
 * Managesieve: Display warning message when filter form contains errors
 * Control search engine crawlers via X-Robots-Tag header instead of <meta> and robots.txt ([#5098](/roundcube/roundcubemail/issues/5098))
 * Fixed redundancy in sql caching system and compatibility with Galera Cluster ([#5439](/roundcube/roundcubemail/issues/5439))
    - Removed redundant 'created' column from cache and cache_shared tables
    - Removed use of redundant data records
    - Added missing primary keys (dictionary, cache, cache_shared tables)
 * Fix so templating system does not mess with external (e.g. email) content ([#5499](/roundcube/roundcubemail/issues/5499))
 * Fix redundant keep-alive/refresh after session error on compose page ([#5500](/roundcube/roundcubemail/issues/5500))
 * Managesieve: Fix handling of scripts with nested rules ([#5540](/roundcube/roundcubemail/issues/5540))
 * Fix variable substitution in ldap host for some use-cases, e.g. new_user_identity ([#5544](/roundcube/roundcubemail/issues/5544))
 * Enigma: Fix PHP fatal error when decrypting a message with invalid signature ([#5555](/roundcube/roundcubemail/issues/5555))
 * Fix adding images to new identity signatures
 * Fix rsync error handling in installto.sh script ([#5562](/roundcube/roundcubemail/issues/5562))
 * Fix some advanced search issues with multiple addressbooks ([#5572](/roundcube/roundcubemail/issues/5572))
 * Fix so group/addressbook selection is retained on page refresh

## RELEASE 1.2.4

 * Managesieve: Fix handling of scripts with nested rules ([#5540](/roundcube/roundcubemail/issues/5540))
 * Managesieve: Fix parser issue with empty lines between comments ([#5657](/roundcube/roundcubemail/issues/5657))
 * Managesieve: Fix possible defect in handling \r\n in scripts ([#5685](/roundcube/roundcubemail/issues/5685))
 * Enigma: Fix handling of messages with nested PGP encrypted parts ([#5634](/roundcube/roundcubemail/issues/5634))
 * Enigma: Fix PHP fatal error when decrypting a message with invalid signature ([#5555](/roundcube/roundcubemail/issues/5555))
 * Enigma: Fix missing require statement for Crypt_GPG_KeyGenerator ([#5641](/roundcube/roundcubemail/issues/5641))
 * Fix variable substitution in ldap host for some use-cases, e.g. new_user_identity ([#5544](/roundcube/roundcubemail/issues/5544))
 * Fix adding images to new identity signatures
 * Fix rsync error handling in installto.sh script ([#5562](/roundcube/roundcubemail/issues/5562))
 * Fix some advanced search issues with multiple addressbooks ([#5572](/roundcube/roundcubemail/issues/5572))
 * Fix so group/addressbook selection is retained on page refresh
 * Fix bug where image data URIs in css style were treated as evil/remote in mail preview ([#5580](/roundcube/roundcubemail/issues/5580))
 * Fix bug where external content in src attribute of input/video tags was not secured ([#5583](/roundcube/roundcubemail/issues/5583))
 * Fix PHP error on update of a contact with multiple email addresses when using PHP 7.1 ([#5587](/roundcube/roundcubemail/issues/5587))
 * Fix bug where mail content frame couldn't be reset in some corner cases ([#5608](/roundcube/roundcubemail/issues/5608))
 * Fix bug where some classic skin images were not displayed in IE/Edge ([#5614](/roundcube/roundcubemail/issues/5614))
 * Fix bug where signature couldn't be added above the quote in Firefox 51 ([#5628](/roundcube/roundcubemail/issues/5628))
 * Fix regression where groups with email address were resolved to its members' addresses
 * Fix update of group name in the contacts list header on group rename ([#5648](/roundcube/roundcubemail/issues/5648))
 * Add rewrite rule to disable access to /vendor/bin folder in .htaccess ([#5630](/roundcube/roundcubemail/issues/5630))
 * Fix bug where it was too easy accidentally move a folder when using the subscription checkbox ([#5655](/roundcube/roundcubemail/issues/5655))
 * Fix XSS issue in handling of a style tag inside of an svg element (CVE-2017-6820)

## RELEASE 1.2.3

 * Searching in both contacts and groups when LDAP addressbook with group_filters option is used
 * Fix vulnerability in handling of mail()'s 5th argument
 * Fix To: header encoding in mail sent with mail() method ([#5475](/roundcube/roundcubemail/issues/5475))
 * Fix flickering of header topline in min-mode ([#5426](/roundcube/roundcubemail/issues/5426))
 * Fix bug where folders list would scroll to top when clicking on subscription checkbox ([#5447](/roundcube/roundcubemail/issues/5447))
 * Fix decoding of GB2312/GBK text when iconv is not installed ([#5448](/roundcube/roundcubemail/issues/5448))
 * Fix regression where creation of default folders wasn't functioning without prefix ([#5460](/roundcube/roundcubemail/issues/5460))
 * Enigma: Fix bug where last records on keys list were hidden ([#5461](/roundcube/roundcubemail/issues/5461))
 * Enigma: Fix key search with keyword containing non-ascii characters ([#5459](/roundcube/roundcubemail/issues/5459))
 * Fix bug where deleting folders with subfolders could fail in some cases ([#5466](/roundcube/roundcubemail/issues/5466))
 * Fix bug where IMAP password could be exposed via error message ([#5472](/roundcube/roundcubemail/issues/5472))
 * Fix bug where it wasn't possible to store more that 2MB objects in memcache/apc,
  Added memcache_max_allowed_packet and apc_max_allowed_packet settings ([#5452](/roundcube/roundcubemail/issues/5452))
 * Fix "Illegal string offset" warning in rcube::log_bug() on PHP 7.1 ([#5508](/roundcube/roundcubemail/issues/5508))
 * Fix storing "empty" values in rcube_cache/rcube_cache_shared ([#5519](/roundcube/roundcubemail/issues/5519))
 * Fix missing content check when image resize fails on attachment thumbnail generation ([#5485](/roundcube/roundcubemail/issues/5485))
 * Fix displaying attached images with wrong Content-Type specified ([#5527](/roundcube/roundcubemail/issues/5527))

## RELEASE 1.2.2

 * Enigma: Add possibility to configure gpg-agent binary location (enigma_pgp_agent)
 * Enigma: Fix signature verification with some IMAP servers, e.g. Gmail, DBMail ([#5371](/roundcube/roundcubemail/issues/5371))
 * Enigma: Make recipient key searches case-insensitive ([#5434](/roundcube/roundcubemail/issues/5434))
 * Fix regression in resizing JPEG images with Imagick ([#5376](/roundcube/roundcubemail/issues/5376))
 * Managesieve: Fix parsing of vacation date-time with non-default date_format ([#5372](/roundcube/roundcubemail/issues/5372))
 * Use SymLinksIfOwnerMatch in .htaccess instead of FollowSymLinks disabled on some hosts for security reasons ([#5370](/roundcube/roundcubemail/issues/5370))
 * Wash position:fixed style in HTML mail for better security ([#5264](/roundcube/roundcubemail/issues/5264))
 * Fix bug where memcache_debug didn't work for session operations
 * Fix bug where Message-ID domain part was tied to username instead of current identity ([#5385](/roundcube/roundcubemail/issues/5385))
 * Fix bug where blocked.gif couldn't be attached to reply/forward with insecure content
 * Fix E_DEPRECATED warning when using Auth_SASL::factory() ([#5401](/roundcube/roundcubemail/issues/5401))
 * Fix bug where names of downloaded files could be malformed when derived from the message subject ([#5404](/roundcube/roundcubemail/issues/5404))
 * Fix so "All" messages selection is resetted on search reset ([#5413](/roundcube/roundcubemail/issues/5413))
 * Fix bug where folder creation could fail if personal namespace contained more than one entry ([#5403](/roundcube/roundcubemail/issues/5403))
 * Fix error causing empty INBOX listing in Firefox when using an URL with user:password specified ([#5400](/roundcube/roundcubemail/issues/5400))
 * Fix PHP warning when handling shared namespace with empty prefix ([#5420](/roundcube/roundcubemail/issues/5420))
 * Fix so folders list is scrolled to the selected folder on page load ([#5424](/roundcube/roundcubemail/issues/5424))
 * Fix so when moving to Trash we make sure the folder exists ([#5192](/roundcube/roundcubemail/issues/5192))
 * Fix displaying size of attachments with zero size
 * Fix so "Action disabled" error uses more appropriate 404 code ([#5440](/roundcube/roundcubemail/issues/5440))

## RELEASE 1.2.1

 * Update TinyMCE to version 4.3.13 ([#5309](/roundcube/roundcubemail/issues/5309))
 * Fix bug where errors could have been not logged when per_user_logging=true
 * Fix bug where message list columns could be in wrong order after column drag-n-drop and list sorting
 * Fix so minified publickey.js (with cache-buster) is used when available ([#5254](/roundcube/roundcubemail/issues/5254))
 * Fix (replace) application/x-tar file extension test as it might not exist in nginx config ([#5253](/roundcube/roundcubemail/issues/5253))
 * Fix PHP warning when password_hosts is set, but is not an array ([#5260](/roundcube/roundcubemail/issues/5260))
 * Fix redundant keep-alive requests when session_lifetime is greater than ~20000 ([#5273](/roundcube/roundcubemail/issues/5273))
 * Fix so subfolders of INBOX can be set as Archive ([#5274](/roundcube/roundcubemail/issues/5274))
 * Fix bug where multi-folder search could choose a wrong folder in "this and subfolders" scope ([#5282](/roundcube/roundcubemail/issues/5282))
 * Fix bug where multi-folder search didn't work for unsubscribed INBOX ([#5259](/roundcube/roundcubemail/issues/5259))
 * Fix bug where "no body" alert could be displayed when sending mailvelope email
 * Enigma: Fix keys import from inside of an encrypted message ([#5285](/roundcube/roundcubemail/issues/5285))
 * Enigma: Fix malformed signed messages with force_7bit=true ([#5292](/roundcube/roundcubemail/issues/5292))
 * Enigma: Add possibility to configure gpg binary location (enigma_pgp_binary)
 * Enigma: Add possibility to export private keys ([#5321](/roundcube/roundcubemail/issues/5321))
 * Fix searching by email address in contacts with multiple addresses ([#5291](/roundcube/roundcubemail/issues/5291))
 * Fix handling of --delete argument in moduserprefs.sh script ([#5296](/roundcube/roundcubemail/issues/5296))
 * Workaround PHP issue by calling closelog() on script shutdown when using log_driver=syslog ([#5289](/roundcube/roundcubemail/issues/5289))
 * Fix so upgrade script makes sure program/lib directory does not contain old libraries ([#5287](/roundcube/roundcubemail/issues/5287))
 * Fix subscription checkbox state on error in folder subscribe/unsubscribe action ([#5243](/roundcube/roundcubemail/issues/5243))
 * Fix bug where microsecond format in logged date didn't work in some cases
 * Fix conflict in new_user_dialog and password_force_new_user settings ([#5275](/roundcube/roundcubemail/issues/5275))
 * Don't create multipart/alternative messages with empty text/plain part ([#5283](/roundcube/roundcubemail/issues/5283))
 * Use contact_search_name format in popup on results in compose contacts search
 * Fix handling of 'mailto' and 'error' arguments in message_before_send hook ([#5347](/roundcube/roundcubemail/issues/5347))
 * Fix missing localization of HTML editor when assets_dir != INSTALL_PATH
 * Fix handling of blockquote tags with mixed case on html2text conversion ([#5363](/roundcube/roundcubemail/issues/5363))
 * Fix javascript errors in IE on page with iframe that points to another domain

## RELEASE 1.2.0

 * Enigma: Added enigma_debug option
 * Fix message list multi-select/deselect issue ([#5219](/roundcube/roundcubemail/issues/5219))
 * Fix bug where getting HTML editor content could steal focus from other form controls ([#5223](/roundcube/roundcubemail/issues/5223))
 * Fix bug where contact search menu fields where always unchecked in Larry skin
 * Fix autoloading of 'html' class
 * Fix bug where Encrypt button appears when switching editor to HTML ([#5235](/roundcube/roundcubemail/issues/5235))
 * Fix XSS issue in href attribute on area tag [CVE-2016-4552] ([#5240](/roundcube/roundcubemail/issues/5240))

## RELEASE 1.2-rc

 * Managesieve: Refactored script parser to be 100x faster
 * Enigma: added option to force users to use signing/encryption
 * Enigma: Added option to attach public keys to sent mail ([#5152](/roundcube/roundcubemail/issues/5152))
 * Enigma: Handle messages with text before an encrypted block ([#5149](/roundcube/roundcubemail/issues/5149))
 * Enigma: Handle encrypted/signed content inside message/rfc822 attachments
 * Enigma: Fix missing html/plain switch on multipart/signed messages ([#4963](/roundcube/roundcubemail/issues/4963))
 * Enigma: Disable format=flowed for signed plain text messages ([#4960](/roundcube/roundcubemail/issues/4960))
 * Enigma: Fix handling of encrypted + signed messages ([#4950](/roundcube/roundcubemail/issues/4950))
 * Enigma: Fix invalid boundary use in signed messages structure
 * Enable use of TLSv1.1 and TLSv1.2 for IMAP ([#4955](/roundcube/roundcubemail/issues/4955))
 * Save copy of original .htaccess file when using installto.sh script ([#4947](/roundcube/roundcubemail/issues/4947))
 * Fix regression where some message attachments could be missing on edit/forward ([#4939](/roundcube/roundcubemail/issues/4939))
 * Fix regression in displaying contents of message/rfc822 parts ([#4937](/roundcube/roundcubemail/issues/4937))
 * Fix handling of message/rfc822 attachments on replies and forwards ([#4938](/roundcube/roundcubemail/issues/4938))
 * Fix PDF support detection in Firefox > 19 ([#4941](/roundcube/roundcubemail/issues/4941))
 * Fix path traversal vulnerability in setting a skin [CVE-2015-8770] ([#4945](/roundcube/roundcubemail/issues/4945))
 * Fix so drag-n-drop of text (e.g. recipient addresses) on compose page actually works ([#4944](/roundcube/roundcubemail/issues/4944))
 * Fix .htaccess rewrite rules to not block .well-known URIs ([#4943](/roundcube/roundcubemail/issues/4943))
 * Fix mail view scaling on iOS ([#4915](/roundcube/roundcubemail/issues/4915))
 * Fix PHP7 warning "session_start(): Session callback expects true/false return value" ([#4948](/roundcube/roundcubemail/issues/4948))
 * Fix XSS issue in SVG images handling ([#4949](/roundcube/roundcubemail/issues/4949))
 * Fix missing language name in "Add to Dictionary" request in HTML mode ([#4951](/roundcube/roundcubemail/issues/4951))
 * Fix (again) security issue in DBMail driver of password plugin (CVE-2015-2181) ([#4958](/roundcube/roundcubemail/issues/4958))
 * Fix bug where Archive/Junk buttons were not active after page jump with select=all mode ([#4961](/roundcube/roundcubemail/issues/4961))
 * Fix bug in long recipients list parsing for cases where recipient name contained @-char ([#4964](/roundcube/roundcubemail/issues/4964))
 * Plugin API: Added addressbook_export hook
 * Fix additional_message_headers plugin compatibility with Mail_Mime >= 1.9 ([#4966](/roundcube/roundcubemail/issues/4966))
 * Hide DSN option in Preferences when smtp_server is not used ([#4967](/roundcube/roundcubemail/issues/4967))
 * Fix handling of body parameter in mail compose request
 * Protect download urls against CSRF using unique request tokens ([#4957](/roundcube/roundcubemail/issues/4957))
 * newmail_notifier: Refactor desktop notifications
 * Fix so contactlist_fields option can be set via config file
 * Fix so SPECIAL-USE assignments are forced only until user sets special folders ([#4782](/roundcube/roundcubemail/issues/4782))
 * Fix performance in reverting order of THREAD result
 * Fix converting mail addresses with `@www.` into mailto links ([#5197](/roundcube/roundcubemail/issues/5197))

## RELEASE 1.2-beta

 * Update TinyMCE to version 4.2
 * Remove backward compatibility "layer" of bc.php ([#4902](/roundcube/roundcubemail/issues/4902))
 * Add possibility to define date format in write operations for ldap attributes ([#3956](/roundcube/roundcubemail/issues/3956))
 * Display attachment size in compose ([#1329](/roundcube/roundcubemail/issues/1329))
 * Added possibility to drag-n-drop attachments from mail preview to compose window
 * Implemented mail messages searching with predefined date interval
 * PGP encryption support via Mailvelope integration
 * PGP encryption support via Enigma plugin
 * PHP7 compatibility fixes ([#4836](/roundcube/roundcubemail/issues/4836))
 * Security: Added brute-force attack prevention via login rate limit ([#4922](/roundcube/roundcubemail/issues/4922))
 * Security: Added options to validate username/password on logon ([#4884](/roundcube/roundcubemail/issues/4884))
 * Security: Improve randomness of security tokens ([#4899](/roundcube/roundcubemail/issues/4899))
 * Security: Use random security tokens instead of hashes based on encryption key ([#4829](/roundcube/roundcubemail/issues/4829))
 * Security: Improved encrypt/decrypt methods with option to choose the cipher_method ([#4492](/roundcube/roundcubemail/issues/4492))
 * Make optional adding of standard signature separator - sig_separator ([#3276](/roundcube/roundcubemail/issues/3276))
 * Optimize folder_size() on Cyrus IMAP by using special folder annotation ([#4894](/roundcube/roundcubemail/issues/4894))
 * Make optional hidding of folders with name starting with a dot - imap_skip_hidden_folders ([#4870](/roundcube/roundcubemail/issues/4870))
 * Add option to enable HTML editor always, except when replying to plain text messages ([#4352](/roundcube/roundcubemail/issues/4352))
 * Emoticons: Added option to switch on/off emoticons in compose editor ([#2076](/roundcube/roundcubemail/issues/2076))
 * Emoticons: Added option to switch on/off emoticons in plain text messages
 * Emoticons: All emoticons-related functionality is handled by the plugin now
 * Installer: Add button to save generated config file in system temp directory ([#3553](/roundcube/roundcubemail/issues/3553))
 * Remove common subject prefixes Re:, Re[x]:, Re-x: on reply ([#4882](/roundcube/roundcubemail/issues/4882))
 * Added GSSAPI/Kerberos authentication plugin - krb_authentication
 * Password: Allow temporarily disabling the plugin functionality with a notice
 * Require Mbstring and OpenSSL extensions ([#5166](/roundcube/roundcubemail/issues/5166))
 * Add --config and --type options to moduserprefs.sh script ([#4651](/roundcube/roundcubemail/issues/4651))
 * Implemented memcache_debug and apc_debug options
 * Installer: Remove system() function use ([#4695](/roundcube/roundcubemail/issues/4695))
 * Password plugin: Added 'kpasswd' driver by Peter Allgeyer
 * Add initdb.sh to create database from initial.sql script with prefix support ([#4722](/roundcube/roundcubemail/issues/4722))
 * Plugin API: Added disabled_plugins an disabled_buttons options in html_editor hook
 * Plugin API: Added message_part_body hook
 * Plugin API: Added message_ready hook
 * Plugin API: Add special onload() method to execute plugin actions before startup (session and GUI initialization)
 * Implemented UI element to jump to specified page of the messages list ([#1677](/roundcube/roundcubemail/issues/1677))
 * Fix searching of contacts to allow remote images for known senders ([#4886](/roundcube/roundcubemail/issues/4886))
 * Fix bug where clicking date column with 'arrival' sorting would switch to sorting by 'date' ([#4690](/roundcube/roundcubemail/issues/4690))
 * Fix bug where message content could overlap attachments list in Larry skin ([#4876](/roundcube/roundcubemail/issues/4876))
 * Fix so microseconds macro (u) in log_date_format works ([#4855](/roundcube/roundcubemail/issues/4855))
 * Fix so unrecognized TNEF attachments are displayed on the list of attachments ([#5138](/roundcube/roundcubemail/issues/5138))

## RELEASE 1.1.5

 * Plugin API: Added `html2text` hook
 * Plugin API: Added `addressbook_export` hook
 * Fix missing emoticons on html-to-text conversion
 * Fix random "access to this resource is secured against CSRF" message at logout ([#4956](/roundcube/roundcubemail/issues/4956))
 * Fix missing language name in "Add to Dictionary" request in HTML mode ([#4951](/roundcube/roundcubemail/issues/4951))
 * Enable use of TLSv1.1 and TLSv1.2 for IMAP ([#4955](/roundcube/roundcubemail/issues/4955))
 * Fix XSS issue in SVG images handling ([#4949](/roundcube/roundcubemail/issues/4949))
 * Fix (again) security issue in DBMail driver of password plugin (CVE-2015-2181) ([#4958](/roundcube/roundcubemail/issues/4958))
 * Fix bug in long recipients list parsing for cases where recipient name contained @-char ([#4964](/roundcube/roundcubemail/issues/4964))
 * Fix additional_message_headers plugin compatibility with Mail_Mime >= 1.9 ([#4966](/roundcube/roundcubemail/issues/4966))
 * Hide DSN option in Preferences when smtp_server is not used ([#4967](/roundcube/roundcubemail/issues/4967))
 * Protect download urls against CSRF using unique request tokens ([#4957](/roundcube/roundcubemail/issues/4957))
 * newmail_notifier Plugin: Refactored desktop notifications
 * Fix so contactlist_fields option can be set via config file
 * Fix so SPECIAL-USE assignments are forced only until user sets special folders ([#4782](/roundcube/roundcubemail/issues/4782))
 * Fix performance in reverting order of THREAD result
 * Fix converting mail addresses with `@www.` into mailto links ([#5197](/roundcube/roundcubemail/issues/5197))

## RELEASE 1.1.4

 * Add workaround for https://bugs.php.net/bug.php?id=70757 ([#4931](/roundcube/roundcubemail/issues/4931))
 * Fix duplicate messages in list and wrong count after delete ([#4925](/roundcube/roundcubemail/issues/4925))
 * Fix so Installer requires PHP5
 * Make brute force attacks harder by re-generating security token on every failed login ([#4913](/roundcube/roundcubemail/issues/4913))
 * Slow down brute-force attacks by waiting for a second after failed login ([#4913](/roundcube/roundcubemail/issues/4913))
 * Fix .htaccess rewrite rules to not block .well-known URIs ([#4943](/roundcube/roundcubemail/issues/4943))
 * Fix mail view scaling on iOS ([#4915](/roundcube/roundcubemail/issues/4915))
 * Fix so database_attachments::cleanup() does not remove attachments from other sessions ([#4907](/roundcube/roundcubemail/issues/4907))
 * Fix responses list update issue after response name change ([#4917](/roundcube/roundcubemail/issues/4917))
 * Fix bug where message preview was unintentionally reset on check-recent action ([#4921](/roundcube/roundcubemail/issues/4921))
 * Fix bug where HTML messages with invalid/excessive css styles couldn't be displayed ([#4905](/roundcube/roundcubemail/issues/4905))
 * Fix redundant blank lines when using HTML and top posting ([#4927](/roundcube/roundcubemail/issues/4927))
 * Fix redundant blank lines on start of text after html to text conversion ([#4928](/roundcube/roundcubemail/issues/4928))
 * Fix HTML sanitizer to skip <!-- node type X --> in output ([#4932](/roundcube/roundcubemail/issues/4932))
 * Fix invalid LDAP query in ACL user autocompletion ([#4934](/roundcube/roundcubemail/issues/4934))
 * Fix regression in displaying contents of message/rfc822 parts ([#4937](/roundcube/roundcubemail/issues/4937))
 * Fix handling of message/rfc822 attachments on replies and forwards ([#4938](/roundcube/roundcubemail/issues/4938))
 * Fix PDF support detection in Firefox > 19 ([#4941](/roundcube/roundcubemail/issues/4941))
 * Fix path traversal vulnerability (CWE-22) in setting a skin ([#4945](/roundcube/roundcubemail/issues/4945))
 * Fix so drag-n-drop of text (e.g. recipient addresses) on compose page actually works ([#4944](/roundcube/roundcubemail/issues/4944))

## RELEASE 1.1.3

 * Fix closing of nested menus ([#4854](/roundcube/roundcubemail/issues/4854))
 * Fix so E_DEPRECATED errors from PEAR libs are ignored by error_reporting change ([#4770](/roundcube/roundcubemail/issues/4770))
 * Fix compatibility with PHP 5.3 in rcube_ldap class ([#4842](/roundcube/roundcubemail/issues/4842))
 * Get rid of Mail_mimeDecode package dependency ([#4836](/roundcube/roundcubemail/issues/4836))
 * Fix "Importing..." message does not hide on error ([#4840](/roundcube/roundcubemail/issues/4840))
 * Fix SQL error on logout when using session_storage=php ([#4839](/roundcube/roundcubemail/issues/4839))
 * Update to jQuery 2.1.4 ([#5165](/roundcube/roundcubemail/issues/5165))
 * Fix Compose action in addressbook for results from multiple addressbooks ([#4834](/roundcube/roundcubemail/issues/4834))
 * Fix bug where some messages in multi-folder search couldn't be viewed/printed/downloaded ([#4843](/roundcube/roundcubemail/issues/4843))
 * Fix unintentional messages list page change on page switch in compose addressbook ([#4844](/roundcube/roundcubemail/issues/4844))
 * Fix race-condition in saving user preferences and loading plugin config ([#4845](/roundcube/roundcubemail/issues/4845))
 * Fix so plain text signature field uses monospace font ([#4848](/roundcube/roundcubemail/issues/4848))
 * Fix so links with href == content aren't added to links list on html to text conversion ([#4847](/roundcube/roundcubemail/issues/4847))
 * Fix handling of non-break spaces in html to text conversion ([#4849](/roundcube/roundcubemail/issues/4849))
 * Fix self-reply detection issues ([#4852](/roundcube/roundcubemail/issues/4852))
 * Fix multi-folder search result sorting by arrival date ([#4858](/roundcube/roundcubemail/issues/4858))
 * Fix so *-request@ addresses in Sender: header are also ignored on reply-all ([#4860](/roundcube/roundcubemail/issues/4860))
 * Update to TinyMCE 4.1.10 ([#5164](/roundcube/roundcubemail/issues/5164))
 * Fix draft removal after a message is sent and storing sent message is disabled ([#4869](/roundcube/roundcubemail/issues/4869))
 * Fix so imap folder attribute comparisons are case-insensitive ([#4868](/roundcube/roundcubemail/issues/4868))
 * Fix bug where new messages weren't added to the list in search mode
 * Fix wrong positioning of message list header on page scroll in Webkit browsers ([#4646](/roundcube/roundcubemail/issues/4646))
 * Fix some javascript errors in rare situations ([#4853](/roundcube/roundcubemail/issues/4853))
 * Fix error when using back button after sending an email ([#4628](/roundcube/roundcubemail/issues/4628))
 * Fix removing signature when switching to identity with an empty sig in HTML mode ([#4872](/roundcube/roundcubemail/issues/4872))
 * Disable links list generation on html-to-text conversion of identities or composed message ([#4850](/roundcube/roundcubemail/issues/4850))
 * Fix "washing" of style elements wrapped into many lines
 * Fix so input field (e.g. search box) does not loose focus on list load ([#4862](/roundcube/roundcubemail/issues/4862))
 * Fix minor XSS issue in drag-n-drop file uploads ([#4900](/roundcube/roundcubemail/issues/4900))

## RELEASE 1.1.2

 * Add new plugin hook 'identity_create_after' providing the ID of the inserted identity ([#4807](/roundcube/roundcubemail/issues/4807))
 * Add option to place signature at bottom of the quoted text even in top-posting mode [sig_below]
 * Fix handling of %-encoded entities in mailto: URLs ([#4799](/roundcube/roundcubemail/issues/4799))
 * Fix zipped messages downloads after selecting all messages in a folder ([#4797](/roundcube/roundcubemail/issues/4797))
 * Fix vpopmaild driver of password plugin
 * Fix PHP warning: Non-static method PEAR::setErrorHandling() should not be called statically ([#4798](/roundcube/roundcubemail/issues/4798))
 * Fix tables listing routine on mysql and postgres so it skips system or other database tables and views ([#4796](/roundcube/roundcubemail/issues/4796))
 * Fix message list header in classic skin on window resize in Internet Explorer ([#4732](/roundcube/roundcubemail/issues/4732))
 * Fix so text/calendar parts are listed as attachments even if not marked as such ([#4795](/roundcube/roundcubemail/issues/4795))
 * Fix lack of signature separator for plain text signatures in html mode ([#4802](/roundcube/roundcubemail/issues/4802))
 * Fix font artifact in Google Chrome on Windows ([#4803](/roundcube/roundcubemail/issues/4803))
 * Fix bug where forced extwin page reload could exit from the extwin mode ([#4801](/roundcube/roundcubemail/issues/4801))
 * Fix bug where some unrelated attachments in multipart/related message were not listed ([#4805](/roundcube/roundcubemail/issues/4805))
 * Fix mouseup event handling when dragging a list record ([#4808](/roundcube/roundcubemail/issues/4808))
 * Fix bug where preview_pane setting wasn't always saved into user preferences ([#4809](/roundcube/roundcubemail/issues/4809))
 * Fix bug where messages count was not updated after message move/delete with skip_deleted=false ([#4814](/roundcube/roundcubemail/issues/4814))
 * Fix security issue in contact photo handling ([#4817](/roundcube/roundcubemail/issues/4817))
 * Fix possible memcache/apc cache data consistency issues ([#4820](/roundcube/roundcubemail/issues/4820))
 * Fix bug where imap_conn_options were ignored in IMAP connection test ([#4822](/roundcube/roundcubemail/issues/4822))
 * Fix bug where some files could have "executable" extension when stored in temp folder ([#4815](/roundcube/roundcubemail/issues/4815))
 * Fix attached file path unsetting in database_attachments plugin ([#4823](/roundcube/roundcubemail/issues/4823))
 * Fix issues when using moduserprefs.sh without --user argument ([#4825](/roundcube/roundcubemail/issues/4825))
 * Fix potential info disclosure issue by protecting directory access ([#4816](/roundcube/roundcubemail/issues/4816))
 * Fix blank image in html_signature when saving identity changes ([#4833](/roundcube/roundcubemail/issues/4833))
 * Installer: Use openssl_random_pseudo_bytes() (if available) to generate des_key ([#4827](/roundcube/roundcubemail/issues/4827))
 * Fix XSS vulnerability in _mbox argument handling ([#4837](/roundcube/roundcubemail/issues/4837))

## RELEASE 1.1.1

 * ACL: Allow other plugins to adjust the list of permissions and groups to edit
 * Add possibility to print contact information (of a single contact)
 * Add possibility to configure max_allowed_packet value for all database engines ([#4772](/roundcube/roundcubemail/issues/4772))
 * Improved handling of storage errors after message is sent
 * Update to TinyMCE 4.1.9
 * Unified request* event arguments handling, added support for _unlock and _action parameters
 * Security: Generate random hash for the per-user local storage prefix ([#4768](/roundcube/roundcubemail/issues/4768))
 * Fix refreshing of drafts list when sending a message which was saved in meantime ([#4745](/roundcube/roundcubemail/issues/4745))
 * Fix saving/sending emoticon images when assets_dir is set
 * Fix PHP fatal error when visiting Vacation interface and there's no sieve script yet ([#4778](/roundcube/roundcubemail/issues/4778))
 * Fix setting max packet size for DB caches and check packet size also in shared cache
 * Fix needless security warning on BMP attachments display ([#4771](/roundcube/roundcubemail/issues/4771))
 * Fix handling of some improper constructs in format=flowed text as per the RFC3676[4.5] ([#4773](/roundcube/roundcubemail/issues/4773))
 * Fix performance of rcube_db_mysql::get_variable()
 * Fix missing or not up-to-date CATEGORIES entry in vCard export ([#4766](/roundcube/roundcubemail/issues/4766))
 * Fix fatal errors on systems without mbstring extension or mb_regex_encoding() function ([#4769](/roundcube/roundcubemail/issues/4769))
 * Fix cursor position on reply below the quote in HTML mode ([#4759](/roundcube/roundcubemail/issues/4759))
 * Fix so "over quota" errors are displayed also in message compose page
 * Fix duplicate entries supression in autocomplete result ([#4776](/roundcube/roundcubemail/issues/4776))
 * Fix "Non-static method PEAR::isError() should not be called statically" errors ([#4770](/roundcube/roundcubemail/issues/4770))
 * Fix parsing invalid HTML messages with BOM after <!DOCTYPE> ([#4777](/roundcube/roundcubemail/issues/4777))
 * Fix duplicate entry on timezones list in rcube_config::timezone_name_from_abbr() ([#4779](/roundcube/roundcubemail/issues/4779))
 * Fix so localized folder name is displayed in multi-folder search result ([#4750](/roundcube/roundcubemail/issues/4750))
 * Fix javascript error after creating a folder which is a subfolder of another one ([#4781](/roundcube/roundcubemail/issues/4781))
 * Fix bug where subject of sent/saved message was removed if mbstring wasn't installed ([#4780](/roundcube/roundcubemail/issues/4780))
 * Fix missing vcard_attachment icon on messages list ([#4783](/roundcube/roundcubemail/issues/4783))
 * Fix storing signatures with big images in MySQL database ([#4785](/roundcube/roundcubemail/issues/4785))
 * Fix Opera browser detection in javascript ([#4786](/roundcube/roundcubemail/issues/4786))
 * Fix so search filter, scope and fields are reset on folder change
 * Fix rows count when messages search fails ([#4760](/roundcube/roundcubemail/issues/4760))
 * Fix bug where spellchecking in HTML editor do not work after switching editor type more than once ([#4789](/roundcube/roundcubemail/issues/4789))
 * Fix bug where TinyMCE area height was too small on slow network connection ([#4788](/roundcube/roundcubemail/issues/4788))
 * Fix backtick character handling in sql queries ([#4790](/roundcube/roundcubemail/issues/4790))
 * Fix redirect URL for attachments loaded in an iframe when behind a proxy ([#4724](/roundcube/roundcubemail/issues/4724))
 * Fix menu container references to point to the actual `<ul>` element ([#4791](/roundcube/roundcubemail/issues/4791))
 * Fix javascripts errors in IE8 - lack of Event.which, focusing a hidden element ([#4793](/roundcube/roundcubemail/issues/4793))

## RELEASE 1.1.0

 * Make SMTP error log more verbose - include server response and error code
 * Fix download options menu (added by zipdownload plugin) in classic skin ([#4740](/roundcube/roundcubemail/issues/4740))
 * Fix blocked.gif image usage with assets_dir set
 * Fix bug where max_group_members was ignored when adding a new contact ([#4733](/roundcube/roundcubemail/issues/4733))
 * Hide MDN and DSN options in compose if disabled by admin ([#4735](/roundcube/roundcubemail/issues/4735))
 * Fix checks based on window.ActiveXObject in IE > 10
 * Fix XSS issue in style attribute handling ([#4739](/roundcube/roundcubemail/issues/4739))
 * Fix bug where Drafts list wasn't updated on draft-save action in new window ([#4737](/roundcube/roundcubemail/issues/4737))
 * Fix so "set as default" option is hidden if identities_level > 1 ([#4738](/roundcube/roundcubemail/issues/4738))
 * Fix bug where search was reset after returning from compose visited for reply
 * Fix javascript error in "IE 8.0/Tablet PC" browser ([#4730](/roundcube/roundcubemail/issues/4730))
 * Fix bug where Reply-To address was ignored on reply to messages sent by self ([#4742](/roundcube/roundcubemail/issues/4742))
 * Fix bug where empty fieldmap config entries caused empty results of ldap search ([#4741](/roundcube/roundcubemail/issues/4741))
 * Fix bug where drafts list wasn't refreshed after draft message was sent from another window ([#4745](/roundcube/roundcubemail/issues/4745))
 * Fix keyboard navigation and css in datepicker widget across many Firefox versions
 * Fix false warning when opening attached text/plain files ([#4748](/roundcube/roundcubemail/issues/4748))
 * Fix bug where signature could have been inserted twice after plain-to-html switch ([#4746](/roundcube/roundcubemail/issues/4746))
 * Fix security issue in DBMail driver of password plugin ([#4757](/roundcube/roundcubemail/issues/4757))
 * Enable FollowSymLinks option in .htaccess file which is required by rewrite rules ([#4754](/roundcube/roundcubemail/issues/4754))
 * Fix so JSON.parse() errors on localStorage items are ignored ([#4752](/roundcube/roundcubemail/issues/4752))

## RELEASE 1.1-RC

 * Update jQuery to version 2.1.3
 * Improve system security by using optional special URL with security token - use_secure_urls
 * Allow to define separate server/path for image/js/css files - assets_url/assets_dir
 * Sync vendor folder if exists in source package ([#4700](/roundcube/roundcubemail/issues/4700))
 * Avoid useless reloading list when resetting search with active filter ([#4654](/roundcube/roundcubemail/issues/4654))
 * Fix invalid folder selection if clicked while busy ([#4709](/roundcube/roundcubemail/issues/4709))
 * Fix import of multiple contact email addresses from Outlook-csv format ([#4714](/roundcube/roundcubemail/issues/4714))
 * Fix drag-n-drop to folders expanded while dragging ([#4708](/roundcube/roundcubemail/issues/4708))
 * Fix import of multiple contact groups from Google-csv format ([#4710](/roundcube/roundcubemail/issues/4710))
 * Fix import of contacts with multiple email addresses from Google-csv format ([#4719](/roundcube/roundcubemail/issues/4719))
 * Fix bugs where CSRF attacks were still possible on some requests
 * Fix some rcube_utils::anytodatetime() corner cases with timezone mismatches ([#4712](/roundcube/roundcubemail/issues/4712))
 * Improve move-to and contact-export button in classic skin ([#4713](/roundcube/roundcubemail/issues/4713))
 * Fix wrong icon for download button in classic skin
 * Fix bug where sent message was saved in Sent folder even if disabled by user ([#4729](/roundcube/roundcubemail/issues/4729))

## RELEASE 1.1-beta

 * Fix skin path handling in plugin context ([#4111](/roundcube/roundcubemail/issues/4111))
 * Prevent memory exhaustion on image resizing with GD on Windows ([#4580](/roundcube/roundcubemail/issues/4580))
 * Add plugin hook for database table name lookups as requested in [#4538](/roundcube/roundcubemail/issues/4538)
 * Added Oracle database support
 * Support contacts import in GMail CSV format
 * Added namespace filter in Folder Manager
 * Added folder searching in Folder Manager
 * Fix restoring draft messages from localStorage if editor mode differs ([#4631](/roundcube/roundcubemail/issues/4631))
 * Added config option/user preference to disable saving messages in localStorage ([#4606](/roundcube/roundcubemail/issues/4606))
 * Added config option 'imap_log_session' to enable Roundcube <-> IMAP session ID logging
 * Added config option 'log_session_id' to control the length of the session identifier in logs
 * Implemented 'storage_connected' API hook after successful IMAP login ([#4638](/roundcube/roundcubemail/issues/4638))
 * Integrate Net_LDAP3 and rcube_ldap_generic classes
 * Add option (disabled_actions) to disable UI elements/actions ([#4478](/roundcube/roundcubemail/issues/4478))
 * Support password encryption using openssl extension ([#4614](/roundcube/roundcubemail/issues/4614))
 * Create/rename groups in UI dialogs ([#4592](/roundcube/roundcubemail/issues/4592))
 * Added 'contact_search_name' option to define autocompletion entry format
 * Display quota information for current folder not INBOX only ([#3442](/roundcube/roundcubemail/issues/3442))
 * Support images in HTML signatures ([#3917](/roundcube/roundcubemail/issues/3917))
 * Display full quota information in popup ([#2103](/roundcube/roundcubemail/issues/2103), [#2746](/roundcube/roundcubemail/issues/2746))
 * Mail compose: Selecting contact inserts recipient to previously focused input - to/cc/bcc accordingly ([#4487](/roundcube/roundcubemail/issues/4487))
 * Close "no subject" prompt with Enter key ([#4463](/roundcube/roundcubemail/issues/4463))
 * Password: Add option to force new users to change their password ([#2963](/roundcube/roundcubemail/issues/2963))
 * Improve support for screen readers and assistive technology using WCAG 2.0 and WAI ARIA standards
 * Enable basic keyboard navigation throughout the UI ([#3333](/roundcube/roundcubemail/issues/3333))
 * Select/scroll to previously selected message when returning from message page ([#4146](/roundcube/roundcubemail/issues/4146))
 * Display a warning if popup window was blocked ([#4472](/roundcube/roundcubemail/issues/4472))
 * Remove (was: ...) from message subject on reply ([#4359](/roundcube/roundcubemail/issues/4359))
 * Update to TinyMCE 4.1 ([#4168](/roundcube/roundcubemail/issues/4168))
 * Enable autolink plugin in TinyMCE ([#4029](/roundcube/roundcubemail/issues/4029))
 * Support image operations with Imagick extension ([#4498](/roundcube/roundcubemail/issues/4498))
 * Support upload progress with session.upload_progress and PECL uploadprogress module ([#3934](/roundcube/roundcubemail/issues/3934))
 * Make identity name field optional ([#4435](/roundcube/roundcubemail/issues/4435))
 * Utility script to remove user records from the local database
 * Plugin API: Added message_saved hook ([#4503](/roundcube/roundcubemail/issues/4503))
 * Plugin API: Added imap_search_before hook
 * Support messages import from zip archives
 * Zipdownload: Added mbox format support ([#2354](/roundcube/roundcubemail/issues/2354))
 * Drop support for IE6, move IE7/IE8 support to legacy_browser plugin
 * Update to jQuery-2.1.1
 * Search across multiple folders ([#1676](/roundcube/roundcubemail/issues/1676))
 * Improve UI integration of ACL settings
 * Drop support for PHP < 5.3.7
 * Set In-Reply-To and References for forwarded messages ([#4465](/roundcube/roundcubemail/issues/4465))
 * Removed redundant default_folders config option ([#4500](/roundcube/roundcubemail/issues/4500))
 * Implemented IMAP SPECIAL-USE extension support [RFC6154] ([#3326](/roundcube/roundcubemail/issues/3326))
 * Optimize some framed pages content for better performance ([#4517](/roundcube/roundcubemail/issues/4517))
 * Improve text messages display and conversion to HTML ([#4091](/roundcube/roundcubemail/issues/4091))
 * Don't remove links when html signature is converted to text ([#4473](/roundcube/roundcubemail/issues/4473))
 * Fix page title when using search filter ([#4636](/roundcube/roundcubemail/issues/4636))
 * Fix mbox files import
 * Fix some character sets detection ([#4694](/roundcube/roundcubemail/issues/4694))
 * Fix so attachment charset is set in headers of forward/draft message ([#4676](/roundcube/roundcubemail/issues/4676))
 * Fix bug where wrong charset could be used for text attachment preview page ([#4674](/roundcube/roundcubemail/issues/4674))
 * Fix setting flags on servers with no PERMANENTFLAGS response ([#4667](/roundcube/roundcubemail/issues/4667))
 * Fix regression in SHAA password generation in ldap driver of password plugin ([#4670](/roundcube/roundcubemail/issues/4670))
 * Fix displaying of HTML messages with absolutely positioned elements in Larry skin ([#4672](/roundcube/roundcubemail/issues/4672))
 * Fix font style display issue in HTML messages with styled <span> elements ([#4671](/roundcube/roundcubemail/issues/4671))
 * Fix download of attachments that are part of TNEF message ([#4668](/roundcube/roundcubemail/issues/4668))
 * Fix handling of uuencoded messages if messages_cache is enabled ([#4675](/roundcube/roundcubemail/issues/4675))
 * Fix handling of base64-encoded attachments with extra spaces ([#4678](/roundcube/roundcubemail/issues/4678))
 * Fix handling of UNKNOWN-CTE response, try do decode content client-side ([#4650](/roundcube/roundcubemail/issues/4650))
 * Fix bug where creating subfolders in shared folders wasn't possible without ACL extension ([#4680](/roundcube/roundcubemail/issues/4680))
 * Fix reply scrolling issue with text mode and start message below the quote ([#4681](/roundcube/roundcubemail/issues/4681))
 * Fix possible issues in skin/skin_path config handling ([#4689](/roundcube/roundcubemail/issues/4689))

## RELEASE 1.0.6

 * Make SMTP error log more verbose - include server response and error code
 * Fix rows count when messages search fails ([#4760](/roundcube/roundcubemail/issues/4760))
 * Fix security issue in DBMail driver of password plugin ([#4757](/roundcube/roundcubemail/issues/4757))
 * Fix handling of some improper constructs in format=flowed text as per the RFC3676[4.5] ([#4773](/roundcube/roundcubemail/issues/4773))
 * Fix missing or not up-to-date CATEGORIES entry in vCard export ([#4766](/roundcube/roundcubemail/issues/4766))
 * Fix duplicate entry on timezones list in rcube_config::timezone_name_from_abbr() ([#4779](/roundcube/roundcubemail/issues/4779))
 * Fix handling of %-encoded entities in mailto: URLs ([#4799](/roundcube/roundcubemail/issues/4799))
 * Fix bug where messages count was not updated after message move/delete with skip_deleted=false ([#4814](/roundcube/roundcubemail/issues/4814))
 * Fix security issue in contact photo handling ([#4817](/roundcube/roundcubemail/issues/4817))
 * Fix bug where database_attachments_cache setting was not working
 * Fix attached file path unsetting in database_attachments plugin ([#4823](/roundcube/roundcubemail/issues/4823))
 * Fix issues when using moduserprefs.sh without --user argument ([#4825](/roundcube/roundcubemail/issues/4825))

## RELEASE 1.0.5

 * Fix bug where some valid text in a message was handled as uuencoded attachment
 * Fix wrong icon for download button in classic skin
 * Fix bug where sent message was saved in Sent folder even if disabled by user ([#4729](/roundcube/roundcubemail/issues/4729))
 * Fix checks based on window.ActiveXObject in IE > 10
 * Fix XSS issue in style attribute handling ([#4739](/roundcube/roundcubemail/issues/4739))
 * Fix bug where Drafts list wasn't updated on draft-save action in new window ([#4737](/roundcube/roundcubemail/issues/4737))
 * Fix so "set as default" option is hidden if identities_level > 1 ([#4738](/roundcube/roundcubemail/issues/4738))
 * Fix bug where search was reset after returning from compose visited for reply
 * Fix javascript error in "IE 8.0/Tablet PC" browser ([#4730](/roundcube/roundcubemail/issues/4730))
 * Fix bug where empty fieldmap config entries caused empty results of ldap search ([#4741](/roundcube/roundcubemail/issues/4741))

## RELEASE 1.0.4

 * Disable TinyMCE contextmenu plugin as there are more cons than pros in using it ([#4684](/roundcube/roundcubemail/issues/4684))
 * Fix bug where show_real_foldernames setting wasn't honored on compose page ([#4705](/roundcube/roundcubemail/issues/4705))
 * Fix issue where Archive folder wasn't protected in Folder Manager ([#4706](/roundcube/roundcubemail/issues/4706))
 * Fix compatibility with PHP 5.2. in rcube_imap_generic ([#4682](/roundcube/roundcubemail/issues/4682))
 * Fix setting flags on servers with no PERMANENTFLAGS response ([#4667](/roundcube/roundcubemail/issues/4667))
 * Fix regression in SHAA password generation in ldap driver of password plugin ([#4670](/roundcube/roundcubemail/issues/4670))
 * Fix displaying of HTML messages with absolutely positioned elements in Larry skin ([#4672](/roundcube/roundcubemail/issues/4672))
 * Fix font style display issue in HTML messages with styled <span> elements ([#4671](/roundcube/roundcubemail/issues/4671))
 * Fix download of attachments that are part of TNEF message ([#4668](/roundcube/roundcubemail/issues/4668))
 * Fix handling of uuencoded messages if messages_cache is enabled ([#4675](/roundcube/roundcubemail/issues/4675))
 * Fix handling of base64-encoded attachments with extra spaces ([#4678](/roundcube/roundcubemail/issues/4678))
 * Fix handling of UNKNOWN-CTE response, try do decode content client-side ([#4650](/roundcube/roundcubemail/issues/4650))
 * Fix bug where creating subfolders in shared folders wasn't possible without ACL extension ([#4680](/roundcube/roundcubemail/issues/4680))
 * Fix reply scrolling issue with text mode and start message below the quote ([#4681](/roundcube/roundcubemail/issues/4681))
 * Fix possible issues in skin/skin_path config handling ([#4689](/roundcube/roundcubemail/issues/4689))
 * Fix lack of delimiter for recipient addresses in smtp_log ([#4703](/roundcube/roundcubemail/issues/4703))
 * Fix generation of Blowfish-based password hashes ([#4721](/roundcube/roundcubemail/issues/4721))
 * Fix bugs where CSRF attacks were still possible on some requests

## RELEASE 1.0.3

 * Fix insert-signature command in external compose window if opened from inline compose screen ([#4663](/roundcube/roundcubemail/issues/4663))
 * Initialize HTML editor before restoring a message from localStorage ([#4631](/roundcube/roundcubemail/issues/4631))
 * Add 'sig_max_lines' config option to default config file ([#5162](/roundcube/roundcubemail/issues/5162))
 * Add option to specify IMAP connection socket parameters - imap_conn_options ([#4589](/roundcube/roundcubemail/issues/4589))
 * Add option to set default message list mode - default_list_mode ([#3157](/roundcube/roundcubemail/issues/3157))
 * Enable contextmenu plugin for TinyMCE editor ([#3062](/roundcube/roundcubemail/issues/3062))
 * Fix some mime-type to extension mapping checks in Installer ([#4610](/roundcube/roundcubemail/issues/4610))
 * Fix errors when using localStorage in Safari's private browsing mode ([#4619](/roundcube/roundcubemail/issues/4619))
 * Fix bug where $Forwarded flag was being set even if server didn't support it ([#4621](/roundcube/roundcubemail/issues/4621))
 * Fix various iCloud vCard issues, added fallback for external photos ([#4617](/roundcube/roundcubemail/issues/4617))
 * Fix invalid Content-Type header when send_format_flowed=false ([#4616](/roundcube/roundcubemail/issues/4616))
 * Fix errors when adding/updating contacts in active search ([#4630](/roundcube/roundcubemail/issues/4630))
 * Fix incorrect thumbnail rotation with GD and exif orientation data ([#4641](/roundcube/roundcubemail/issues/4641))
 * Fix contacts list update after adding/deleting/moving a contact ([#4640](/roundcube/roundcubemail/issues/4640), [#4644](/roundcube/roundcubemail/issues/4644))
 * Fix handling of email addresses with quoted domain part ([#4647](/roundcube/roundcubemail/issues/4647))
 * Fix comm_path update on task switch ([#4648](/roundcube/roundcubemail/issues/4648))
 * Fix error in MSSQL update script 2013061000.sql ([#4658](/roundcube/roundcubemail/issues/4658))
 * Fix validation of email addresses with IDNA domains ([#4661](/roundcube/roundcubemail/issues/4661))

## RELEASE 1.0.2

 * Fix storing unsaved drafts in localStorage ([#4529](/roundcube/roundcubemail/issues/4529))
 * Fix redundant horizontal scrollbar in HTML editor ([#4591](/roundcube/roundcubemail/issues/4591))
 * Fix PHP error in Preferences when default_folders was in dont_override ([#4581](/roundcube/roundcubemail/issues/4581))
 * Add configurable LDAP_OPT_DEREF option ([#4546](/roundcube/roundcubemail/issues/4546))
 * Fix unintentional draft autosave request if autosave is disabled ([#4550](/roundcube/roundcubemail/issues/4550))
 * Fix malformed References: header in send/saved mail ([#4552](/roundcube/roundcubemail/issues/4552))
 * Fix handling unicode characters in links ([#4555](/roundcube/roundcubemail/issues/4555))
 * Fix incorrect handling of HTML comments in messages sanitization code ([#4558](/roundcube/roundcubemail/issues/4558))
 * Fix so current page is reset on list-mode change ([#4561](/roundcube/roundcubemail/issues/4561))
 * Fix so responses menu hides on click in classic skin ([#4566](/roundcube/roundcubemail/issues/4566))
 * Fix unintentional line-height style modification in HTML messages ([#4567](/roundcube/roundcubemail/issues/4567))
 * Fix broken normalize_string(), add support for ISO-8859-2 ([#4568](/roundcube/roundcubemail/issues/4568))
 * Support csv contacts import in German localization ([#4570](/roundcube/roundcubemail/issues/4570))
 * Fix so message list and counters are updated when a message is opened in new window ([#4569](/roundcube/roundcubemail/issues/4569))
 * Fix malformed recipient name when composing a message by clicking on mailto link ([#4583](/roundcube/roundcubemail/issues/4583))
 * Fix list reload after sending message in another window ([#4576](/roundcube/roundcubemail/issues/4576))
 * Fix so address format errors are ignored when saving a draft ([#4594](/roundcube/roundcubemail/issues/4594))
 * Fix incorrect label translation in return receipt ([#4598](/roundcube/roundcubemail/issues/4598))
 * Fix security issue in delete-response action - allow only ajax request
 * Fix Delete button state after deleting identity/response ([#4603](/roundcube/roundcubemail/issues/4603))
 * Fix bug where contacts with no email address were listed on compose addressbook ([#4602](/roundcube/roundcubemail/issues/4602))
 * Fix images import from various vCard formats ([#4604](/roundcube/roundcubemail/issues/4604))
 * Fix sorting messages by size on servers without SORT capability ([#4608](/roundcube/roundcubemail/issues/4608))

## RELEASE 1.0.1

 * Support 'error' and 'body_file' return attribs in 'message_before_send' hook ([#4467](/roundcube/roundcubemail/issues/4467))
 * Apply user-specific replacements to group's base_dn property ([#4512](/roundcube/roundcubemail/issues/4512))
 * Fix missing email address when importing contacts from outlook csv ([#4535](/roundcube/roundcubemail/issues/4535))
 * Fix bug where "With attachment" option in search filter wasn't selected after return from mail view ([#4508](/roundcube/roundcubemail/issues/4508))
 * Fix "washing" of unicoded style attributes ([#4510](/roundcube/roundcubemail/issues/4510))
 * Fix unintentional redirect from compose page in Webkit browsers ([#4516](/roundcube/roundcubemail/issues/4516))
 * Fix messages index cache update under some conditions (e.g. proxy) ([#4505](/roundcube/roundcubemail/issues/4505))
 * Fix lack of translation of special folders in some configurations ([#4520](/roundcube/roundcubemail/issues/4520))
 * Fix XSS issue in plain text spellchecker ([#4524](/roundcube/roundcubemail/issues/4524))
 * Fix invalid page title for some folders (1489804)
 * Fix redundant alert message on over-size uploads ([#4528](/roundcube/roundcubemail/issues/4528))
 * Fix next message display after removing a message ([#4521](/roundcube/roundcubemail/issues/4521))
 * Fix missing Mail-Followup-To header in sent mail ([#4534](/roundcube/roundcubemail/issues/4534))
 * Fix error when spell-checking an empty text ([#4536](/roundcube/roundcubemail/issues/4536))
 * Avoid popupmenus being closed when scrollbar is clicked ([#4537](/roundcube/roundcubemail/issues/4537))
 * Add proxy_whitelist configuration option ([#4496](/roundcube/roundcubemail/issues/4496))
 * Fix identities_level=4 handling in new_user_dialog plugin ([#4540](/roundcube/roundcubemail/issues/4540))
 * Fix various db_prefix issues ([#4539](/roundcube/roundcubemail/issues/4539))
 * Fix too small length of users.preferences column data type on MySQL
 * Fix redundant warning when switching from html to text in empty editor ([#4530](/roundcube/roundcubemail/issues/4530))
 * Fix invalid host validation on login ([#4541](/roundcube/roundcubemail/issues/4541))
 * Fix IMAP connection test in installer so it is aware of imap_auth_type ([#4502](/roundcube/roundcubemail/issues/4502))

## RELEASE 1.0.0

 * Fix style of disabled protocol handler link on IE ([#4460](/roundcube/roundcubemail/issues/4460))
 * Fix message import dialog when no file is selected ([#4488](/roundcube/roundcubemail/issues/4488))
 * Fix opening compose screen in new window after saving as draft ([#4479](/roundcube/roundcubemail/issues/4479))
 * Added toolbar button to move message in message view
 * Fix directories check in Installer on Windows ([#4462](/roundcube/roundcubemail/issues/4462))
 * Fix issue when default_addressbook option is set to integer value ([#4379](/roundcube/roundcubemail/issues/4379))
 * Fix Opera > 15 detection ([#4455](/roundcube/roundcubemail/issues/4455))
 * Fix security issue in DomainFactory driver of Password plugin
 * Fix invalid X-Draft-Info on forwarded message draft ([#4464](/roundcube/roundcubemail/issues/4464))
 * Fix regression in handling of 'attachments' result in message_compose hook ([#4474](/roundcube/roundcubemail/issues/4474))
 * Fix issue where msgexport.sh printed the message to STDOUT instead of a file ([#4476](/roundcube/roundcubemail/issues/4476))
 * Fix fatal error in database_attachments plugin under some conditions ([#4495](/roundcube/roundcubemail/issues/4495))

## RELEASE 1.0-RC

 * Small CSS fix with message notice boxes in Larry skin ([#4429](/roundcube/roundcubemail/issues/4429))
 * Include groups in contacts search on mail compose ([#4186](/roundcube/roundcubemail/issues/4186))
 * Add mime-type mapping for .7z files ([#4436](/roundcube/roundcubemail/issues/4436))
 * Invoke update scripts with php to circumvent execution restrictions ([#4330](/roundcube/roundcubemail/issues/4330))
 * Fix drag & drop message/contact moving on touch device ([#4395](/roundcube/roundcubemail/issues/4395))
 * Fix canned responses in HTML mode ([#4446](/roundcube/roundcubemail/issues/4446))
 * Check/create default folders on every login not only the first ([#4391](/roundcube/roundcubemail/issues/4391))
 * Update to jQuery-1.11.0 and jQuery-UI-1.9.2
 * Support SMTP socket context options via new config option 'smtp_conn_options'
 * Fix compatibility with PHP 5.2 in html.php file ([#4438](/roundcube/roundcubemail/issues/4438))
 * Remove expand/collapse with plus/minus keys (on numeric keypad) ([#4437](/roundcube/roundcubemail/issues/4437))
 * Fix issue where filesystem path was added to all-attachments (zip) file ([#4433](/roundcube/roundcubemail/issues/4433))
 * Fix case-sensitivity of email addresses handling on compose ([#1899](/roundcube/roundcubemail/issues/1899))
 * Don't alter Message-ID of a draft when sending ([#4381](/roundcube/roundcubemail/issues/4381))
 * Fix issue where deprecated syntax for HTML lists was not handled properly ([#3975](/roundcube/roundcubemail/issues/3975))
 * Display different icons when Trash folder is empty or full ([#2108](/roundcube/roundcubemail/issues/2108))
 * Remember last position of more headers switch ([#3660](/roundcube/roundcubemail/issues/3660))
 * Fix so message flags modified by another client are applied on the list on refresh ([#1639](/roundcube/roundcubemail/issues/1639))
 * Fix broken text/* attachments when forwarding/editing a message ([#4393](/roundcube/roundcubemail/issues/4393))
 * Improved minified files handling, added css minification ([#3041](/roundcube/roundcubemail/issues/3041))
 * Fix handling of X-Forwarded-For header with multiple addresses ([#4424](/roundcube/roundcubemail/issues/4424))
 * Fix border issue on folders list in classic skin ([#4419](/roundcube/roundcubemail/issues/4419))
 * Implemented menu actions to copy/move messages, added folder-selector widget ([#863](/roundcube/roundcubemail/issues/863))
 * Fix security rules in .htaccess preventing access to base URL without the ending slash ([#4422](/roundcube/roundcubemail/issues/4422))
 * Fix regression where only first new folder was placed in correct place on the list ([#4418](/roundcube/roundcubemail/issues/4418))
 * Fix issue where children of selected and collapsed thread were skipped on various actions ([#4410](/roundcube/roundcubemail/issues/4410))
 * Fix issue where groups were not deleted when "Replace entire addressbook" option on contacts import was used ([#4388](/roundcube/roundcubemail/issues/4388))
 * Fix unreliable mimetype tests in Installer ([#4408](/roundcube/roundcubemail/issues/4408))
 * Fix performance of listing writeable folders ([#4406](/roundcube/roundcubemail/issues/4406))

## RELEASE 1.0-beta

 * Fix handling of invalid closing tags in HTML messages ([#4403](/roundcube/roundcubemail/issues/4403))
 * Set real content-type for file downloads ([#4400](/roundcube/roundcubemail/issues/4400))
 * Update TinyMCE to version 3.5.10 ([#4401](/roundcube/roundcubemail/issues/4401))
 * Fix keyboard navigation in list widgets ([#4367](/roundcube/roundcubemail/issues/4367))
 * Allow plugins to grab the reference of opened windows ([#4383](/roundcube/roundcubemail/issues/4383))
 * Larry skin: Improved status message display for better visibility ([#4115](/roundcube/roundcubemail/issues/4115))
 * Fix Internet Explorer 11 detection ([#4397](/roundcube/roundcubemail/issues/4397))
 * Fix date column width to fit the widest possible date format ([#4354](/roundcube/roundcubemail/issues/4354))
 * Move certain user preference options to a collapsed "advanced" block ([#4015](/roundcube/roundcubemail/issues/4015))
 * Add file type icons for Powerpoint and Open Office presentations ([#4269](/roundcube/roundcubemail/issues/4269))
 * Fix operations on folders with trailing spaces in name ([#4387](/roundcube/roundcubemail/issues/4387))
 * Improve identity selection based on From: header ([#4360](/roundcube/roundcubemail/issues/4360))
 * Fix issue where mails with inline images of the same name contained only the first image multiple times ([#4378](/roundcube/roundcubemail/issues/4378))
 * Use left/right arrow keys to collapse/expand thread and spacebar to select a row, change Ctrl key behavior ([#4367](/roundcube/roundcubemail/issues/4367))
 * Fix an issue where using arrow keys to go up a list can result in selected message being under headers ([#4375](/roundcube/roundcubemail/issues/4375))
 * Fix an issue where Home/End keys don't focus list row properly, don't scrollTo properly ([#4370](/roundcube/roundcubemail/issues/4370))
 * Add an option to disable smart Reply-List behaviour - reply_all_mode ([#3953](/roundcube/roundcubemail/issues/3953))
 * Fix an issue where pressing minus key on contacts list was hiding list records ([#4368](/roundcube/roundcubemail/issues/4368))
 * Fix an issue where shift + arrow-up key wasn't selecting all messages in collapsed thread ([#4371](/roundcube/roundcubemail/issues/4371))
 * Added icon for priority column in messages list header ([#4275](/roundcube/roundcubemail/issues/4275))
 * New feature "Canned Responses" to save and recall boilerplate text snippets
 * Fix HTML part detection when encapsulated inside multipart/signed ([#4357](/roundcube/roundcubemail/issues/4357))
 * Add spellchecker backend for the After the Deadline service
 * Replace markdown-style [1] link indexes in plain text email bodies
 * Improved mailto: link arguments handling ([#4351](/roundcube/roundcubemail/issues/4351))
 * Use DOMDocument LIBXML_PARSEHUGE and LIBXML_COMPACT options if possible ([#4316](/roundcube/roundcubemail/issues/4316))
 * Support HTTP_HOST, SERVER_NAME and SERVER_ADDR values in include_host_config feature
 * Make default font size for HTML messages configurable (request #118)
 * Fix XSS issue in addressbook group name field [CVE-2013-5646] ([#4337](/roundcube/roundcubemail/issues/4337))
 * After message is sent refresh messages list of replied message folder ([#4282](/roundcube/roundcubemail/issues/4282))
 * Add option force specified domain in user login - username_domain_forced ([#4290](/roundcube/roundcubemail/issues/4290))
 * Add option to import Vcards with group assignments
 * Save groups membership in Vcard export ([#3801](/roundcube/roundcubemail/issues/3801))
 * Workaround broken PHP function timezone_name_from_abbr ([#4289](/roundcube/roundcubemail/issues/4289))
 * Make cached message size limit configurable - messages_cache_threshold ([#4326](/roundcube/roundcubemail/issues/4326))
 * Log also failed logins to userlogins log
 * Add temp_dir_ttl configuration option ([#4318](/roundcube/roundcubemail/issues/4318))
 * Allow setting INBOX as Sent folder ([#4264](/roundcube/roundcubemail/issues/4264))
 * Fix replacement variables in user-specific base_dn in some LDAP requests ([#4299](/roundcube/roundcubemail/issues/4299))
 * Fix image scaling issues when image has only one dimension smaller than the limit ([#4296](/roundcube/roundcubemail/issues/4296))
 * Fix issue where uploaded photo was lost when contact form did not validate ([#4296](/roundcube/roundcubemail/issues/4296))
 * Move identity selection based on non-standard headers into (new) identity_select plugin ([#3835](/roundcube/roundcubemail/issues/3835))
 * Fix downloading binary files with (wrong) text/* content-type ([#4292](/roundcube/roundcubemail/issues/4292))
 * Respect HTTP_X_FORWARDED_FOR and HTTP_X_REAL_IP variables for session IP check
 * Simplified configuration by merging it into one file + defaults ([#3156](/roundcube/roundcubemail/issues/3156))
 * Make message list header stay on top when scrolling ([#353](/roundcube/roundcubemail/issues/353))
 * Add support for 'enchant' spellcheck engine
 * Check filetype detection in installer and update script ([#4252](/roundcube/roundcubemail/issues/4252))
 * Fix folder names truncation in Classic skin ([#4265](/roundcube/roundcubemail/issues/4265))
 * Make possible to disable some (broken) IMAP extensions with imap_disable_caps option ([#4245](/roundcube/roundcubemail/issues/4245))
 * Contacts drag-n-drop default action is to move contacts ([#3962](/roundcube/roundcubemail/issues/3962))
 * Added possibility to choose to move or copy contacts from drag-n-drop menu ([#3962](/roundcube/roundcubemail/issues/3962))
 * Fix Close link and remove About link on error pages ([#4201](/roundcube/roundcubemail/issues/4201))
 * Improved/unified attachment preview screen, added print button
 * Fix lack of space between searchfiler and quicksearchbar in Larry skin ([#4233](/roundcube/roundcubemail/issues/4233))
 * Cache LDAP's user_specific search and use vlv for better performance ([#4247](/roundcube/roundcubemail/issues/4247))
 * LDAP: auto-detect and use VLV indices for all search operations
 * LDAP: additional group configuration options for  address books
 * LDAP: separated address book implementation from a generic LDAP wrapper class
 * Allow address books to browse a multi-level group hierarchy in the contacts list
 * Fix session issues when local and database time differs ([#2401](/roundcube/roundcubemail/issues/2401))
 * Fix thread cache syncronization/validation ([#4150](/roundcube/roundcubemail/issues/4150))
 * Added feature to import messages to the currently selected folder
 * Add option show_real_foldernames to disable localization of special folders
 * Fix database cache expunge issues ([#4229](/roundcube/roundcubemail/issues/4229))
 * Fix date format issues on MS SQL Server ([#4078](/roundcube/roundcubemail/issues/4078))
 * Add imap_cache_ttl option to configure TTL of imap_cache
 * Make LDAP cache engine configurable via ldap_cache and ldap_cache_ttl options
 * Fix "duplicate entry" errors on inserts to imap cache tables ([#4228](/roundcube/roundcubemail/issues/4228))
 * Improved handling of Reply-To/Bcc addresses of identity in compose form ([#4142](/roundcube/roundcubemail/issues/4142))
 * Added user preference to open all popups as standard windows
 * Implemented shared cache (rcube_cache_shared)
 * Change Reply-All button label/title when mailing list is detected ([#4092](/roundcube/roundcubemail/issues/4092))
 * Fix SMTP connection using IPv6 address in smtp_server option ([#4147](/roundcube/roundcubemail/issues/4147))
 * Added attachment_reminder plugin
 * Make PHP code eval() free, use create_function()
 * Add option to display email address together with a name in mail preview ([#3952](/roundcube/roundcubemail/issues/3952))
 * Support CSV import from Atmail ([#4161](/roundcube/roundcubemail/issues/4161))
 * Add db_prefix configuration option in place of db_table_*/db_sequence_* options
 * Make possible to use db_prefix for schema initialization in Installer ([#4175](/roundcube/roundcubemail/issues/4175))
 * Fix updatedb.sh script so it recognizes also table prefix for external DDL files
 * Fix parsing invalid date string ([#4155](/roundcube/roundcubemail/issues/4155))
 * Add "with attachment" option to messages list filter ([#1795](/roundcube/roundcubemail/issues/1795))
 * Call resize handler in intervals to prevent lags and double onresize calls in Chrome ([#4137](/roundcube/roundcubemail/issues/4137))
 * Add rel="noreferrer" for links in displayed messages ([#4976](/roundcube/roundcubemail/issues/4976))
 * Add ability to toggle between HTML and text while viewing a message ([#3005](/roundcube/roundcubemail/issues/3005))
 * Remove "HTML message" from attachments list while viewing a message in text mode ([#3005](/roundcube/roundcubemail/issues/3005))
 * Support IMAP MOVE extension [RFC 6851]
 * Add attachment menu with Open and Download options ([#4116](/roundcube/roundcubemail/issues/4116))
 * Display user-friendly message on IMAP "over quota" errors ([#914](/roundcube/roundcubemail/issues/914))
 * Extended archive plugin with user-configurable options to store messages into subfolders
 * Fix export of selected contacts from search result ([#4070](/roundcube/roundcubemail/issues/4070))
 * Feature to export only selected contacts from addressbook (by Phil Weir)

## RELEASE 0.9.5

 * Fix failing vCard import when email address field contains spaces ([#4363](/roundcube/roundcubemail/issues/4363))
 * Fix default spell-check configuration after Google suspended their spell service
 * Fix vulnerability in handling _session argument of utils/save-prefs ([#4362](/roundcube/roundcubemail/issues/4362))
 * Fix iframe onload for upload errors handling ([#4361](/roundcube/roundcubemail/issues/4361))
 * Fix address matching in Return-Path header on identity selection ([#4358](/roundcube/roundcubemail/issues/4358))
 * Fix text wrapping issue with long unwrappable lines ([#4356](/roundcube/roundcubemail/issues/4356))
 * Fixed mispelling: occured -> occurred ([#4353](/roundcube/roundcubemail/issues/4353))
 * Fixed issues where HTML comments inside style tag would hang Internet Explorer
 * Fix setting domain in virtualmin password driver ([#4336](/roundcube/roundcubemail/issues/4336))
 * Hide Delivery Status Notification option when smtp_server is unset ([#4339](/roundcube/roundcubemail/issues/4339))
 * Display full attachment name using title attribute when name is too long to display ([#4328](/roundcube/roundcubemail/issues/4328))
 * Fix attachment icon issue when rare font/language is used ([#4334](/roundcube/roundcubemail/issues/4334))
 * Fix expanded thread root message styling after refreshing messages list ([#4335](/roundcube/roundcubemail/issues/4335))
 * Fix issue where From address was removed from Cc and Bcc fields when editing a draft ([#4327](/roundcube/roundcubemail/issues/4327))
 * Fix error_reporting directive check ([#4331](/roundcube/roundcubemail/issues/4331))
 * Fix de_DE localization of "About" label in Help plugin ([#4333](/roundcube/roundcubemail/issues/4333))

## RELEASE 0.9.4

 * Make identities matching case insensitive ([#1881](/roundcube/roundcubemail/issues/1881))
 * Fix issue where too big message data was stored in cache causing sql errors ([#4325](/roundcube/roundcubemail/issues/4325))
 * Fix iframe scrollbars on webkit desktop browsers ([#4319](/roundcube/roundcubemail/issues/4319))
 * Fix issue where legacy config was overriden by default config ([#4305](/roundcube/roundcubemail/issues/4305))
 * Fix newmail_notifier issue where favicon wasn't changed back to default ([#4324](/roundcube/roundcubemail/issues/4324))
 * Fix setting of Junk and NonJunk flags by markasjunk plugin ([#4303](/roundcube/roundcubemail/issues/4303))
 * Fix lack of Reply-To address in header of forwarded message body ([#4314](/roundcube/roundcubemail/issues/4314))
 * Fix bugs when invoking contact creation form when read-only addressbook is selected ([#4313](/roundcube/roundcubemail/issues/4313))
 * Fix identity selection on reply ([#4308](/roundcube/roundcubemail/issues/4308))
 * Fix so additional headers are added to all messages sent ([#4302](/roundcube/roundcubemail/issues/4302))
 * Fix display issue after moving folder in Folder Manager ([#4310](/roundcube/roundcubemail/issues/4310))
 * Fix handling of non-default date formats ([#4311](/roundcube/roundcubemail/issues/4311))
 * Fix unquoted path in PREG expression on Windows ([#4307](/roundcube/roundcubemail/issues/4307))
 * Fix Junk folder icon alignment when it's nested in inbox folder ([#4309](/roundcube/roundcubemail/issues/4309))
 * Fix wrong close tag in /template/mail.html ([#4312](/roundcube/roundcubemail/issues/4312))

## RELEASE 0.9.3

 * Optimized UI behavior for touch devices
 * Fix setting refresh_interval to "Never" in Preferences ([#4304](/roundcube/roundcubemail/issues/4304))
 * Fix purge action in folder manager ([#4300](/roundcube/roundcubemail/issues/4300))
 * Fix base URL resolving on attribute values with no quotes ([#4297](/roundcube/roundcubemail/issues/4297))
 * Fix wrong handling of links with '|' character ([#4298](/roundcube/roundcubemail/issues/4298))
 * Fix colorspace issue on image conversion using ImageMagick ([#4294](/roundcube/roundcubemail/issues/4294))
 * Fix XSS vulnerability when saving HTML signatures ([#4283](/roundcube/roundcubemail/issues/4283))
 * Fix XSS vulnerability when editing a message "as new" or draft ([#4283](/roundcube/roundcubemail/issues/4283))
 * Fix rewrite rule in .htaccess ([#4278](/roundcube/roundcubemail/issues/4278))
 * Fix detecting Turkish language in ISO-8859-9 encoding ([#4284](/roundcube/roundcubemail/issues/4284))
 * Fix identity-selection using Return-Path headers ([#4279](/roundcube/roundcubemail/issues/4279))
 * Fix parsing of links with ... in URL ([#4251](/roundcube/roundcubemail/issues/4251))
 * Fix compose priority selector when opening in new window ([#4286](/roundcube/roundcubemail/issues/4286))
 * Fix bug where signature wasn't changed on identity selection when editing a draft ([#4272](/roundcube/roundcubemail/issues/4272))
 * Fix IMAP SETMETADATA parameters quoting ([#4274](/roundcube/roundcubemail/issues/4274))
 * Fix "could not load message" error on valid empty message body ([#4271](/roundcube/roundcubemail/issues/4271))
 * Fix handling of message/rfc822 attachments on message forward and edit ([#4262](/roundcube/roundcubemail/issues/4262))
 * Fix parsing of square bracket characters in IMAP response strings ([#4267](/roundcube/roundcubemail/issues/4267))
 * Don't clear References and in-Reply-To when a message is "edited as new" ([#4263](/roundcube/roundcubemail/issues/4263))
 * Fix messages list sorting with THREAD=REFS
 * Remove deprecated (in PHP 5.5) PREG /e modifier usage ([#4239](/roundcube/roundcubemail/issues/4239))
 * Fix empty messages list when register_globals is enabled ([#4232](/roundcube/roundcubemail/issues/4232))
 * Fix so valid and set date.timezone is not required by installer checks ([#4242](/roundcube/roundcubemail/issues/4242))
 * Canonize boolean ini_get() results ([#4249](/roundcube/roundcubemail/issues/4249))
 * Fix so install do not fail when one of DB driver checks fails but other drivers exist ([#4240](/roundcube/roundcubemail/issues/4240))
 * Fix so exported vCard specifies encoding in v3-compatible format ([#4244](/roundcube/roundcubemail/issues/4244))

## RELEASE 0.9.2

 * Fix image thumbnails display in print mode ([#4220](/roundcube/roundcubemail/issues/4220))
 * Fix height of message headers block ([#4200](/roundcube/roundcubemail/issues/4200))
 * Fix timeout issue on drag&drop uploads ([#4238](/roundcube/roundcubemail/issues/4238))
 * Fix default sorting of threaded list when THREAD=REFS isn't supported
 * Fix list mode switch to 'List' after saving list settings in Larry skin ([#4236](/roundcube/roundcubemail/issues/4236))
 * Fix error when there's no writeable addressbook source ([#4235](/roundcube/roundcubemail/issues/4235))
 * Fix zipdownload plugin issue with filenames charset ([#4231](/roundcube/roundcubemail/issues/4231))
 * Fix so non-inline images aren't skipped on forward ([#4230](/roundcube/roundcubemail/issues/4230))
 * Fix "null" instead of empty string on messages list in IE10 ([#4227](/roundcube/roundcubemail/issues/4227))
 * Fix legacy options handling
 * Fix so bounces addresses in Sender headers are skipped on Reply-All ([#4140](/roundcube/roundcubemail/issues/4140))
 * Fix bug where serialized strings were truncated in PDO::quote() ([#4226](/roundcube/roundcubemail/issues/4226))
 * Fix displaying messages with invalid self-closing HTML tags ([#4223](/roundcube/roundcubemail/issues/4223))
 * Fix PHP warning when responding to a message with many Return-Path headers ([#4222](/roundcube/roundcubemail/issues/4222))
 * Fix unintentional compose window resize ([#4206](/roundcube/roundcubemail/issues/4206))
 * Fix performance regression in text wrapping function ([#4219](/roundcube/roundcubemail/issues/4219))
 * Fix connection to posgtres db using unix socket ([#4218](/roundcube/roundcubemail/issues/4218))
 * Fix handling of comma when adding contact from contacts widget ([#4199](/roundcube/roundcubemail/issues/4199))
 * Fix bug where a message was opened in both preview pane and new window on double-click ([#4212](/roundcube/roundcubemail/issues/4212))
 * Fix fatal error when xdebug.max_nesting_level was exceeded in rcube_washtml ([#4202](/roundcube/roundcubemail/issues/4202))
 * Fix PHP warning in html_table::set_row_attribs() in PHP 5.4 ([#4194](/roundcube/roundcubemail/issues/4194))
 * Fix invalid option selected in default_font selector when font is unset ([#4204](/roundcube/roundcubemail/issues/4204))
 * Fix displaying contact with ID divisible by 100 in sql addressbook ([#4211](/roundcube/roundcubemail/issues/4211))
 * Fix browser warnings on PDF plugin detection ([#4209](/roundcube/roundcubemail/issues/4209))
 * Fix fatal error when parsing UUencoded messages ([#4210](/roundcube/roundcubemail/issues/4210))

## RELEASE 0.9.1

 * Better German labels for from/to to avoid conflicts with 'sender' ([#4188](/roundcube/roundcubemail/issues/4188))
 * Fix problem where security warning was displayed for valid images with image/jpg type ([#4196](/roundcube/roundcubemail/issues/4196))
 * Fix handling of invalid email addresses in headers ([#4193](/roundcube/roundcubemail/issues/4193))
 * Fix IMAP connection issue with default_socket_timeout < 0 and imap_timeout < 0 ([#4191](/roundcube/roundcubemail/issues/4191))
 * Fix various PHP code bugs found using static analysis ([#4190](/roundcube/roundcubemail/issues/4190))
 * Fix backslash character handling on vCard import ([#4189](/roundcube/roundcubemail/issues/4189))
 * Fix csv import from Thunderbird with French localization ([#4170](/roundcube/roundcubemail/issues/4170))
 * Fix messages list focus issue in Opera and Webkit ([#4169](/roundcube/roundcubemail/issues/4169))
 * Fix Reply-To header handling in Reply-All action ([#4157](/roundcube/roundcubemail/issues/4157))
 * Fix so Sender: address is added to Cc: field on reply to all ([#4140](/roundcube/roundcubemail/issues/4140))
 * Fix so addressbook_search_mode works also for group search ([#4183](/roundcube/roundcubemail/issues/4183))
 * Fix removal of a contact from a group in LDAP addressbook ([#4185](/roundcube/roundcubemail/issues/4185))
 * Inlcude SQL query in the log on SQL error ([#4172](/roundcube/roundcubemail/issues/4172))
 * Fix handling untagged responses in IMAP FETCH - "could not load message" error ([#4180](/roundcube/roundcubemail/issues/4180))
 * Fix very small window size in Chrome ([#4087](/roundcube/roundcubemail/issues/4087))
 * Fix list page reset when viewing a message in Larry skin ([#4182](/roundcube/roundcubemail/issues/4182))
 * Fix min_refresh_interval handling on preferences save ([#4179](/roundcube/roundcubemail/issues/4179))
 * Fix PDF support detection for Firefox PDF.js ([#4113](/roundcube/roundcubemail/issues/4113))
 * Fix possible collision in generated thumbnail cache key ([#4177](/roundcube/roundcubemail/issues/4177))
 * Fix exit code on bootsrap errors in CLI mode ([#4160](/roundcube/roundcubemail/issues/4160))
 * Fix error handling in CLI mode, use STDERR and non-empty exit code ([#5161](/roundcube/roundcubemail/issues/5161))
 * Fix error when using check_referer=true
 * Fix incorrect handling of some specific links ([#4171](/roundcube/roundcubemail/issues/4171))
 * Fix incorrect handling of leading spaces in text wrapping
 * Fix unintentional messages list jumps on click in Internet Explorer ([#4167](/roundcube/roundcubemail/issues/4167))
 * Fix list of required configuration options ([#4166](/roundcube/roundcubemail/issues/4166))
 * Fix DB error when creating a new contact and a group is selected ([#4164](/roundcube/roundcubemail/issues/4164))
 * Fix handling of deprecated boolean value of reply_mode option ([#4165](/roundcube/roundcubemail/issues/4165))

## RELEASE 0.9.0

 * Fix display of HTML entities in protected folder name ([#4159](/roundcube/roundcubemail/issues/4159))
 * Set minimal permissions to temp files ([#4131](/roundcube/roundcubemail/issues/4131))
 * Improve content check for embedded images without filename ([#4151](/roundcube/roundcubemail/issues/4151))
 * Fix handling of invalid characters in message headers and output ([#4153](/roundcube/roundcubemail/issues/4153))
 * Avoid race-conditions with concurrent attachment uploads ([#3739](/roundcube/roundcubemail/issues/3739))
 * Fix selecting collapsed rows on select-all ([#4156](/roundcube/roundcubemail/issues/4156))
 * Fix possible header duplicates when using additional headers ([#4154](/roundcube/roundcubemail/issues/4154))
 * Fix session issues with use_https=true ([#4125](/roundcube/roundcubemail/issues/4125))
 * Fix blockquote width in sent mail ([#4152](/roundcube/roundcubemail/issues/4152))
 * Fix keyboard events on list widgets in Internet Explorer ([#4148](/roundcube/roundcubemail/issues/4148))

## RELEASE 0.9-rc2

 * Fix security issue in save-pref command
 * Remove sig_above configuration option, use reply_mode only ([#4135](/roundcube/roundcubemail/issues/4135))
 * Refresh current folder in opener window after draft save or message sent ([#4132](/roundcube/roundcubemail/issues/4132))
 * Fix saving draft just after entering compose window ([#4141](/roundcube/roundcubemail/issues/4141))
 * Fix javascript error in IE9 when loading form with placeholders into an iframe ([#4138](/roundcube/roundcubemail/issues/4138))
 * Fix handling of some conditional comment tags in HTML message ([#4136](/roundcube/roundcubemail/issues/4136))
 * Fix so forward as attachment works if additional attachment is added by message_compose hook ([#4134](/roundcube/roundcubemail/issues/4134))
 * Better handling of session errors in ajax requests ([#4105](/roundcube/roundcubemail/issues/4105))
 * Fix HTML part detection for some specific message structures ([#4130](/roundcube/roundcubemail/issues/4130))
 * Don't show fake address - phishing prevention ([#4120](/roundcube/roundcubemail/issues/4120))
 * Fix forward as attachment bug with editormode != 1 ([#4129](/roundcube/roundcubemail/issues/4129))
 * Fix LIMIT/OFFSET queries handling on MS SQL Server ([#4123](/roundcube/roundcubemail/issues/4123))
 * Fix javascript errors when working in a page opened with taget="_blank"
 * Mention SQLite database format change in UPGRADING file ([#4122](/roundcube/roundcubemail/issues/4122))
 * Increase maxlength to 254 chars for email input fields in addressbook ([#4126](/roundcube/roundcubemail/issues/4126))
 * Fix thumbnail size when GD extension is used for image resize ([#4124](/roundcube/roundcubemail/issues/4124))
 * Display notice that message is encrypted also for application/pkcs7-mime messages ([#3815](/roundcube/roundcubemail/issues/3815))

## Release 0.9-rc

 * Updated translations from Transifex
 * Fix plain text spellchecker icorrect highlighting in non-ASCII text ([#4114](/roundcube/roundcubemail/issues/4114))
 * Add workaround for invalid message charset detection by IMAP servers ([#4112](/roundcube/roundcubemail/issues/4112)) 
 * Fix NUL characters in content-type of ms-tnef attachment ([#4108](/roundcube/roundcubemail/issues/4108))
 * Fix regression in handling LDAP contact identifiers ([#4104](/roundcube/roundcubemail/issues/4104))
 * Fix buggy error template in a frame ([#4092](/roundcube/roundcubemail/issues/4092))
 * Add addressbook widget on compose page in classic skin
 * Add search box to compose address book widget ([#3710](/roundcube/roundcubemail/issues/3710))
 * Fix login in case when default_host is an array with one element ([#4085](/roundcube/roundcubemail/issues/4085))
 * Use LDAP fallback hosts on connect + bind instead of ldap_connect() only.
 * Add config option for LDAP bind timeout (sets LDAP_OPT_NETWORK_TIMEOUT option)
 * Submit Addressbook advanced search form with Enter key ([#3843](/roundcube/roundcubemail/issues/3843))
 * Also block remote images in HTML part view ([#4013](/roundcube/roundcubemail/issues/4013))
 * Improved database schema upgrade procedure, added updatedb.sh script
 * Force autocommit mode in mysql database driver ([#4068](/roundcube/roundcubemail/issues/4068))

## Release 0.9-beta

 * Fix searching by date in address book ([#4058](/roundcube/roundcubemail/issues/4058))
 * Improve charset detection by prioritizing charset according to user language ([#2032](/roundcube/roundcubemail/issues/2032))
 * Fix handling of escaped separator in vCard file ([#4064](/roundcube/roundcubemail/issues/4064))
 * Fix #countcontrols issue in IE<=8 when text is very long ([#4060](/roundcube/roundcubemail/issues/4060))
 * Add option to use envelope From address for MDN responses ([#4052](/roundcube/roundcubemail/issues/4052))
 * Add possibility to search in message body only ([#3977](/roundcube/roundcubemail/issues/3977))
 * Support "multipart/relative" as an alias for "multipart/related" type ([#4057](/roundcube/roundcubemail/issues/4057))
 * Display PGP/MIME signature attachments as "Digital Signature" ([#3845](/roundcube/roundcubemail/issues/3845))
 * Workaround UW-IMAP bug where hierarchy separator is added to the shared folder name ([#4051](/roundcube/roundcubemail/issues/4051))
 * Fix version comparisons with -stable suffix ([#4050](/roundcube/roundcubemail/issues/4050))
 * Add unsupported alternative parts to attachments list ([#4046](/roundcube/roundcubemail/issues/4046))
 * Add Compose button on message view page ([#3959](/roundcube/roundcubemail/issues/3959))
 * Display 'Sender' header in message preview
 * Plugin API: Added message_before_send hook
 * Fix contact copy/add-to-group operations on search result ([#4042](/roundcube/roundcubemail/issues/4042))
 * Use matching identity in MDN response ([#4043](/roundcube/roundcubemail/issues/4043))
 * Fix unwanted horizontal scrollbar in message preview header ([#4044](/roundcube/roundcubemail/issues/4044))
 * Fix handling of signatures on draft edit ([#3996](/roundcube/roundcubemail/issues/3996))
 * Fix so compacting of non-empty folder is possible also when messages list is empty ([#4039](/roundcube/roundcubemail/issues/4039))
 * Allow forwarding of multiple emails ([#2941](/roundcube/roundcubemail/issues/2941))
 * Fix big memory consumption of DB layer ([#4037](/roundcube/roundcubemail/issues/4037))
 * Add workaround for IE<=8 bug where Content-Disposition:inline was ignored ([#4028](/roundcube/roundcubemail/issues/4028))
 * Fix XSS vulnerability in vbscript: and data:text links handling ([#4033](/roundcube/roundcubemail/issues/4033))
 * Fix broken message/part bodies when FETCH response contains more untagged lines ([#4020](/roundcube/roundcubemail/issues/4020))
 * Fix empty email on identities list after identity update ([#4018](/roundcube/roundcubemail/issues/4018))
 * Add new identities_level: (4) one identity with possibility to edit only signature
 * Use Delivered-To and Envelope-To headers for identity selection ([#4024](/roundcube/roundcubemail/issues/4024), [#3835](/roundcube/roundcubemail/issues/3835))
 * Fix XSS vulnerability using Flash files ([#4014](/roundcube/roundcubemail/issues/4014))
 * Fix absolute positioning in HTML messages ([#4007](/roundcube/roundcubemail/issues/4007))
 * Fix cache (in)validation after setting \Deleted flag
 * Fix keybord events on messages list in opera browser ([#4011](/roundcube/roundcubemail/issues/4011))
 * Fix selection of collapsed thread rows ([#3978](/roundcube/roundcubemail/issues/3978))
 * Always save drafts with format=flowed in order to keep original line wraps ([#3997](/roundcube/roundcubemail/issues/3997))
 * Fix wrapping of quoted text with format=flowed ([#3561](/roundcube/roundcubemail/issues/3561))
 * Select default_addressbook on the list in Address Book ([#3624](/roundcube/roundcubemail/issues/3624))
 * Fix so mobile phone has TYPE=CELL in exported vCard ([#4004](/roundcube/roundcubemail/issues/4004))
 * Support contacts import from CSV file ([#2605](/roundcube/roundcubemail/issues/2605))
 * Improved keep-alive action. Now the interval is based on session_lifetime ([#3799](/roundcube/roundcubemail/issues/3799))
 * Added cross-task 'refresh' request for system state updates ([#3799](/roundcube/roundcubemail/issues/3799))
 * Renamed config options: keep_alive to refresh_interval, min_keep_alive to min_refresh_interval
 * Fix handling of text/enriched content on message reply/forward/edit
 * Option to display attached images as thumbnails below message body
 * Upgraded to jQuery 1.8.3 and jQuery UI 1.9.1
 * Add config option to automatically generate LDAP attributes for new entries
 * Add user settings to open message view and compose form in new windows ([#1886](/roundcube/roundcubemail/issues/1886))
 * Better client-side timezone detection using the jsTimezoneDetect library ([#3947](/roundcube/roundcubemail/issues/3947))
 * Add option to disable saving sent mail in Sent folder - no_save_sent_messages ([#3923](/roundcube/roundcubemail/issues/3923))
 * Fix handling dont_override with message_sort_col and message_sort_order settings ([#3970](/roundcube/roundcubemail/issues/3970))
 * Fix handling of URLs with asterisk characters ([#3969](/roundcube/roundcubemail/issues/3969))
 * Remove automatic to-lowercase conversion of usernames ([#3941](/roundcube/roundcubemail/issues/3941))
 * Plugin API: Add 'email_list' argument for identities data in user_create hook
 * Integrated zipdownload plugin to download all attachments ([#617](/roundcube/roundcubemail/issues/617))
 * Fix HTML special characters handling in message list/header display ([#3812](/roundcube/roundcubemail/issues/3812))
 * List related text/html part as attachment in plain text mode ([#3918](/roundcube/roundcubemail/issues/3918))
 * Use IMAP BINARY (RFC3516) extension to fetch message/part bodies
 * Fix folder creation under public namespace root ([#3910](/roundcube/roundcubemail/issues/3910))
 * Fix so "Edit as new" on draft creates a new message ([#3924](/roundcube/roundcubemail/issues/3924))
 * Fix invalid error message on deleting mail from read only folder ([#3929](/roundcube/roundcubemail/issues/3929))
 * Replace data URIs of images (pasted in HTML editor) with inline attachments ([#3795](/roundcube/roundcubemail/issues/3795))
 * Remove (too big) min-width on mail screen
 * Added template object 'frame'
 * Add option to enable HTML editor on forwarding ([#3807](/roundcube/roundcubemail/issues/3807))
 * Add option to not include original message on reply, rename option top_posting to reply_mode ([#1615](/roundcube/roundcubemail/issues/1615))
 * Added session_path config option and unified cookies settings in javascript
 * Added "Undeleted" option to messages list filter
 * Rewritten test scripts for PHPUnit
 * Add new DB abstraction layer based on PHP PDO, supporting SQLite3 ([#3668](/roundcube/roundcubemail/issues/3668))
 * Removed PEAR::MDB2 package
 * Removed users.alias column, added option ('user_aliases')
  to use email address from identities as username ([#3851](/roundcube/roundcubemail/issues/3851))
 * Removed redundant cache.cache_id column ([#3817](/roundcube/roundcubemail/issues/3817))
 * Fix order of attachments in sent mail ([#3740](/roundcube/roundcubemail/issues/3740))
 * Fix Shift + delete button does not permanently delete messages ([#3598](/roundcube/roundcubemail/issues/3598))
 * Add Content-Length for attachments where possible ([#1880](/roundcube/roundcubemail/issues/1880))
 * Fix attachment sizes in message print page and attachment preview page ([#3805](/roundcube/roundcubemail/issues/3805))
 * Add mail attachments using drag & drop on HTML5 enabled browsers
 * Add workaround for invalid BODYSTRUCTURE response - parse message with Mail_mimeDecode package ([#1966](/roundcube/roundcubemail/issues/1966))
 * Display Tiff as Jpeg in browsers without Tiff support ([#3757](/roundcube/roundcubemail/issues/3757))
 * Don't display Pdf/Tiff/Flash attachments inline without browser support ([#3757](/roundcube/roundcubemail/issues/3757), [#3394](/roundcube/roundcubemail/issues/3394))
 * Add is_escaped attribute for html_select and html_textarea ([#3782](/roundcube/roundcubemail/issues/3782))
 * Fix issue where draft auto-save wasn't executed after some inactivity time
 * Add vCard import from multiple files at once ([#3458](/roundcube/roundcubemail/issues/3458))
 * Roundcube Framework:
    * Add possibility to replace IMAP driver with custom class
    * Add IMAP auto-connection feature, improving performance with caching enabled
    * Replace imap_init hook with storage_init (with additional 'driver' argument)
    * Improved performance by caching IMAP server's capabilities in session
    * Unified global functions naming (rcube_ prefix)
    * Better classes separation
    * Framework files moved to lib/Roundcube

## Release 0.8.6

* Fix security issue in save-pref command

## Release 0.8.5

 * Fix #countcontrols issue in IE<=8 when text is very long ([#4060](/roundcube/roundcubemail/issues/4060))
 * Fix unwanted horizontal scrollbar in message preview header ([#4044](/roundcube/roundcubemail/issues/4044))
 * Add workaround for IE<=8 bug where Content-Disposition:inline was ignored ([#4028](/roundcube/roundcubemail/issues/4028))
 * Fix XSS vulnerability in vbscript: and data:text links handling ([#4033](/roundcube/roundcubemail/issues/4033))
 * Fix absolute positioning in HTML messages ([#4007](/roundcube/roundcubemail/issues/4007))
 * Fix keybord events on messages list in opera browser ([#4011](/roundcube/roundcubemail/issues/4011))
 * Fix cache (in)validation after setting \Deleted flag
 * Fix selection of collapsed thread rows ([#3978](/roundcube/roundcubemail/issues/3978))
 * Fix wrapping of quoted text with format=flowed ([#3561](/roundcube/roundcubemail/issues/3561))

## Release 0.8.4

 * Fix XSS vulnerability in handling of text/enriched messages ([#4000](/roundcube/roundcubemail/issues/4000))
 * Fix handling of 'media' attribute on linked css ([#3989](/roundcube/roundcubemail/issues/3989))
 * Fix regression where unintentional page reload was done after request abort ([#3999](/roundcube/roundcubemail/issues/3999))
 * Fix excessive LFs at the end of composed message with top_posting=true ([#3995](/roundcube/roundcubemail/issues/3995))
 * Fix bug where leading blanks were stripped from quoted lines ([#3994](/roundcube/roundcubemail/issues/3994))

## Release 0.8.3

 * Fix AREA links handling ([#3992](/roundcube/roundcubemail/issues/3992))
 * Fix possible HTTP DoS on error in keep-alive requests ([#3983](/roundcube/roundcubemail/issues/3983))
 * Fix compatybility with MDB2 2.5.0b4 ([#3982](/roundcube/roundcubemail/issues/3982))
 * Fix a bug where saving a message in INBOX wasn't possible
 * Fix HTML part detection in messages with attachments ([#3976](/roundcube/roundcubemail/issues/3976))
 * Fix bug where wrong words were highlighted on spell-before-send check
 * Fix scrolling quirk in email preview frame using Opera 12 ([#3973](/roundcube/roundcubemail/issues/3973))
 * Fix displaying of multipart/alternative messages with empty parts ([#3961](/roundcube/roundcubemail/issues/3961))
 * Fix Warning: htmlspecialchars(): charset `RCMAIL_CHARSET' not supported warning in Installer ([#3958](/roundcube/roundcubemail/issues/3958))
 * Fix threaded list sorting on PHP < 5.2.9 ([#3960](/roundcube/roundcubemail/issues/3960))

## Release 0.8.2

 * Fix XSS vulnerability from HTTP User-Agent header ([#3954](/roundcube/roundcubemail/issues/3954))
 * Force fonts in compose fields to be all the same ([#3926](/roundcube/roundcubemail/issues/3926))
 * Add full headers view in message preview window ([#3823](/roundcube/roundcubemail/issues/3823))
 * Fix message display page issues ([#3856](/roundcube/roundcubemail/issues/3856), [#3895](/roundcube/roundcubemail/issues/3895))
 * Fix handling vCard entries with TEL;TYPE=CELL ([#3949](/roundcube/roundcubemail/issues/3949))
 * Fix error where session wasn't updated after folder rename/delete ([#3928](/roundcube/roundcubemail/issues/3928))
 * Fix PLAIN authentication for some IMAP servers ([#3916](/roundcube/roundcubemail/issues/3916))
 * Fix encoding vCard file when contains PHOTO;ENCODING=b ([#3922](/roundcube/roundcubemail/issues/3922))
 * Fix focus issue in IE when selecting message row ([#3881](/roundcube/roundcubemail/issues/3881))
 * Fix displaying all headers when they contain malformed characters ([#3911](/roundcube/roundcubemail/issues/3911))
 * Fix decoding of HTML messages with UTF-16 charset specified ([#3902](/roundcube/roundcubemail/issues/3902))
 * Fix quota capability detection so it can be overwritten by a plugin ([#3903](/roundcube/roundcubemail/issues/3903))
 * Fix identity selection on reply ([#3516](/roundcube/roundcubemail/issues/3516))
 * Fix Larry's messages list filter in IE ([#3890](/roundcube/roundcubemail/issues/3890))
 * Fix more IE issues by disabling Compat. mode with X-UA-Compatible meta tag ([#3886](/roundcube/roundcubemail/issues/3886))
 * Fix setting locales under Solaris - use additional .UTF-8 suffix ([#3887](/roundcube/roundcubemail/issues/3887))
 * Fix email address validation for addresses with IP address in domain part
 * Fix Larry skin issues in IE7 compat. mode ([#3879](/roundcube/roundcubemail/issues/3879))
 * Fix so subscribed non-existing/non-accessible shared folder can be unsubscribed

## Release 0.8.1

 * Fix bug where domain name was converted to lower-case even with login_lc=false ([#3859](/roundcube/roundcubemail/issues/3859))
 * Fix lower-casing email address on replies ([#3863](/roundcube/roundcubemail/issues/3863))
 * Fix line separator in exported messages ([#3866](/roundcube/roundcubemail/issues/3866))
 * Fix XSS issue where plain signatures wasn't secured in HTML mode ([#3875](/roundcube/roundcubemail/issues/3875))
 * Fix XSS issue where href="javascript:" wasn't secured ([#3875](/roundcube/roundcubemail/issues/3875))
 * Fix impossible to create message with empty plain text part ([#3873](/roundcube/roundcubemail/issues/3873))
 * Fix stripped apostrophes when replying in plain text to HTML message ([#3869](/roundcube/roundcubemail/issues/3869))
 * Fix inactive Save search option after advanced search ([#3870](/roundcube/roundcubemail/issues/3870))
 * Fix Remove from group option is active for contact search result ([#3871](/roundcube/roundcubemail/issues/3871))
 * Disable autocapitalization in login form on iPad/iPhone ([#3872](/roundcube/roundcubemail/issues/3872))
 * Fix focus on the list when list row is clicked ([#3865](/roundcube/roundcubemail/issues/3865))
 * Added separate From and To columns apart from smart From/To column ([#2970](/roundcube/roundcubemail/issues/2970))
 * Fix fallback to Larry skin when configured skin isn't available ([#3857](/roundcube/roundcubemail/issues/3857))
 * Fix (workaround) delete operations with some versions of memcache ([#3858](/roundcube/roundcubemail/issues/3858))
 * Fix (disable) request validation for spell and spell_html actions

## Release 0.8.0

 * Renamed old default skin to 'classic'. Larry is the new default skin.
 * Support connections to memcached socket file ([#3848](/roundcube/roundcubemail/issues/3848))
 * Enable TinyMCE inlinepopups plugin
 * Update to TinyMCE 3.5.6
 * Correctly escape localized labels in javascript variable ([#3842](/roundcube/roundcubemail/issues/3842))
 * Update Net_SMTP/Auth_SASL packages to fix Digest-MD5/Cram-MD5 authentication ([#3846](/roundcube/roundcubemail/issues/3846))
 * Don't add attachments content into reply/forward/draft message body ([#3837](/roundcube/roundcubemail/issues/3837))
 * Fix 'no connection' errors on page unloads ([#3832](/roundcube/roundcubemail/issues/3832))
 * Plugin API: Add 'unauthenticated' hook ([#3545](/roundcube/roundcubemail/issues/3545))
 * Show explicit error message when provided hostname is invalid ([#3834](/roundcube/roundcubemail/issues/3834))
 * Fix wrong compose screen elements focus in IE9 ([#3826](/roundcube/roundcubemail/issues/3826))
 * Fix fatal error when date.timezone isn't set ([#3831](/roundcube/roundcubemail/issues/3831))
 * Update to TinyMCE 3.5.4.1
 * Better icons with distinct shapes for priority columns ([#3706](/roundcube/roundcubemail/issues/3706))
 * Show dedicated icon for multipart/report messages ([#3813](/roundcube/roundcubemail/issues/3813))
 * Properly hide text of icon links/buttons ([#3820](/roundcube/roundcubemail/issues/3820))
 * Fix handling of unitless CSS size values in HTML message ([#3821](/roundcube/roundcubemail/issues/3821))
 * Fix removing contact photo using LDAP addressbook ([#3737](/roundcube/roundcubemail/issues/3737))
 * Fix storing X-ANNIVERSARY date in vCard format ([#3816](/roundcube/roundcubemail/issues/3816))
 * Update to Mail_Mime-1.8.5 ([#3810](/roundcube/roundcubemail/issues/3810))
 * Fix XSS vulnerability in message subject handling using Larry skin ([#3809](/roundcube/roundcubemail/issues/3809))
 * Fix handling of links with various URI schemes e.g. "skype:" ([#3521](/roundcube/roundcubemail/issues/3521))
 * Fix handling of links inside PRE elements on html to text conversion
 * Fix indexing of links on html to text conversion
 * Decode header value in rcube_mime::get() by default ([#3803](/roundcube/roundcubemail/issues/3803))
 * Fix errors with enabled PHP magic_quotes_sybase option ([#3798](/roundcube/roundcubemail/issues/3798))
 * Fix SQL query for contacts listing on MS SQL Server ([#3797](/roundcube/roundcubemail/issues/3797))
 * Fix window.resize handler on IE8 and Opera ([#3758](/roundcube/roundcubemail/issues/3758))
 * Don't let error message popups cover the login form ([#3794](/roundcube/roundcubemail/issues/3794))
 * Don't show errors when moving contacts into groups they are already in ([#3788](/roundcube/roundcubemail/issues/3788))
 * Make folders with unread messages in subfolders bold again ([#2892](/roundcube/roundcubemail/issues/2892))
 * Abbreviate long attachment file names with ellipsis ([#3793](/roundcube/roundcubemail/issues/3793))
 * Fix html2text conversion of strong|b|a|th|h tags when used in upper case
 * Add listcontrols template container in Larry skin ([#3792](/roundcube/roundcubemail/issues/3792))
 * Fix host autoselection when default_host is an array ([#3790](/roundcube/roundcubemail/issues/3790))
 * Move messages forwarding mode setting into Preferences
 * Fix HTML entities handling in HTML editor ([#3780](/roundcube/roundcubemail/issues/3780))
 * Fix listing shared folders on Courier IMAP ([#3767](/roundcube/roundcubemail/issues/3767))