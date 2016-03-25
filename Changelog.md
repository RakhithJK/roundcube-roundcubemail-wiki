# CHANGELOG

## RELEASE 1.2-beta

 * Update TinyMCE to version 4.2
 * Remove backward compatibility "layer" of bc.php (#1490534)
 * Add possibility to define date format in write operations for ldap attributes (#1488741)
 * Display attachment size in compose (#1484774)
 * Added possibility to drag-n-drop attachments from mail preview to compose window
 * Implemented mail messages searching with predefined date interval
 * PGP encryption support via Mailvelope integration
 * PGP encryption support via Enigma plugin
 * PHP7 compatibility fixes (#1490416)
 * Security: Added brute-force attack prevention via login rate limit (#1490566)
 * Security: Added options to validate username/password on logon (#1490500)
 * Security: Improve randomness of security tokens (#1490529)
 * Security: Use random security tokens instead of hashes based on encryption key (#1490404)
 * Security: Improved encrypt/decrypt methods with option to choose the cipher_method (#1489719)
 * Make optional adding of standard signature separator - sig_separator (#1487768)
 * Optimize folder_size() on Cyrus IMAP by using special folder annotation (#1490514)
 * Make optional hidding of folders with name starting with a dot - imap_skip_hidden_folders (#1490468)
 * Add option to enable HTML editor always, except when replying to plain text messages (#1489365)
 * Emoticons: Added option to switch on/off emoticons in compose editor (#1485732)
 * Emoticons: Added option to switch on/off emoticons in plain text messages
 * Emoticons: All emoticons-related functionality is handled by the plugin now
 * Installer: Add button to save generated config file in system temp directory (#1488149)
 * Remove common subject prefixes Re:, Re[x]:, Re-x: on reply (#1490497)
 * Added GSSAPI/Kerberos authentication plugin - krb_authentication
 * Password: Allow temporarily disabling the plugin functionality with a notice
 * Require Mbstring and OpenSSL extensions (#1490415)
 * Add --config and --type options to moduserprefs.sh script (#1490051)
 * Implemented memcache_debug and apc_debug options
 * Installer: Remove system() function use (#1490139)
 * Password plugin: Added 'kpasswd' driver by Peter Allgeyer
 * Add initdb.sh to create database from initial.sql script with prefix support (#1490188)
 * Plugin API: Added disabled_plugins an disabled_buttons options in html_editor hook
 * Plugin API: Added html2text hook
 * Plugin API: Added message_part_body hook
 * Plugin API: Added message_ready hook
 * Plugin API: Add special onload() method to execute plugin actions before startup (session and GUI initialization)
 * Implemented UI element to jump to specified page of the messages list (#1485235)
 * Fix searching of contacts to allow remote images for known senders (#1490504)
 * Fix bug where clicking date column with 'arrival' sorting would switch to sorting by 'date' (#1490126)
 * Fix bug where message content could overlap attachments list in Larry skin (#1490479)
 * Fix so microseconds macro (u) in log_date_format works (#1490446)
 * Fix so unrecognized TNEF attachments are displayed on the list of attachments (#1490351)

## RELEASE 1.1.4

 * Add workaround for https://bugs.php.net/bug.php?id=70757 (#1490582)
 * Fix duplicate messages in list and wrong count after delete (#1490572)
 * Fix so Installer requires PHP5
 * Make brute force attacks harder by re-generating security token on every failed login (#1490549)
 * Slow down brute-force attacks by waiting for a second after failed login (#1490549)
 * Fix .htaccess rewrite rules to not block .well-known URIs (#1490615)
 * Fix mail view scaling on iOS (#1490551)
 * Fix so database_attachments::cleanup() does not remove attachments from other sessions (#1490542)
 * Fix responses list update issue after response name change (#1490555)
 * Fix bug where message preview was unintentionally reset on check-recent action (#1490563)
 * Fix bug where HTML messages with invalid/excessive css styles couldn't be displayed (#1490539)
 * Fix redundant blank lines when using HTML and top posting (#1490576)
 * Fix redundant blank lines on start of text after html to text conversion (#1490577)
 * Fix HTML sanitizer to skip <!-- node type X --> in output (#1490583)
 * Fix invalid LDAP query in ACL user autocompletion (#1490591)
 * Fix regression in displaying contents of message/rfc822 parts (#1490606)
 * Fix handling of message/rfc822 attachments on replies and forwards (#1490607)
 * Fix PDF support detection in Firefox > 19 (#1490610)
 * Fix path traversal vulnerability (CWE-22) in setting a skin (#1490620)
 * Fix so drag-n-drop of text (e.g. recipient addresses) on compose page actually works (#1490619)

## RELEASE 1.1.3

 * Fix closing of nested menus (#1490443)
 * Fix so E_DEPRECATED errors from PEAR libs are ignored by error_reporting change (#1490281)
 * Fix compatibility with PHP 5.3 in rcube_ldap class (#1490424)
 * Get rid of Mail_mimeDecode package dependency (#1490416)
 * Fix "Importing..." message does not hide on error (#1490422)
 * Fix SQL error on logout when using session_storage=php (#1490421)
 * Update to jQuery 2.1.4 (#1490406)
 * Fix Compose action in addressbook for results from multiple addressbooks (#1490413)
 * Fix bug where some messages in multi-folder search couldn't be viewed/printed/downloaded (#1490426)
 * Fix unintentional messages list page change on page switch in compose addressbook (#1490427)
 * Fix race-condition in saving user preferences and loading plugin config (#1490431)
 * Fix so plain text signature field uses monospace font (#1490435)
 * Fix so links with href == content aren't added to links list on html to text conversion (#1490434)
 * Fix handling of non-break spaces in html to text conversion (#1490436)
 * Fix self-reply detection issues (#1490439)
 * Fix multi-folder search result sorting by arrival date (#1490450)
 * Fix so *-request@ addresses in Sender: header are also ignored on reply-all (#1490452)
 * Update to TinyMCE 4.1.10 (#1490405)
 * Fix draft removal after a message is sent and storing sent message is disabled (#1490467)
 * Fix so imap folder attribute comparisons are case-insensitive (#1490466)
 * Fix bug where new messages weren't added to the list in search mode
 * Fix wrong positioning of message list header on page scroll in Webkit browsers (#1490035)
 * Fix some javascript errors in rare situations (#1490441)
 * Fix error when using back button after sending an email (#1490009)
 * Fix removing signature when switching to identity with an empty sig in HTML mode (#1490470)
 * Disable links list generation on html-to-text conversion of identities or composed message (#1490437)
 * Fix "washing" of style elements wrapped into many lines
 * Fix so input field (e.g. search box) does not loose focus on list load (#1490455)
 * Fix minor XSS issue in drag-n-drop file uploads (#1490530)

## RELEASE 1.1.2

 * Add new plugin hook 'identity_create_after' providing the ID of the inserted identity (#1490358)
 * Add option to place signature at bottom of the quoted text even in top-posting mode [sig_below]
 * Fix handling of %-encoded entities in mailto: URLs (#1490346)
 * Fix zipped messages downloads after selecting all messages in a folder (#1490339)
 * Fix vpopmaild driver of password plugin
 * Fix PHP warning: Non-static method PEAR::setErrorHandling() should not be called statically (#1490343)
 * Fix tables listing routine on mysql and postgres so it skips system or other database tables and views (#1490337)
 * Fix message list header in classic skin on window resize in Internet Explorer (#1490213)
 * Fix so text/calendar parts are listed as attachments even if not marked as such (#1490325)
 * Fix lack of signature separator for plain text signatures in html mode (#1490352)
 * Fix font artifact in Google Chrome on Windows (#1490353)
 * Fix bug where forced extwin page reload could exit from the extwin mode (#1490350)
 * Fix bug where some unrelated attachments in multipart/related message were not listed (#1490355)
 * Fix mouseup event handling when dragging a list record (#1490359)
 * Fix bug where preview_pane setting wasn't always saved into user preferences (#1490362)
 * Fix bug where messages count was not updated after message move/delete with skip_deleted=false (#1490372)
 * Fix security issue in contact photo handling (#1490379)
 * Fix possible memcache/apc cache data consistency issues (#1490390)
 * Fix bug where imap_conn_options were ignored in IMAP connection test (#1490392)
 * Fix bug where some files could have "executable" extension when stored in temp folder (#1490377)
 * Fix attached file path unsetting in database_attachments plugin (#1490393)
 * Fix issues when using moduserprefs.sh without --user argument (#1490399)
 * Fix potential info disclosure issue by protecting directory access (#1490378)
 * Fix blank image in html_signature when saving identity changes (#1490412)
 * Installer: Use openssl_random_pseudo_bytes() (if available) to generate des_key (#1490402)
 * Fix XSS vulnerability in _mbox argument handling (#1490417)

## RELEASE 1.1.1

 * ACL: Allow other plugins to adjust the list of permissions and groups to edit
 * Add possibility to print contact information (of a single contact)
 * Add possibility to configure max_allowed_packet value for all database engines (#1490283)
 * Improved handling of storage errors after message is sent
 * Update to TinyMCE 4.1.9
 * Unified request* event arguments handling, added support for _unlock and _action parameters
 * Security: Generate random hash for the per-user local storage prefix (#1490279)
 * Fix refreshing of drafts list when sending a message which was saved in meantime (#1490238)
 * Fix saving/sending emoticon images when assets_dir is set
 * Fix PHP fatal error when visiting Vacation interface and there's no sieve script yet (#1490292)
 * Fix setting max packet size for DB caches and check packet size also in shared cache
 * Fix needless security warning on BMP attachments display (#1490282)
 * Fix handling of some improper constructs in format=flowed text as per the RFC3676[4.5] (#1490284)
 * Fix performance of rcube_db_mysql::get_variable()
 * Fix missing or not up-to-date CATEGORIES entry in vCard export (#1490277)
 * Fix fatal errors on systems without mbstring extension or mb_regex_encoding() function (#1490280)
 * Fix cursor position on reply below the quote in HTML mode (#1490263)
 * Fix so "over quota" errors are displayed also in message compose page
 * Fix duplicate entries supression in autocomplete result (#1490290)
 * Fix "Non-static method PEAR::isError() should not be called statically" errors (#1490281)
 * Fix parsing invalid HTML messages with BOM after <!DOCTYPE> (#1490291)
 * Fix duplicate entry on timezones list in rcube_config::timezone_name_from_abbr() (#1490293)
 * Fix so localized folder name is displayed in multi-folder search result (#1490243)
 * Fix javascript error after creating a folder which is a subfolder of another one (#1490297)
 * Fix bug where subject of sent/saved message was removed if mbstring wasn't installed (#1490295)
 * Fix missing vcard_attachment icon on messages list (#1490303)
 * Fix storing signatures with big images in MySQL database (#1490306)
 * Fix Opera browser detection in javascript (#1490307)
 * Fix so search filter, scope and fields are reset on folder change
 * Fix rows count when messages search fails (#1490266)
 * Fix bug where spellchecking in HTML editor do not work after switching editor type more than once (#1490311)
 * Fix bug where TinyMCE area height was too small on slow network connection (#1490310)
 * Fix backtick character handling in sql queries (#1490312)
 * Fix redirect URL for attachments loaded in an iframe when behind a proxy (#1490191)
 * Fix menu container references to point to the actual `<ul>` element (#1490313)
 * Fix javascripts errors in IE8 - lack of Event.which, focusing a hidden element (#1490318)

## RELEASE 1.1.0

 * Make SMTP error log more verbose - include server response and error code
 * Fix download options menu (added by zipdownload plugin) in classic skin (#1490228)
 * Fix blocked.gif image usage with assets_dir set
 * Fix bug where max_group_members was ignored when adding a new contact (#1490214)
 * Hide MDN and DSN options in compose if disabled by admin (#1490221)
 * Fix checks based on window.ActiveXObject in IE > 10
 * Fix XSS issue in style attribute handling (#1490227)
 * Fix bug where Drafts list wasn't updated on draft-save action in new window (#1490225)
 * Fix so "set as default" option is hidden if identities_level > 1 (#1490226)
 * Fix bug where search was reset after returning from compose visited for reply
 * Fix javascript error in "IE 8.0/Tablet PC" browser (#1490210)
 * Fix bug where Reply-To address was ignored on reply to messages sent by self (#1490233)
 * Fix bug where empty fieldmap config entries caused empty results of ldap search (#1490229)
 * Fix bug where drafts list wasn't refreshed after draft message was sent from another window (#1490238)
 * Fix keyboard navigation and css in datepicker widget across many Firefox versions
 * Fix false warning when opening attached text/plain files (#1490241)
 * Fix bug where signature could have been inserted twice after plain-to-html switch (#1490239)
 * Fix security issue in DBMail driver of password plugin (#1490261)
 * Enable FollowSymLinks option in .htaccess file which is required by rewrite rules (#1490255)
 * Fix so JSON.parse() errors on localStorage items are ignored (#1490249)

## RELEASE 1.1-RC

 * Update jQuery to version 2.1.3
 * Improve system security by using optional special URL with security token - use_secure_urls
 * Allow to define separate server/path for image/js/css files - assets_url/assets_dir
 * Sync vendor folder if exists in source package (#1490145)
 * Avoid useless reloading list when resetting search with active filter (#1490057)
 * Fix invalid folder selection if clicked while busy (#1490158)
 * Fix import of multiple contact email addresses from Outlook-csv format (#1490169)
 * Fix drag-n-drop to folders expanded while dragging (#1490157)
 * Fix import of multiple contact groups from Google-csv format (#1490159)
 * Fix import of contacts with multiple email addresses from Google-csv format (#1490178)
 * Fix bugs where CSRF attacks were still possible on some requests
 * Fix some rcube_utils::anytodatetime() corner cases with timezone mismatches (#1490163)
 * Improve move-to and contact-export button in classic skin (#1490166)
 * Fix wrong icon for download button in classic skin
 * Fix bug where sent message was saved in Sent folder even if disabled by user (#1490208)

## RELEASE 1.1-beta

 * Fix skin path handling in plugin context (#1488967)
 * Prevent memory exhaustion on image resizing with GD on Windows (#1489937)
 * Add plugin hook for database table name lookups as requested in #1489837
 * Added Oracle database support
 * Support contacts import in GMail CSV format
 * Added namespace filter in Folder Manager
 * Added folder searching in Folder Manager
 * Fix restoring draft messages from localStorage if editor mode differs (#1490016)
 * Added config option/user preference to disable saving messages in localStorage (#1489979)
 * Added config option 'imap_log_session' to enable Roundcube <-> IMAP session ID logging
 * Added config option 'log_session_id' to control the length of the session identifier in logs
 * Implemented 'storage_connected' API hook after successful IMAP login (#1490025)
 * Integrate Net_LDAP3 and rcube_ldap_generic classes
 * Add option (disabled_actions) to disable UI elements/actions (#1489638)
 * Support password encryption using openssl extension (#1489989)
 * Create/rename groups in UI dialogs (#1489951)
 * Added 'contact_search_name' option to define autocompletion entry format
 * Display quota information for current folder not INBOX only (#1487993)
 * Support images in HTML signatures (#1488676)
 * Display full quota information in popup (#1485769, #1486604)
 * Mail compose: Selecting contact inserts recipient to previously focused input - to/cc/bcc accordingly (#1489684)
 * Close "no subject" prompt with Enter key (#1489580)
 * Password: Add option to force new users to change their password (#1486884)
 * Improve support for screen readers and assistive technology using WCAG 2.0 and WAI ARIA standards
 * Enable basic keyboard navigation throughout the UI (#1487845)
 * Select/scroll to previously selected message when returning from message page (#1489023)
 * Display a warning if popup window was blocked (#1489618)
 * Remove (was: ...) from message subject on reply (#1489375)
 * Update to TinyMCE 4.1 (#1489057)
 * Enable autolink plugin in TinyMCE (#1488845)
 * Support image operations with Imagick extension (#1489734)
 * Support upload progress with session.upload_progress and PECL uploadprogress module (#1488702)
 * Make identity name field optional (#1489510)
 * Utility script to remove user records from the local database
 * Plugin API: Added message_saved hook (#1489752)
 * Plugin API: Added imap_search_before hook
 * Support messages import from zip archives
 * Zipdownload: Added mbox format support (#1486069)
 * Drop support for IE6, move IE7/IE8 support to legacy_browser plugin
 * Update to jQuery-2.1.1
 * Search across multiple folders (#1485234)
 * Improve UI integration of ACL settings
 * Drop support for PHP < 5.3.7
 * Set In-Reply-To and References for forwarded messages (#1489593)
 * Removed redundant default_folders config option (#1489737)
 * Implemented IMAP SPECIAL-USE extension support [RFC6154] (#1487830)
 * Optimize some framed pages content for better performance (#1489792)
 * Improve text messages display and conversion to HTML (#1488937)
 * Don't remove links when html signature is converted to text (#1489621)
 * Fix page title when using search filter (#1490023)
 * Fix mbox files import
 * Fix some character sets detection (#1490135)
 * Fix so attachment charset is set in headers of forward/draft message (#1490109)
 * Fix bug where wrong charset could be used for text attachment preview page (#1490106)
 * Fix setting flags on servers with no PERMANENTFLAGS response (#1490087)
 * Fix regression in SHAA password generation in ldap driver of password plugin (#1490094)
 * Fix displaying of HTML messages with absolutely positioned elements in Larry skin (#1490103)
 * Fix font style display issue in HTML messages with styled <span> elements (#1490101)
 * Fix download of attachments that are part of TNEF message (#1490091)
 * Fix handling of uuencoded messages if messages_cache is enabled (#1490108)
 * Fix handling of base64-encoded attachments with extra spaces (#1490111)
 * Fix handling of UNKNOWN-CTE response, try do decode content client-side (#1490046)
 * Fix bug where creating subfolders in shared folders wasn't possible without ACL extension (#1490113)
 * Fix reply scrolling issue with text mode and start message below the quote (#1490114)
 * Fix possible issues in skin/skin_path config handling (#1490125)

## RELEASE 1.0.6

 * Make SMTP error log more verbose - include server response and error code
 * Fix rows count when messages search fails (#1490266)
 * Fix security issue in DBMail driver of password plugin (#1490261)
 * Fix handling of some improper constructs in format=flowed text as per the RFC3676[4.5] (#1490284)
 * Fix missing or not up-to-date CATEGORIES entry in vCard export (#1490277)
 * Fix duplicate entry on timezones list in rcube_config::timezone_name_from_abbr() (#1490293)
 * Fix handling of %-encoded entities in mailto: URLs (#1490346)
 * Fix bug where messages count was not updated after message move/delete with skip_deleted=false (#1490372)
 * Fix security issue in contact photo handling (#1490379)
 * Fix bug where database_attachments_cache setting was not working
 * Fix attached file path unsetting in database_attachments plugin (#1490393)
 * Fix issues when using moduserprefs.sh without --user argument (#1490399)

## RELEASE 1.0.5

 * Fix bug where some valid text in a message was handled as uuencoded attachment
 * Fix wrong icon for download button in classic skin
 * Fix bug where sent message was saved in Sent folder even if disabled by user (#1490208)
 * Fix checks based on window.ActiveXObject in IE > 10
 * Fix XSS issue in style attribute handling (#1490227)
 * Fix bug where Drafts list wasn't updated on draft-save action in new window (#1490225)
 * Fix so "set as default" option is hidden if identities_level > 1 (#1490226)
 * Fix bug where search was reset after returning from compose visited for reply
 * Fix javascript error in "IE 8.0/Tablet PC" browser (#1490210)
 * Fix bug where empty fieldmap config entries caused empty results of ldap search (#1490229)

## RELEASE 1.0.4

 * Disable TinyMCE contextmenu plugin as there are more cons than pros in using it (#1490118)
 * Fix bug where show_real_foldernames setting wasn't honored on compose page (#1490153)
 * Fix issue where Archive folder wasn't protected in Folder Manager (#1490154)
 * Fix compatibility with PHP 5.2. in rcube_imap_generic (#1490115)
 * Fix setting flags on servers with no PERMANENTFLAGS response (#1490087)
 * Fix regression in SHAA password generation in ldap driver of password plugin (#1490094)
 * Fix displaying of HTML messages with absolutely positioned elements in Larry skin (#1490103)
 * Fix font style display issue in HTML messages with styled <span> elements (#1490101)
 * Fix download of attachments that are part of TNEF message (#1490091)
 * Fix handling of uuencoded messages if messages_cache is enabled (#1490108)
 * Fix handling of base64-encoded attachments with extra spaces (#1490111)
 * Fix handling of UNKNOWN-CTE response, try do decode content client-side (#1490046)
 * Fix bug where creating subfolders in shared folders wasn't possible without ACL extension (#1490113)
 * Fix reply scrolling issue with text mode and start message below the quote (#1490114)
 * Fix possible issues in skin/skin_path config handling (#1490125)
 * Fix lack of delimiter for recipient addresses in smtp_log (#1490150)
 * Fix generation of Blowfish-based password hashes (#1490184)
 * Fix bugs where CSRF attacks were still possible on some requests

## RELEASE 1.0.3

 * Fix insert-signature command in external compose window if opened from inline compose screen (#1490074)
 * Initialize HTML editor before restoring a message from localStorage (#1490016)
 * Add 'sig_max_lines' config option to default config file (#1490071)
 * Add option to specify IMAP connection socket parameters - imap_conn_options (#1489948)
 * Add option to set default message list mode - default_list_mode (#1487312)
 * Enable contextmenu plugin for TinyMCE editor (#1487014)
 * Fix some mime-type to extension mapping checks in Installer (#1489983)
 * Fix errors when using localStorage in Safari's private browsing mode (#1489996)
 * Fix bug where $Forwarded flag was being set even if server didn't support it (#1490000)
 * Fix various iCloud vCard issues, added fallback for external photos (#1489993)
 * Fix invalid Content-Type header when send_format_flowed=false (#1489992)
 * Fix errors when adding/updating contacts in active search (#1490015)
 * Fix incorrect thumbnail rotation with GD and exif orientation data (#1490029)
 * Fix contacts list update after adding/deleting/moving a contact (#1490028, #1490033)
 * Fix handling of email addresses with quoted domain part (#1490040)
 * Fix comm_path update on task switch (#1490041)
 * Fix error in MSSQL update script 2013061000.sql (#1490061)
 * Fix validation of email addresses with IDNA domains (#1490067)

## RELEASE 1.0.2

 * Fix storing unsaved drafts in localStorage (#1489818)
 * Fix redundant horizontal scrollbar in HTML editor (#1489950)
 * Fix PHP error in Preferences when default_folders was in dont_override (#1489940)
 * Add configurable LDAP_OPT_DEREF option (#1489864)
 * Fix unintentional draft autosave request if autosave is disabled (#1489882)
 * Fix malformed References: header in send/saved mail (#1489891)
 * Fix handling unicode characters in links (#1489898)
 * Fix incorrect handling of HTML comments in messages sanitization code (#1489904)
 * Fix so current page is reset on list-mode change (#1489907)
 * Fix so responses menu hides on click in classic skin (#1489915)
 * Fix unintentional line-height style modification in HTML messages (#1489917)
 * Fix broken normalize_string(), add support for ISO-8859-2 (#1489918)
 * Support csv contacts import in German localization (#1489920)
 * Fix so message list and counters are updated when a message is opened in new window (#1489919)
 * Fix malformed recipient name when composing a message by clicking on mailto link (#1489942)
 * Fix list reload after sending message in another window (#1489931)
 * Fix so address format errors are ignored when saving a draft (#1489954)
 * Fix incorrect label translation in return receipt (#1489963)
 * Fix security issue in delete-response action - allow only ajax request
 * Fix Delete button state after deleting identity/response (#1489972)
 * Fix bug where contacts with no email address were listed on compose addressbook (#1489970)
 * Fix images import from various vCard formats (#1489977)
 * Fix sorting messages by size on servers without SORT capability (#1489981)

## RELEASE 1.0.1

 * Support 'error' and 'body_file' return attribs in 'message_before_send' hook (#1489595)
 * Apply user-specific replacements to group's base_dn property (#1489779)
 * Fix missing email address when importing contacts from outlook csv (#1489830)
 * Fix bug where "With attachment" option in search filter wasn't selected after return from mail view (#1489774)
 * Fix "washing" of unicoded style attributes (#1489777)
 * Fix unintentional redirect from compose page in Webkit browsers (#1489789)
 * Fix messages index cache update under some conditions (e.g. proxy) (#1489756)
 * Fix lack of translation of special folders in some configurations (#1489799)
 * Fix XSS issue in plain text spellchecker (#1489806)
 * Fix invalid page title for some folders (1489804)
 * Fix redundant alert message on over-size uploads (#1489817)
 * Fix next message display after removing a message (#1489800)
 * Fix missing Mail-Followup-To header in sent mail (#1489829)
 * Fix error when spell-checking an empty text (#1489831)
 * Avoid popupmenus being closed when scrollbar is clicked (#1489832)
 * Add proxy_whitelist configuration option (#1489729)
 * Fix identities_level=4 handling in new_user_dialog plugin (#1489840)
 * Fix various db_prefix issues (#1489839)
 * Fix too small length of users.preferences column data type on MySQL
 * Fix redundant warning when switching from html to text in empty editor (#1489819)
 * Fix invalid host validation on login (#1489841)
 * Fix IMAP connection test in installer so it is aware of imap_auth_type (#1489746)

## RELEASE 1.0.0

 * Fix style of disabled protocol handler link on IE (#1489569)
 * Fix message import dialog when no file is selected (#1489685)
 * Fix opening compose screen in new window after saving as draft (#1489643)
 * Added toolbar button to move message in message view
 * Fix directories check in Installer on Windows (#1489576)
 * Fix issue when default_addressbook option is set to integer value (#1489407)
 * Fix Opera > 15 detection (#1489562)
 * Fix security issue in DomainFactory driver of Password plugin
 * Fix invalid X-Draft-Info on forwarded message draft (#1489587)
 * Fix regression in handling of 'attachments' result in message_compose hook (#1489627)
 * Fix issue where msgexport.sh printed the message to STDOUT instead of a file (#1489634)
 * Fix fatal error in database_attachments plugin under some conditions (#1489726)

## RELEASE 1.0-RC

 * Small CSS fix with message notice boxes in Larry skin (#1489497)
 * Include groups in contacts search on mail compose (#1489082)
 * Add mime-type mapping for .7z files (#1489512)
 * Invoke update scripts with php to circumvent execution restrictions (#1489322)
 * Fix drag & drop message/contact moving on touch device (#1489431)
 * Fix canned responses in HTML mode (#1489536)
 * Check/create default folders on every login not only the first (#1489423)
 * Update to jQuery-1.11.0 and jQuery-UI-1.9.2
 * Support SMTP socket context options via new config option 'smtp_conn_options'
 * Fix compatibility with PHP 5.2 in html.php file (#1489514)
 * Remove expand/collapse with plus/minus keys (on numeric keypad) (#1489513)
 * Fix issue where filesystem path was added to all-attachments (zip) file (#1489507)
 * Fix case-sensitivity of email addresses handling on compose (#1485499)
 * Don't alter Message-ID of a draft when sending (#1489409)
 * Fix issue where deprecated syntax for HTML lists was not handled properly (#1488768)
 * Display different icons when Trash folder is empty or full (#1485775)
 * Remember last position of more headers switch (#1488323)
 * Fix so message flags modified by another client are applied on the list on refresh (#1485186)
 * Fix broken text/* attachments when forwarding/editing a message (#1489426)
 * Improved minified files handling, added css minification (#1486988)
 * Fix handling of X-Forwarded-For header with multiple addresses (#1489481)
 * Fix border issue on folders list in classic skin (#1489473)
 * Implemented menu actions to copy/move messages, added folder-selector widget (#1484086)
 * Fix security rules in .htaccess preventing access to base URL without the ending slash (#1489477)
 * Fix regression where only first new folder was placed in correct place on the list (#1489472)
 * Fix issue where children of selected and collapsed thread were skipped on various actions (#1489457)
 * Fix issue where groups were not deleted when "Replace entire addressbook" option on contacts import was used (#1489420)
 * Fix unreliable mimetype tests in Installer (#1489453)
 * Fix performance of listing writeable folders (#1489451)

## RELEASE 1.0-beta

 * Fix handling of invalid closing tags in HTML messages (#1489446)
 * Set real content-type for file downloads (#1489439)
 * Update TinyMCE to version 3.5.10 (#1489442)
 * Fix keyboard navigation in list widgets (#1489392)
 * Allow plugins to grab the reference of opened windows (#1489413)
 * Larry skin: Improved status message display for better visibility (#1488974)
 * Fix Internet Explorer 11 detection (#1489434)
 * Fix date column width to fit the widest possible date format (#1489368)
 * Move certain user preference options to a collapsed "advanced" block (#1488829)
 * Add file type icons for Powerpoint and Open Office presentations (#1489225)
 * Fix operations on folders with trailing spaces in name (#1489419)
 * Improve identity selection based on From: header (#1489378)
 * Fix issue where mails with inline images of the same name contained only the first image multiple times (#1489406)
 * Use left/right arrow keys to collapse/expand thread and spacebar to select a row, change Ctrl key behavior (#1489392)
 * Fix an issue where using arrow keys to go up a list can result in selected message being under headers (#1489403)
 * Fix an issue where Home/End keys don't focus list row properly, don't scrollTo properly (#1489396)
 * Add an option to disable smart Reply-List behaviour - reply_all_mode (#1488734)
 * Fix an issue where pressing minus key on contacts list was hiding list records (#1489393)
 * Fix an issue where shift + arrow-up key wasn't selecting all messages in collapsed thread (#1489397)
 * Added icon for priority column in messages list header (#1489234)
 * New feature "Canned Responses" to save and recall boilerplate text snippets
 * Fix HTML part detection when encapsulated inside multipart/signed (#1489372)
 * Add spellchecker backend for the After the Deadline service
 * Replace markdown-style [1] link indexes in plain text email bodies
 * Improved mailto: link arguments handling (#1489363)
 * Use DOMDocument LIBXML_PARSEHUGE and LIBXML_COMPACT options if possible (#1489302)
 * Support HTTP_HOST, SERVER_NAME and SERVER_ADDR values in include_host_config feature
 * Make default font size for HTML messages configurable (request #118)
 * Fix XSS issue in addressbook group name field [CVE-2013-5646] (#1489333)
 * After message is sent refresh messages list of replied message folder (#1489249)
 * Add option force specified domain in user login - username_domain_forced (#1489264)
 * Add option to import Vcards with group assignments
 * Save groups membership in Vcard export (#1488509)
 * Workaround broken PHP function timezone_name_from_abbr (#1489261)
 * Make cached message size limit configurable - messages_cache_threshold (#1489317)
 * Log also failed logins to userlogins log
 * Add temp_dir_ttl configuration option (#1489304)
 * Allow setting INBOX as Sent folder (#1489219)
 * Fix replacement variables in user-specific base_dn in some LDAP requests (#1489279)
 * Fix image scaling issues when image has only one dimension smaller than the limit (#1489274)
 * Fix issue where uploaded photo was lost when contact form did not validate (#1489274)
 * Move identity selection based on non-standard headers into (new) identity_select plugin (#1488553)
 * Fix downloading binary files with (wrong) text/* content-type (#1489267)
 * Respect HTTP_X_FORWARDED_FOR and HTTP_X_REAL_IP variables for session IP check
 * Simplified configuration by merging it into one file + defaults (#1487311)
 * Make message list header stay on top when scrolling (#1295420)
 * Add support for 'enchant' spellcheck engine
 * Check filetype detection in installer and update script (#1489193)
 * Fix folder names truncation in Classic skin (#1489220)
 * Make possible to disable some (broken) IMAP extensions with imap_disable_caps option (#1489184)
 * Contacts drag-n-drop default action is to move contacts (#1488751)
 * Added possibility to choose to move or copy contacts from drag-n-drop menu (#1488751)
 * Fix Close link and remove About link on error pages (#1489109)
 * Improved/unified attachment preview screen, added print button
 * Fix lack of space between searchfiler and quicksearchbar in Larry skin (#1489158)
 * Cache LDAP's user_specific search and use vlv for better performance (#1489186)
 * LDAP: auto-detect and use VLV indices for all search operations
 * LDAP: additional group configuration options for  address books
 * LDAP: separated address book implementation from a generic LDAP wrapper class
 * Allow address books to browse a multi-level group hierarchy in the contacts list
 * Fix session issues when local and database time differs (#1486132)
 * Fix thread cache syncronization/validation (#1489028)
 * Added feature to import messages to the currently selected folder
 * Add option show_real_foldernames to disable localization of special folders
 * Fix database cache expunge issues (#1489149)
 * Fix date format issues on MS SQL Server (#1488918)
 * Add imap_cache_ttl option to configure TTL of imap_cache
 * Make LDAP cache engine configurable via ldap_cache and ldap_cache_ttl options
 * Fix "duplicate entry" errors on inserts to imap cache tables (#1489146)
 * Improved handling of Reply-To/Bcc addresses of identity in compose form (#1489016)
 * Added user preference to open all popups as standard windows
 * Implemented shared cache (rcube_cache_shared)
 * Change Reply-All button label/title when mailing list is detected (#1488938)
 * Fix SMTP connection using IPv6 address in smtp_server option (#1489024)
 * Added attachment_reminder plugin
 * Make PHP code eval() free, use create_function()
 * Add option to display email address together with a name in mail preview (#1488732)
 * Support CSV import from Atmail (#1489045)
 * Add db_prefix configuration option in place of db_table_*/db_sequence_* options
 * Make possible to use db_prefix for schema initialization in Installer (#1489067)
 * Fix updatedb.sh script so it recognizes also table prefix for external DDL files
 * Fix parsing invalid date string (#1489035)
 * Add "with attachment" option to messages list filter (#1485382)
 * Call resize handler in intervals to prevent lags and double onresize calls in Chrome (#1489005)
 * Add rel="noreferrer" for links in displayed messages (#1484686)
 * Add ability to toggle between HTML and text while viewing a message (#1486939)
 * Remove "HTML message" from attachments list while viewing a message in text mode (#1486939)
 * Support IMAP MOVE extension [RFC 6851]
 * Add attachment menu with Open and Download options (#1488975)
 * Display user-friendly message on IMAP "over quota" errors (#1484164)
 * Extended archive plugin with user-configurable options to store messages into subfolders
 * Fix export of selected contacts from search result (#1488905)
 * Feature to export only selected contacts from addressbook (by Phil Weir)

## RELEASE 0.9.5

 * Fix failing vCard import when email address field contains spaces (#1489386)
 * Fix default spell-check configuration after Google suspended their spell service
 * Fix vulnerability in handling _session argument of utils/save-prefs (#1489382)
 * Fix iframe onload for upload errors handling (#1489379)
 * Fix address matching in Return-Path header on identity selection (#1489374)
 * Fix text wrapping issue with long unwrappable lines (#1489371)
 * Fixed mispelling: occured -> occurred (#1489366)
 * Fixed issues where HTML comments inside style tag would hang Internet Explorer
 * Fix setting domain in virtualmin password driver (#1489332)
 * Hide Delivery Status Notification option when smtp_server is unset (#1489336)
 * Display full attachment name using title attribute when name is too long to display (#1489320)
 * Fix attachment icon issue when rare font/language is used (#1489326)
 * Fix expanded thread root message styling after refreshing messages list (#1489327)
 * Fix issue where From address was removed from Cc and Bcc fields when editing a draft (#1489319)
 * Fix error_reporting directive check (#1489323)
 * Fix de_DE localization of "About" label in Help plugin (#1489325)

## RELEASE 0.9.4

 * Make identities matching case insensitive (#1485480)
 * Fix issue where too big message data was stored in cache causing sql errors (#1489316)
 * Fix iframe scrollbars on webkit desktop browsers (#1489306)
 * Fix issue where legacy config was overriden by default config (#1489288)
 * Fix newmail_notifier issue where favicon wasn't changed back to default (#1489313)
 * Fix setting of Junk and NonJunk flags by markasjunk plugin (#1489285)
 * Fix lack of Reply-To address in header of forwarded message body (#1489298)
 * Fix bugs when invoking contact creation form when read-only addressbook is selected (#1489296)
 * Fix identity selection on reply (#1489291)
 * Fix so additional headers are added to all messages sent (#1489284)
 * Fix display issue after moving folder in Folder Manager (#1489293)
 * Fix handling of non-default date formats (#1489294)
 * Fix unquoted path in PREG expression on Windows (#1489290)
 * Fix Junk folder icon alignment when it's nested in inbox folder (#1489292)
 * Fix wrong close tag in /template/mail.html (#1489295)

## RELEASE 0.9.3

 * Optimized UI behavior for touch devices
 * Fix setting refresh_interval to "Never" in Preferences (#1489286)
 * Fix purge action in folder manager (#1489280)
 * Fix base URL resolving on attribute values with no quotes (#1489275)
 * Fix wrong handling of links with '|' character (#1489276)
 * Fix colorspace issue on image conversion using ImageMagick (#1489270)
 * Fix XSS vulnerability when saving HTML signatures (#1489251)
 * Fix XSS vulnerability when editing a message "as new" or draft (#1489251)
 * Fix rewrite rule in .htaccess (#1489240)
 * Fix detecting Turkish language in ISO-8859-9 encoding (#1489252)
 * Fix identity-selection using Return-Path headers (#1489241)
 * Fix parsing of links with ... in URL (#1489192)
 * Fix compose priority selector when opening in new window (#1489257)
 * Fix bug where signature wasn't changed on identity selection when editing a draft (#1489229)
 * Fix IMAP SETMETADATA parameters quoting (#1489231)
 * Fix "could not load message" error on valid empty message body (#1489228)
 * Fix handling of message/rfc822 attachments on message forward and edit (#1489214)
 * Fix parsing of square bracket characters in IMAP response strings (#1489223)
 * Don't clear References and in-Reply-To when a message is "edited as new" (#1489216)
 * Fix messages list sorting with THREAD=REFS
 * Remove deprecated (in PHP 5.5) PREG /e modifier usage (#1489174)
 * Fix empty messages list when register_globals is enabled (#1489157)
 * Fix so valid and set date.timezone is not required by installer checks (#1489180)
 * Canonize boolean ini_get() results (#1489189)
 * Fix so install do not fail when one of DB driver checks fails but other drivers exist (#1489178)
 * Fix so exported vCard specifies encoding in v3-compatible format (#1489183)

## RELEASE 0.9.2

 * Fix image thumbnails display in print mode (#1489134)
 * Fix height of message headers block (#1489108)
 * Fix timeout issue on drag&drop uploads (#1489170)
 * Fix default sorting of threaded list when THREAD=REFS isn't supported
 * Fix list mode switch to 'List' after saving list settings in Larry skin (#1489164)
 * Fix error when there's no writeable addressbook source (#1489162)
 * Fix zipdownload plugin issue with filenames charset (#1489156)
 * Fix so non-inline images aren't skipped on forward (#1489150)
 * Fix "null" instead of empty string on messages list in IE10 (#1489145)
 * Fix legacy options handling
 * Fix so bounces addresses in Sender headers are skipped on Reply-All (#1489011)
 * Fix bug where serialized strings were truncated in PDO::quote() (#1489142)
 * Fix displaying messages with invalid self-closing HTML tags (#1489137)
 * Fix PHP warning when responding to a message with many Return-Path headers (#1489136)
 * Fix unintentional compose window resize (#1489114)
 * Fix performance regression in text wrapping function (#1489133)
 * Fix connection to posgtres db using unix socket (#1489132)
 * Fix handling of comma when adding contact from contacts widget (#1489107)
 * Fix bug where a message was opened in both preview pane and new window on double-click (#1489122)
 * Fix fatal error when xdebug.max_nesting_level was exceeded in rcube_washtml (#1489110)
 * Fix PHP warning in html_table::set_row_attribs() in PHP 5.4 (#1489094)
 * Fix invalid option selected in default_font selector when font is unset (#1489112)
 * Fix displaying contact with ID divisible by 100 in sql addressbook (#1489121)
 * Fix browser warnings on PDF plugin detection (#1489118)
 * Fix fatal error when parsing UUencoded messages (#1489119)

## RELEASE 0.9.1

 * Better German labels for from/to to avoid conflicts with 'sender' (#1489084)
 * Fix problem where security warning was displayed for valid images with image/jpg type (#1489097)
 * Fix handling of invalid email addresses in headers (#1489092)
 * Fix IMAP connection issue with default_socket_timeout < 0 and imap_timeout < 0 (#1489090)
 * Fix various PHP code bugs found using static analysis (#1489086)
 * Fix backslash character handling on vCard import (#1489085)
 * Fix csv import from Thunderbird with French localization (#1489059)
 * Fix messages list focus issue in Opera and Webkit (#1489058)
 * Fix Reply-To header handling in Reply-All action (#1489037)
 * Fix so Sender: address is added to Cc: field on reply to all (#1489011)
 * Fix so addressbook_search_mode works also for group search (#1489079)
 * Fix removal of a contact from a group in LDAP addressbook (#1489081)
 * Inlcude SQL query in the log on SQL error (#1489064)
 * Fix handling untagged responses in IMAP FETCH - "could not load message" error (#1489074)
 * Fix very small window size in Chrome (#1488931)
 * Fix list page reset when viewing a message in Larry skin (#1489076)
 * Fix min_refresh_interval handling on preferences save (#1489073)
 * Fix PDF support detection for Firefox PDF.js (#1488972)
 * Fix possible collision in generated thumbnail cache key (#1489069)
 * Fix exit code on bootsrap errors in CLI mode (#1489044)
 * Fix error handling in CLI mode, use STDERR and non-empty exit code (#1489043)
 * Fix error when using check_referer=true
 * Fix incorrect handling of some specific links (#1489060)
 * Fix incorrect handling of leading spaces in text wrapping
 * Fix unintentional messages list jumps on click in Internet Explorer (#1489056)
 * Fix list of required configuration options (#1489055)
 * Fix DB error when creating a new contact and a group is selected (#1489051)
 * Fix handling of deprecated boolean value of reply_mode option (#1489052)

## RELEASE 0.9.0

 * Fix display of HTML entities in protected folder name (#1489042)
 * Set minimal permissions to temp files (#1488996)
 * Improve content check for embedded images without filename (#1489029)
 * Fix handling of invalid characters in message headers and output (#1489032)
 * Avoid race-conditions with concurrent attachment uploads (#1488422)
 * Fix selecting collapsed rows on select-all (#1489036)
 * Fix possible header duplicates when using additional headers (#1489033)
 * Fix session issues with use_https=true (#1488986)
 * Fix blockquote width in sent mail (#1489031)
 * Fix keyboard events on list widgets in Internet Explorer (#1489025)

## RELEASE 0.9-rc2

 * Fix security issue in save-pref command
 * Remove sig_above configuration option, use reply_mode only (#1489001)
 * Refresh current folder in opener window after draft save or message sent (#1488997)
 * Fix saving draft just after entering compose window (#1489012)
 * Fix javascript error in IE9 when loading form with placeholders into an iframe (#1489008)
 * Fix handling of some conditional comment tags in HTML message (#1489004)
 * Fix so forward as attachment works if additional attachment is added by message_compose hook (#1489000)
 * Better handling of session errors in ajax requests (#1488960)
 * Fix HTML part detection for some specific message structures (#1488992)
 * Don't show fake address - phishing prevention (#1488981)
 * Fix forward as attachment bug with editormode != 1 (#1488991)
 * Fix LIMIT/OFFSET queries handling on MS SQL Server (#1488984)
 * Fix javascript errors when working in a page opened with taget="_blank"
 * Mention SQLite database format change in UPGRADING file (#1488983)
 * Increase maxlength to 254 chars for email input fields in addressbook (#1488987)
 * Fix thumbnail size when GD extension is used for image resize (#1488985)
 * Display notice that message is encrypted also for application/pkcs7-mime messages (#1488526)

## Release 0.9-rc

 * Updated translations from Transifex
 * Fix plain text spellchecker icorrect highlighting in non-ASCII text (#1488973)
 * Add workaround for invalid message charset detection by IMAP servers (#1488968) 
 * Fix NUL characters in content-type of ms-tnef attachment (#1488964)
 * Fix regression in handling LDAP contact identifiers (#1488959)
 * Fix buggy error template in a frame (#1488938)
 * Add addressbook widget on compose page in classic skin
 * Add search box to compose address book widget (#1488381)
 * Fix login in case when default_host is an array with one element (#1488928)
 * Use LDAP fallback hosts on connect + bind instead of ldap_connect() only.
 * Add config option for LDAP bind timeout (sets LDAP_OPT_NETWORK_TIMEOUT option)
 * Submit Addressbook advanced search form with Enter key (#1488568)
 * Also block remote images in HTML part view (#1488827)
 * Improved database schema upgrade procedure, added updatedb.sh script
 * Force autocommit mode in mysql database driver (#1488902)

## Release 0.9-beta

 * Fix searching by date in address book (#1488888)
 * Improve charset detection by prioritizing charset according to user language (#1485669)
 * Fix handling of escaped separator in vCard file (#1488896)
 * Fix #countcontrols issue in IE<=8 when text is very long (#1488890)
 * Add option to use envelope From address for MDN responses (#1488880)
 * Add possibility to search in message body only (#1488770)
 * Support "multipart/relative" as an alias for "multipart/related" type (#1488886)
 * Display PGP/MIME signature attachments as "Digital Signature" (#1488570)
 * Workaround UW-IMAP bug where hierarchy separator is added to the shared folder name (#1488879)
 * Fix version comparisons with -stable suffix (#1488876)
 * Add unsupported alternative parts to attachments list (#1488870)
 * Add Compose button on message view page (#1488747)
 * Display 'Sender' header in message preview
 * Plugin API: Added message_before_send hook
 * Fix contact copy/add-to-group operations on search result (#1488862)
 * Use matching identity in MDN response (#1488864)
 * Fix unwanted horizontal scrollbar in message preview header (#1488866)
 * Fix handling of signatures on draft edit (#1488798)
 * Fix so compacting of non-empty folder is possible also when messages list is empty (#1488858)
 * Allow forwarding of multiple emails (#1486854)
 * Fix big memory consumption of DB layer (#1488856)
 * Add workaround for IE<=8 bug where Content-Disposition:inline was ignored (#1488844)
 * Fix XSS vulnerability in vbscript: and data:text links handling (#1488850)
 * Fix broken message/part bodies when FETCH response contains more untagged lines (#1488836)
 * Fix empty email on identities list after identity update (#1488834)
 * Add new identities_level: (4) one identity with possibility to edit only signature
 * Use Delivered-To and Envelope-To headers for identity selection (#1488840, #1488553)
 * Fix XSS vulnerability using Flash files (#1488828)
 * Fix absolute positioning in HTML messages (#1488819)
 * Fix cache (in)validation after setting \Deleted flag
 * Fix keybord events on messages list in opera browser (#1488823)
 * Fix selection of collapsed thread rows (#1488772)
 * Always save drafts with format=flowed in order to keep original line wraps (#1488799)
 * Fix wrapping of quoted text with format=flowed (#1488177)
 * Select default_addressbook on the list in Address Book (#1488280)
 * Fix so mobile phone has TYPE=CELL in exported vCard (#1488812)
 * Support contacts import from CSV file (#1486399)
 * Improved keep-alive action. Now the interval is based on session_lifetime (#1488507)
 * Added cross-task 'refresh' request for system state updates (#1488507)
 * Renamed config options: keep_alive to refresh_interval, min_keep_alive to min_refresh_interval
 * Fix handling of text/enriched content on message reply/forward/edit
 * Option to display attached images as thumbnails below message body
 * Upgraded to jQuery 1.8.3 and jQuery UI 1.9.1
 * Add config option to automatically generate LDAP attributes for new entries
 * Add user settings to open message view and compose form in new windows (#1485486)
 * Better client-side timezone detection using the jsTimezoneDetect library (#1488725)
 * Add option to disable saving sent mail in Sent folder - no_save_sent_messages (#1488686)
 * Fix handling dont_override with message_sort_col and message_sort_order settings (#1488760)
 * Fix handling of URLs with asterisk characters (#1488759)
 * Remove automatic to-lowercase conversion of usernames (#1488715)
 * Plugin API: Add 'email_list' argument for identities data in user_create hook
 * Integrated zipdownload plugin to download all attachments (#1445509)
 * Fix HTML special characters handling in message list/header display (#1488523)
 * List related text/html part as attachment in plain text mode (#1488677)
 * Use IMAP BINARY (RFC3516) extension to fetch message/part bodies
 * Fix folder creation under public namespace root (#1488665)
 * Fix so "Edit as new" on draft creates a new message (#1488687)
 * Fix invalid error message on deleting mail from read only folder (#1488694)
 * Replace data URIs of images (pasted in HTML editor) with inline attachments (#1488502)
 * Remove (too big) min-width on mail screen
 * Added template object 'frame'
 * Add option to enable HTML editor on forwarding (#1488517)
 * Add option to not include original message on reply, rename option top_posting to reply_mode (#1485149)
 * Added session_path config option and unified cookies settings in javascript
 * Added "Undeleted" option to messages list filter
 * Rewritten test scripts for PHPUnit
 * Add new DB abstraction layer based on PHP PDO, supporting SQLite3 (#1488332)
 * Removed PEAR::MDB2 package
 * Removed users.alias column, added option ('user_aliases')
  to use email address from identities as username (#1488581)
 * Removed redundant cache.cache_id column (#1488528)
 * Fix order of attachments in sent mail (#1488423)
 * Fix Shift + delete button does not permanently delete messages (#1488243)
 * Add Content-Length for attachments where possible (#1485478)
 * Fix attachment sizes in message print page and attachment preview page (#1488515)
 * Add mail attachments using drag & drop on HTML5 enabled browsers
 * Add workaround for invalid BODYSTRUCTURE response - parse message with Mail_mimeDecode package (#1485585)
 * Display Tiff as Jpeg in browsers without Tiff support (#1488452)
 * Don't display Pdf/Tiff/Flash attachments inline without browser support (#1488452, #1487929)
 * Add is_escaped attribute for html_select and html_textarea (#1488485)
 * Fix issue where draft auto-save wasn't executed after some inactivity time
 * Add vCard import from multiple files at once (#1488015)
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

 * Fix #countcontrols issue in IE<=8 when text is very long (#1488890)
 * Fix unwanted horizontal scrollbar in message preview header (#1488866)
 * Add workaround for IE<=8 bug where Content-Disposition:inline was ignored (#1488844)
 * Fix XSS vulnerability in vbscript: and data:text links handling (#1488850)
 * Fix absolute positioning in HTML messages (#1488819)
 * Fix keybord events on messages list in opera browser (#1488823)
 * Fix cache (in)validation after setting \Deleted flag
 * Fix selection of collapsed thread rows (#1488772)
 * Fix wrapping of quoted text with format=flowed (#1488177)

## Release 0.8.4

 * Fix XSS vulnerability in handling of text/enriched messages (#1488806)
 * Fix handling of 'media' attribute on linked css (#1488789)
 * Fix regression where unintentional page reload was done after request abort (#1488802)
 * Fix excessive LFs at the end of composed message with top_posting=true (#1488797)
 * Fix bug where leading blanks were stripped from quoted lines (#1488795)

## Release 0.8.3

 * Fix AREA links handling (#1488792)
 * Fix possible HTTP DoS on error in keep-alive requests (#1488782)
 * Fix compatybility with MDB2 2.5.0b4 (#1488779)
 * Fix a bug where saving a message in INBOX wasn't possible
 * Fix HTML part detection in messages with attachments (#1488769)
 * Fix bug where wrong words were highlighted on spell-before-send check
 * Fix scrolling quirk in email preview frame using Opera 12 (#1488763)
 * Fix displaying of multipart/alternative messages with empty parts (#1488750)
 * Fix Warning: htmlspecialchars(): charset `RCMAIL_CHARSET' not supported warning in Installer (#1488744)
 * Fix threaded list sorting on PHP < 5.2.9 (#1488748)

## Release 0.8.2

 * Fix XSS vulnerability from HTTP User-Agent header (#1488737)
 * Force fonts in compose fields to be all the same (#1488690)
 * Add full headers view in message preview window (#1488538)
 * Fix message display page issues (#1488590, #1488642)
 * Fix handling vCard entries with TEL;TYPE=CELL (#1488728)
 * Fix error where session wasn't updated after folder rename/delete (#1488692)
 * Fix PLAIN authentication for some IMAP servers (#1488674)
 * Fix encoding vCard file when contains PHOTO;ENCODING=b (#1488683)
 * Fix focus issue in IE when selecting message row (#1488620)
 * Fix displaying all headers when they contain malformed characters (#1488666)
 * Fix decoding of HTML messages with UTF-16 charset specified (#1488654)
 * Fix quota capability detection so it can be overwritten by a plugin (#1488655)
 * Fix identity selection on reply (#1488101)
 * Fix Larry's messages list filter in IE (#1488632)
 * Fix more IE issues by disabling Compat. mode with X-UA-Compatible meta tag (#1488626)
 * Fix setting locales under Solaris - use additional .UTF-8 suffix (#1488628)
 * Fix email address validation for addresses with IP address in domain part
 * Fix Larry skin issues in IE7 compat. mode (#1488618)
 * Fix so subscribed non-existing/non-accessible shared folder can be unsubscribed

## Release 0.8.1

 * Fix bug where domain name was converted to lower-case even with login_lc=false (#1488593)
 * Fix lower-casing email address on replies (#1488598)
 * Fix line separator in exported messages (#1488603)
 * Fix XSS issue where plain signatures wasn't secured in HTML mode (#1488613)
 * Fix XSS issue where href="javascript:" wasn't secured (#1488613)
 * Fix impossible to create message with empty plain text part (#1488610)
 * Fix stripped apostrophes when replying in plain text to HTML message (#1488606)
 * Fix inactive Save search option after advanced search (#1488607)
 * Fix Remove from group option is active for contact search result (#1488608)
 * Disable autocapitalization in login form on iPad/iPhone (#1488609)
 * Fix focus on the list when list row is clicked (#1488600)
 * Added separate From and To columns apart from smart From/To column (#1486891)
 * Fix fallback to Larry skin when configured skin isn't available (#1488591)
 * Fix (workaround) delete operations with some versions of memcache (#1488592)
 * Fix (disable) request validation for spell and spell_html actions

## Release 0.8.0

 * Renamed old default skin to 'classic'. Larry is the new default skin.
 * Support connections to memcached socket file (#1488577)
 * Enable TinyMCE inlinepopups plugin
 * Update to TinyMCE 3.5.6
 * Correctly escape localized labels in javascript variable (#1488567)
 * Update Net_SMTP/Auth_SASL packages to fix Digest-MD5/Cram-MD5 authentication (#1488571)
 * Don't add attachments content into reply/forward/draft message body (#1488557)
 * Fix 'no connection' errors on page unloads (#1488547)
 * Plugin API: Add 'unauthenticated' hook (#1488138)
 * Show explicit error message when provided hostname is invalid (#1488550)
 * Fix wrong compose screen elements focus in IE9 (#1488541)
 * Fix fatal error when date.timezone isn't set (#1488546)
 * Update to TinyMCE 3.5.4.1
 * Better icons with distinct shapes for priority columns (#1488377)
 * Show dedicated icon for multipart/report messages (#1488524)
 * Properly hide text of icon links/buttons (#1488534)
 * Fix handling of unitless CSS size values in HTML message (#1488535)
 * Fix removing contact photo using LDAP addressbook (#1488420)
 * Fix storing X-ANNIVERSARY date in vCard format (#1488527)
 * Update to Mail_Mime-1.8.5 (#1488521)
 * Fix XSS vulnerability in message subject handling using Larry skin (#1488519)
 * Fix handling of links with various URI schemes e.g. "skype:" (#1488106)
 * Fix handling of links inside PRE elements on html to text conversion
 * Fix indexing of links on html to text conversion
 * Decode header value in rcube_mime::get() by default (#1488511)
 * Fix errors with enabled PHP magic_quotes_sybase option (#1488506)
 * Fix SQL query for contacts listing on MS SQL Server (#1488505)
 * Fix window.resize handler on IE8 and Opera (#1488453)
 * Don't let error message popups cover the login form (#1488500)
 * Don't show errors when moving contacts into groups they are already in (#1488493)
 * Make folders with unread messages in subfolders bold again (#1486793)
 * Abbreviate long attachment file names with ellipsis (#1488499)
 * Fix html2text conversion of strong|b|a|th|h tags when used in upper case
 * Add listcontrols template container in Larry skin (#1488498)
 * Fix host autoselection when default_host is an array (#1488495)
 * Move messages forwarding mode setting into Preferences
 * Fix HTML entities handling in HTML editor (#1488483)
 * Fix listing shared folders on Courier IMAP (#1488466)



## Release 0.8-rc

 * Added new translations in Belarusian, Interlingua and Malayalam
 * Flipped compose options arrow (#1488474)
 * Fix handling of large uuencode attachments (#1488473)
 * Fix handling of "usemap" attribute (#1488472)
 * Fix handling of some HTML tags e.g. IMG (#1488471)
 * Use similar language as a fallback for plugin localization (#1488401)
 * Fix issue where signature wasn't re-added on draft compose (#1488322)
 * Update to TinyMCE 3.5 (#1488459)
 * Fixed multi-threaded autocompletion when number of threads > number of sources
 * Allow to configure the number of values allowed for each LDAP attribute
 * Support for serialized LDAP address values (usually delimited with a $)
 * Less restrictive session auth checks, repeat keep-alive requests on failure (#1488449)
 * Fix redirect to mail/compose on re-login (#1488226)
 * Add IE8 hack for messages list issue (#1487821)
 * Fix handling errors on draft auto-save
 * Fix importing vCard photo with ENCODING param specified (#1488432)
 * Support mutliple name/email pairs for Bcc and Reply-To identity settings (#1488445)
 * Fix parent folder permissions checking on folder creation (#1488443)
 * Set flexible width to login form fields (#1488418)
 * Fix re-draw bug on list columns change in IE8 (#1487822)
 * Allow mass-removal of addresses from a group (#1487748)
 * Fix removing all contacts on import to LDAP addressbook
 * Fix so "Back" from compose/show doesn't reset search request (#1488238)
 * Add option to delete messages instead of moving to Trash when in Junk folder (#1486686)
 * Fix invisible cursor when replying to a html message (#1487073)
 * Reset IP stored in session when destroying session data (#1488056)
 * Fix bug where memory_limit = -1 wasn't handled properly
 * Support mutliple name/email pairs for Bcc and Reply-To identity settings (#1488445)
 * Support LDAP RFC2256's country object class read/write (#1488123)
 * Upgraded to jQuery 1.7.2
 * Image resize with GD extension (#1488383)
 * Fix lack of warning when switching task in compose window (#1488399)
 * Fix bug where it wasn't possible to enter ( or & characters in autocomplete fields
 * Request all needed fields from address book backends (#1488394)
 * Unified (single) spellchecker button
 * Scroll long lists on drag&drop (#1485946)
 * Copy all skins in installto script (#1488376)

## Release 0.8-beta

 * Upgraded to jQuery 1.7.1 (#1488337) and jQuery UI 1.8.18
 * Add Russian to the spellchecker languages list (#1488135)
 * Remember custom skin selection after logout (#1488355)
 * Make sure About tab is always the last tab (#1488257)
 * Fix issue with folder creation under INBOX. namespace (#1488349)
 * Added mailto: protocol handler registration link in User Preferences (#1486580)
 * Handle identity details box with an iframe (#1487020)
 * Fix issue where some text from original message was missing on reply (#1488340)
 * Fix parse errors in DDL files for MS SQL Server
 * User configurable setting how to display contact names in list
 * Make contacts list sorting configurable for the admin/user
 * Revert SORT=DISPLAY support, removed by mistake (#1488327)
 * Fix autoselect_host() for login (#1488297)
 * Fix drafts update issues when edited from preview pane (#1488314)
 * Changed license to GNU GPLv3+ with exceptions for skins & plugins
 * Make mime type detection based on filename extension to be case-insensitive
 * Fix failure on MySQL database upgrade from 0.7 - text column can't have default value (#1488300)
 * Added address book widget on compose screen
 * Use proper timezones from PHP's internal timezonedb (#1485592)
 * Add separate pagesize setting for mail messages and contacts (#1488269)
 * Deprecate $DB, $USER, $IMAP global variables, Use $RCMAIL instead
 * Add option to set default font for HTML message (#1484137)
 * Fix issues with big memory allocation of IMAP results
 * Prevent from memory_limit exceeding when trying to pa