Roundcube Mail comes with many useful plugins, which extend its functionality. There are also many third-party plugins, which can be found at [Roundcube Plugins](https://plugins.roundcube.net/).

## Default Plugins

Below is a table of the names and descriptions of the default plugins, which can be found [here](https://github.com/roundcube/roundcubemail/tree/master/plugins).

| Name                       | Description                                                            |
| -------------------------- | ---------------------------------------------------------------------- |
| acl                        | Allows mailbox access control lists to be managed                      |
| additional_message_headers | Adds additional or removes headers from outgoing mail                  |
| archive                    | Adds a button that lets a user move mail to a specified archive folder |
| attachment_reminder        | Reminds a user to attach files to their email                          |
| autologon                  | Performs an automatic login if accessed from `localhost`               |
| database_attachments       | Provides database-backed storage for temporary attachment handling     |
| debug_logger               | Enhances logging for debugging purposes                                |
| emoticons                  | Replaces emoticons in plain-text messages with real icons              |
| enigma                     | Adds support for viewing and sending PGP signed/encrypted mail         |
| example_addressbook        | Sample plugin that implements a hard-coded list of contacts            |
| filesystem_attachments     | Adds basic, filesystem-based temporary attachment handling             |
| help                       ||
| hide_blockquote            | Add possibility to hide long blocks of cited text in messages |
| http_authentication        ||
| identicon                  ||
| identity_select            ||
| jqueryui                   ||
| krb_authentication         ||
| [managesieve](Plugin-managesieve) | Allows to manage Sieve filters in a visual UI using the managesieve protocol |
| [markasjunk](/roundcube/roundcubemail/tree/master/plugins/markasjunk) | Adds "mark as (not) spam" buttons to the message menu |
| new_user_dialog            ||
| new_user_identity          ||
| newmail_notifier           ||
| [password](/roundcube/roundcubemail/tree/master/plugins/password) | Change user password using many via Settings using many methods (drivers) |
| redundant_attachments      ||
| show_additional_headers    ||
| squirrelmail_usercopy      ||
| subscriptions_option       ||
| userinfo                   ||
| vcard_attachments          | Detects VCard attachments and show a button to add them to address book |
| virtuser_file              ||
| virtuser_query             ||
| [zipdownload](/roundcube/roundcubemail/tree/master/plugins/zipdownload) | Download all attachments of a message or a selection of messages as Zip archive |

## Activating Plugins

A plugin is not loaded until you enable it by adding its directory name to the config option `plugins`, as an array element. This is done by editing your local `config/config.inc.php` file.

For example, to enable plugins named `additional_message_headers` and `archive`, `config/config.inc.php` should contain this line:

```php
    $config['plugins'] = array('additional_message_headers', 'archive');
```
To disable a plugin, just remove it from the list.


# Plugin Development
To learn more about developing plugins for Roundcube, see [[Plugin API]].