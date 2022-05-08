# Available Plugin Hooks

The registered callback function receives a _hash array_ as single argument which contains hook specific data (called _Arguments_ in the following list). It can then alter some of these values (listed as _Return values_) by returning a hash array containing the modified values.

Index:

* [Global Hooks](#global-hooks)
* [Task "login"](#task-login)
* [Task "logout"](#task-logout)
* [Task "mail"](#task-mail)
* [Task "addressbook"](#task-addressbook)
* [Task "settings"](#task-settings)
* [Template Hooks](#template-hooks)
* [Missing documentation](#missing-documentation)


## Global Hooks

### startup

When the application is initialized.
This is the place where task and action arguments can be altered.

_Arguments:_
  * task
  * action

_Return values:_
  * task
  * action


### ready

(since 0.7-beta)

When the application is ready, user is authenticated and the request was checked.
This is the place where task and action arguments can be altered too. It is executed before
any actions and task's func.inc files.

_Arguments:_
  * task
  * action

_Return values:_
  * task
  * action


### config_get

On direct access to a config option, plugins can inject their own values or implement an
alternative storage for configuration.

_Arguments:_
  * name
  * default
  * result

_Return values:_
  * result


### storage_folders

Former `mailboxes_list`

Triggered whenever a list of the mailboxes is requested from the IMAP class.
If no plugin returns a list, the default list is retrieved.

_Arguments:_
  * root: _Root folder_
  * name: _Folder name pattern_
  * filter: _Optional filter_
  * mode: _Query mode: LSUB or LIST_

_Return values:_
  * folders: _Folders list to be used_


### render_mailboxlist

When the mailbox list is about to be rendered.
This hook allows plugins to alter the folder tree or to localize folder names.

_Arguments:_
  * list: _The hierarchical list of mailboxes_
  * delimiter: _IMAP hierarchy delimiter_

_Return values:_
  * list


### write_log

Triggered every time a message is sent to the logs.
Setting the `abort` field to true finishes log action before writing to file.

_Arguments:_
  * name: _The name of the target log_
  * line: _The line to write to the log_

_Return values:_
  * name
  * line
  * abort

### console

Called for debug logging.
Setting the `abort` field to true avoids regular debug logging which will again trigger the `write_log`hook.

_Arguments:_
  * args: _List of variables to dump_

_Return values:_
  * args
  * abort


### email2user

Triggered whenever a email-to-user lookup is executed.

_Arguments:_
  * email: _E-mail address_

_Return values:_
  * user: _User login_


### user2email

Triggered whenever a login-to-email lookup is executed.
Can be used also to set initial identities for a new user.

_Arguments:_
  * user: _User login_
  * first: _True if one entry is expected_
  * extended: _True if array result (email and identity data) is expected_

_Return values:_
  * email: _E-mail address (or array of arrays with keys: email, name, organization, reply-to, bcc, signature, html_signature)_


### request_token

(since 0.6-beta)

Request tokens created for CSRF prevention are passed to this hook before they're used.
A plugin can register or even alter these request tokens.

_Arguments:_
  * value

_Return values:_
  * value


### refresh

(since 0.9-rc)

Hook triggered by periodic polling requests from the client to collect updates or new data. This only happens on AJAX requests
and plugins can execute actions on the client by adding command calls to the output object:

    $rcmail->output->command('plugin.somecallback');

_Arguments:_
  * last: _timestamp of last refresh call_

_Return values:_
  none.

----

## Task "login"

### authenticate

Before the user login on the IMAP server is performed.

_Arguments:_
  * host
  * user
  * pass
  * cookiecheck
  * valid

_Return values:_
  * host
  * user
  * pass
  * cookiecheck: _set to false to disable cookie check_
  * valid: _set to true to disable CSRF check._ (since 0.5.1)
  * abort: _set to true to skip the imap login and fail_
  * error: _if using abort, also set error to any string (else you will get a storage error)_

### login_after

Triggered after a user successfully logged in.
This hook allows a plugin to control the redirect after the login form was submitted. Information about the current user can be obtained from the `rcube_user` object at `rcmail::get_instance()->user`

_Arguments:_
  * [_url parameters, e.g. task, action, etc._]

_Return values:_
  * task
  * action
  * [_more url parameters_]


### login_failed

Triggered if user authentication failed.
Could be useful for logging or to give more detailed feedback to the user why the login failed.

_Arguments:_
  * host
  * user
  * code

_Return values:_
  none.


### user_create

When a somebody logs in the first time and a local user is created.
Return values will also be used to create the default identity for this new user.

_Arguments:_
  * user
  * user_name
  * user_email
  * host

_Return values:_
  * user_name
  * user_email
  * alias
  * language


### oauth_login

(since 1.5-rc)

Hook triggered after successful authentication via OAuth.
It provides all data exchanged with the OAuth service including access and refresh tokens as well as identity information.

_Arguments:_
  * access_token: The access token obtained from the OAuth service
  * token_type: The token type (e.g. Bearer)
  * refresh_token: The refresh token (if supplied)
  * expires: Unix timestamp when the access token will expire
  * username: The username of the authenticated session
  * identity: Hash array with identity information of the authenticated user

_Return values:_
  none.


### oauth_refresh_token

(since 1.5-rc)

Hook triggered after the OAuth access token was refreshed.
It provides all data exchanged with the OAuth service including access and refresh tokens as well as identity information.

_Arguments:_
  * access_token: The access token obtained from the OAuth service
  * token_type: The token type (e.g. Bearer)
  * expires: Unix timestamp when the access token will expire

_Return values:_
  none.


----

## Task "logout"

### session_destroy

Triggered when a user logs out and the session is destroyed.

_Arguments:_
  none.

_Return values:_
  none.


### logout_after

After the user is logged out and the session is killed, this hook is triggered.
The arguments still contain some user info which is not available in `$_SESSION` anymore.
It's also possible to redirect to some other URL in this hook because it's the last action in the logout process.

_Arguments:_
  * host
  * user
  * language

_Return values:_
  none.


----

## Task "mail"

### storage_init

Former _imap_init_

This hook allows you to configure some IMAP communications options.

_Arguments:_
  * fetch_headers: _String appended to the FETCH HEADER.FIELDS () list_
  * message_flags: _Hash array with message flags and their IMAP equivalents_

_Return values:_
  * fetch_headers: _String with additional headers to be fetched (separated by space)_
  * message_flags


### storage_connect

Triggered right before connecting to the IMAP server.
Similar to the _authenticate_ hook but triggered in every step not just on login.

_Arguments:_
  * host
  * user
  * attempt: _Number of connection attempt (if retry is returned)_

_Return values:_
  * host
  * user
  * pass
  * retry: _Set this to true for anther connection attempt_


### storage_connected

(since 1.1-beta)

Triggered after successful IMAP logins.

_Arguments:_
  * host
  * user
  * session: _IMAP session identifier if provided by the server_

_Return values:_
  none.


### message_load

Triggered when a message is loaded from the server, namely when a new rcube_message object was created.
This allows one to analyze the structured message object and find specific attachments, headers or contents for further actions.

_Arguments:_
  * object: _The rcube_message instance_

_Return values:_
  none.


### message_read

Triggered when a message is loaded and its SEEN flag is not yet set.
The `message` argument will give you access to all the message headers and its structure.

_Arguments:_
  * uid
  * mailbox
  * message: _The according rcube_message instance_

_Return values:_
  none.


### message_part_structure

Triggered for every part of the message structure when it's parsing is processed.
The _structure_ argument holds a hierarchical list of the current part and its sub-parts.

_Arguments:_
  * object: _The rcube_message instance_
  * structure: _The raw part structure from the IMAP server_
  * mimetype: _Content type of the part (lowercase)_
  * recursive: _True if the part is parsed recursively (a sub-part)_

_Return values:_
  * structure
  * mimetype
  * recursive


### message_part_before

Triggered before a message part (text or html) is cleaned/formatted.

_Arguments:_
  * type
  * body
  * safe
  * plain
  * inline_html

_Return values:_
  * type
  * body
  * safe
  * plain
  * inline_html


### message_part_after

After message text part formatting.

_Arguments:_
  * type
  * body
  * safe
  * plain
  * inline_html

_Return values:_
  * body


### message_part_get

(since 0.8-beta)

Callback when downloading or displaying a non-text part of a message (e.g. an attachment).

_Arguments:_
  * uid: _The message UID_
  * id:  _The part's mime number_
  * mimetype: _The part's mime type_
  * download: _True if download is forced_
  * part: _The message part structure_

_Return values:_
  * mimetype
  * download
  * body


### message_headers_output

Triggered when building the message headers table for display. 
If you want to add more headers, you need to fetch them at the _storage_init_ hook.

_Arguments:_
  * output: _Hash array with all the headers to be put into the html table_
  * headers: _Message headers object_

_Return values:_
  * output: _Altered headers array_


### message_check_safe

Sets message _safe_ flag when a message contains a HTML part. This hooks allows plugins to alter the _safe_
flag after the lookup for known senders was executed. Check `$args['message']->is_safe` and set 
`$args['message']->set_safe(true|false)` to modify the setting.

_Arguments:_
  * message: _The according rcube_message instance_

_Return values:_
  none.


### message_objects

Hook to render the alert box displayed above a message when links to remote images or resources are detected.
This is also triggered for draft messages showing the edit button.

_Arguments:_
  * content: _Array with alert box contents_
  * message: _The according rcube_message instance_

_Return values:_
  * content: _Altered headers array_


### message_body_prefix

Contents prepended to the message body block when viewing an email message.

_Arguments:_
  * part: _rcube_message_part instance of the rendered body part_
  * prefix: _The content to be prepended_

_Return values:_
  * prefix


### message_compose

Triggered when the compose step is executed (before redirecting).
This allows a plugin to manipulate the request parameters and pre-fill the compose form.
Even attachments can be appended to the message using this hook.

_Arguments:_
  * param: _Array with request parameters_

_Return values:_
  * param: _Compose parameters like 'to', 'subject', 'body' _
  * attachments: _Array of attachments to be added. An entry (array) should contain the fields 'path', 'name' and 'mimetype' _


### message_compose_body

Triggered during the compose step.
This allows a plugin to modify the body of a message after the blank/draft/forward has been assembled, but before the compose form is displayed.

_Arguments:_
  * body: _The body of the message_

_Return values:_
  * body: _The body of the message_


### attachment_upload

Triggered every time a user uploads an attachment in message compose mode.
This hook is mainly used by core plugins that handle the storage of the uploaded files.

_Arguments:_
  * path: _Temporary file path to the uploaded file_
  * name: _The original file name_
  * mimetype: _Detected mime-type_

_Return values:_
  * status: _True if the file was successfully stored (required)_
  * error: _Error message in case a plugin rejects the upload and sets the `abort` flag_
  * id: _The unique ID of the file to get retrieve it later on (required)_
  * name
  * mimetype
  * abort


### attachment_save

Triggered for every attachment of forwarded message before compose.
This hook is mainly used by core plugins that handle the storage of mail attachments.

_Arguments:_
  * path: _Temporary file path or_
  * data: _File contents (if path is empty)_
  * name: _The original file name_
  * mimetype: _Detected mime-type_
  * content_id: _Message part ID_

_Return values:_
  * status: _True if the file was successfully stored (required)_
  * id: _The unique ID of the file to get retrieve it later on (required)_
  * name
  * mimetype


### message_outgoing_headers

(deprecated, use [message_before_send](#message_before_send) or [message_ready](#message_ready) hooks instead)

Before a mail message is sent, this hooks allows you to set additional mail headers.

_Arguments:_
  * headers: _Hash array with current message headers_

_Return values:_
  * headers
  * abort: _If true the message will not be sent_
  * message: _The reason why the message was not sent which will be shown to the user_


### message_outgoing_body

Before a mail message is composed, this hook is triggered before adding the message body contents.

_Arguments:_
  * body: _The message body to be added_
  * type: _html|plain|alternative_
  * message: _Reference to current MailMime object_

_Return values:_
  * body


### message_ready

(since 1.2-beta)

Before a composed message is either sent or saved as draft, this hook allows final modifications to the mime structure.

_Arguments:_
  * message: _Reference to current MailMime object_

_Return values:_
  * message: _The modified or completely replaced MailMime object_


### smtp_connect

Triggered when before opening an SMTP connection to send a message.
Some SMTP related config options are passed as arguments and can be altered by a plugin.

_Arguments:_
  * smtp_server
  * smtp_port
  * smtp_user
  * smtp_pass
  * smtp_auth_type
  * smtp_helo_host

_Return values:_
  _all arguments_


### message_before_send

Triggered before message is finally sent

_Arguments:_
  * message: _Message object (Mail_mime)_
  * from: _Sender address string_
  * mailto: _Either a comma-separated list of recipients (RFC822 compliant), or an array of recipients, each RFC822 valid_
  * options: _SMTP options_

_Return values:_
  * message
  * from
  * mailto
  * options
  * abort: _Aborts sending operation._
  * error: _Error message as string or arguments to be passed to rcube::gettext(). Used with abort=true_
  * result: _Boolean result of send operation. Used with abort=true._


### message_sent

Triggered when a message is finally sent
This hook doesn't have any return values but can be used for logging or notifications.

_Arguments:_
  * headers: _Hash array with all message headers_
  * body: _The full message body as text or file handle_

_Return values:_
  none.


### message_draftsaved

(since 0.8-beta)

Triggered when a message is saved as draft .
This hook can be used for logging or notifications and it can overwrite the displayed confirmation message.

_Arguments:_
  * msgid: _The message ID header value_
  * uid: _The UID of the message saved_
  * folder: _The folder where the message was saved in_

_Return values:_
  * message: _Confirmation message text to display_


### check_recent

Triggered before checking the given folders for new messages. Plugins can alter the list of folders
to be considered for the checking.

_Arguments:_
  * folders: _The list of folders to be checked_
  * all: _True if checking all folders is enabled_

_Return values:_
  * folders


### new_messages

Triggered in step _check_recent_ if some new (recent) messages are available.
This hook doesn't have any return values but it can add some javascript actions to the output.

_Arguments:_
  * mailbox: _The current mailbox_

_Return values:_
  none.


### html_editor

Triggered to add HTML editor scripts into the page.
You can use it to replace default TinyMCE editor.

_Arguments:_
  * mode: _Editor mode. Specifies where editor is used. For identity signature or message body_

_Return values:_
  * abort


### quota

Triggered after fetching mailbox quota resource usage and limits from IMAP server.

_Arguments:_
  * total: _Mailbox size limit in kilobytes. Not set if server doesn't support IMAP quota._
  * used: _Current mailbox size in kilobytes. Not set if server doesn't support IMAP quota._
  * percent: _Current mailbox size in percent. Not set if server doesn't support IMAP quota._

_Return values:_
  * total: _Mailbox size limit in kilobytes._
  * used: _Current mailbox size in kilobytes._
  * percent: _Current mailbox size in percent._


### messages_list

Triggered before sending the message list.
You can use it to set message headers, list_cols/list_flags and other rcube_mail_header variables.
Also use it to pass additional plugin related flags to the UI using the extra_flags array.

_Arguments:_
  * messages: _List of message headers._
  * cols: _All the currently visible columns._

_Return values:_
  * messages
  * cols

----


## Task "addressbook"

### addressbooks_list

Triggered when building the list of address sources in the address book view.
Each entry in the _sources_ list needs to hold the following fields: _id, name, readonly_.

_Arguments:_
  * sources: _Hash array with list of available address books_

_Return values:_
  * sources


### addressbook_get

This hook is triggered each time an address book object is requested.
The _id_ parameter specifies which address book the application needs. If it's the ID of the plugins' address book, this hooks should return an according instance of a `rcube_addressbook` implementation.

_Arguments:_
  * id

_Return values:_
  * instance: _Instance of an address book implementation derived from rcube_addressbook_


### contact_validate

(since 1.0-beta)

Triggered before an contact record is saved (e.g. created or updated).
A plugin can perform additional validation checks and reject the contact data from being saved.

_Arguments:_
  * record: _Hash array with record fields_
  * autofix: _Attempt to automatically fill the missing fields_
  * valid: _Result of the default pre-validation_

_Return values:_
  * record: _Record data with corrected values_
  * valid: _Set to false if invalid_
  * error: _Provide a reason if validation failed_
  * abort


### contact_create

Triggered when an new address book record is created.
A plugin can prevent the contact to be created by setting the `abort` field to true. The user is then rejected back to the input form.

_Arguments:_
  * record: _Hash array with record fields_
  * source: _Address book identifier_

_Return values:_
  * record
  * abort


### contact_update

Triggered when an address book record is saved.
As in the _create_contact_ hook this action can be aborted by setting the `abort` field to true.

_Arguments:_
  * id
  * record: _Hash array with record fields_
  * source: _Address book identifier_

_Return values:_
  * record
  * abort


### contact_delete

Triggered when an address book record is to be deleted.
To abort the deletion a plugin can set the `abort` field to true.

_Arguments:_
  * id
  * source: _Address book identifier_

_Return values:_
  * abort


### contact_displayname

(since 0.6-beta)

When saving a contact without name field or when adding a contact from mail task,
all data is passed to this hook where the display name can be composed.

_Arguments:_
  * name: _The name of the contact to be saved (could be empty)_
  * email: _E-mail address_
  * prefix
  * firstname
  * middlename
  * surname
  * suffix

_Return values:_
  * name


### group_create

(since 0.4-beta)

Triggered when a contacts group is to be created.
A plugin can set the `abort` field to true in order to prevent the creation of this group.

_Arguments:_
  * name: _The name of the group to create_
  * source: _Address book identifier_

_Return values:_
  * name
  * abort
  * message: _Reason why this operation was aborted_


### group_delete

(since 0.4-beta)

Triggered when a specific contacts group should be deleted.
To abort the deletion a plugin can set the `abort` field to true.

_Arguments:_
  * group_id: _The group identifier_
  * source: _Address book identifier_

_Return values:_
  * abort
  * message: _Reason why this operation was aborted_


### group_rename

(since 0.4-beta)

This hook is triggered when a contacts group is renamed.
To abort this operation a plugin can set the `abort` field to true.

_Arguments:_
  * group_id: _The group identifier_
  * name: _New name of the group_
  * source: _Address book identifier_

_Return values:_
  * abort
  * message: _Reason why this operation was aborted_


### group_addmembers

(since 0.4-beta)

When one or more contacts are added to a contacts group.
A plugin can set the `abort` field to true in order to prevent this action.

_Arguments:_
  * ids: _List of contact IDs (string separated by comma)_
  * group_id: _The group identifier_
  * source: _Address book identifier_

_Return values:_
  * ids
  * abort
  * message: _Reason why this operation was aborted_


### group_delmembers

(since 0.4-beta)

Contacts are about to be removed from a group.
A plugin can set the `abort` field to true in order to prevent this action.

_Arguments:_
  * ids: _List of contact IDs (string separated by comma)_
  * group_id: _The group identifier_
  * source: _Address book identifier_

_Return values:_
  * ids
  * abort
  * message: _Reason why this operation was aborted_


----


## Task "settings"

### settings_actions

(since 1.0-beta)

Hook to render the top level list of settings sections (aka "tabs").
Plugins which want to define a new section in the settings screen should use this hook instead of injecting a new item with javascript or using the "tabs" in [template_container](#template_container) hook.
Just append the following struct to the _actions_ argument:

    array(
      'command' => '<the-command-executed-on-click>',
      'type' => 'link',
      'label' => '<plugin>.<label-name>',
      'title' => '<plugin>.<label-name>',
      'class' => '<css-class-name>',
    )

_Arguments:_
  * actions: _reference to an html_table object_
  * attrib: _HTML attributes_

_Return values:_
  * actions
  * attrib


### folders_list

Allows a plugin to modify the main table on the manage folders screen

_Arguments:_
  * table: _reference to an html_table object_

_Return values:_
  none.


### preferences_save

(since 1.0-beta)

Allows a plugin to inject data into the array of preferences about to be saved

_Arguments:_
  * prefs: _Hash array with prefs to be saved_

_Return values:_
  * result: boolean
  * abort: boolean
  * prefs: array


### preferences_update

As opposed to the _preferences_save_ hook, this is triggered whenever user preferences are updated.
And that's not limited to the preferences section but can also be executed by another plugin.

_Arguments:_
  * prefs: _Hash array with prefs to be updated_
  * old: _Hash array with currently stored user preferences_
  * userid: _The ID of the user these prefs are saved for_

_Return values:_
  * prefs: array
  * old: array
  * abort: boolean


### preferences_list

Allows a plugin to modify the user preferences table.
This hook is triggered for each section of the user prefs pane. The section is denoted in the _section_ parameter. Possible values are `general, mailbox, mailview, compose, folders, server`

_Arguments:_
  * section: _which section of the prefs pane_
  * blocks: _reference to an array containing preferences blocks/options_

_Return values:_
  * blocks


### preferences_sections_list

Allows a plugin to modify the user preferences sections list.

_Arguments:_
  * list: _list (hash array) of sections_
  * cols: _column names to display_

_Return values:_
  * list
  * cols


### identities_list

Triggered when a users identities are listed.

_Arguments:_
  * list: _The list of identity records_
  * cols: _List of cols to be displayed_

_Return values:_
  * list
  * cols


### identity_create

Triggered when a user attempts to create a new sender identity.
A plugin can prevent the record to be created by setting the `abort` field to true. The user is then rejected back to the input form.

_Arguments:_
  * login: _True if triggered at login when a new user is created (deprecated)_
  * record: _Hash array with identity record fields_

_Return values:_
  * record
  * abort


### identity_create_after

(since 1.1.2)

Triggered when a user successfully saved a new sender identity.
In addition to the `record` property, the arguments also contain the ID of the new identity record.

_Arguments:_
  * id: _The ID of the newly created identity record_
  * record: _Hash array with identity record fields_

_Return values:_
  -


### identity_update

Triggered when a user changes one of his sender identities.
As in the _create_identity_ hook this action can be aborted by setting the `abort` field to true.

_Arguments:_
  * id
  * record: _Hash array with identity record fields_

_Return values:_
  * record
  * abort


### identity_delete

Triggered when a sender identity is to be deleted.
To abort the deletion a plugin can set the `abort` field to true.

_Arguments:_
  * id

_Return values:_
  * abort


### identity_form

Triggered when identity edit form is being build.

_Arguments:_
  * form: _Form content definition array._
  * record: _Identity data array._

_Return values:_
  * form
  * record


----


## Template Hooks

The RoundCube skin retrieves certain parts (e.g. message list, folders list, etc.) from the application with special tags within the HTML templates: `<roundcube:object name="someobject" ... />`. Template hooks are triggered once a template object is rendered. A plugin can alter or extend the html content of a template object.

The hooks are named `template_object_*` where * is the name of the object. A list of all available template objects is given in [wiki:Doc_SkinML#Contentobjects].

_Arguments:_
  * content
  * [_tag attributes_]

_Return values:_
  * content


### template_container

Allows a plugin the add HTML content to a specific container.
A skin template may specify several containers (e.g. taskbar, toolbar, etc...). This hook is triggered when the template engine processes such a container and it is also internally used for adding buttons using `$this->add_button(attrib, container)`. Remember to always add or prepend to the `content` argument and never replace it entirely.

_Arguments:_
  * name: _Name of the container_
  * content: _The container content_

_Return values:_
  * content


### render_page

Triggered after a template was parsed, just before sending the HTML page to the client.
This is the place where plugins can add additional content to the page which is not related to any template object. Use `$rcmail->output->add_footer()` or `$this->include_script()` to extend the html page. Of course it's also possible to directly alter the `content` attribute.

_Arguments:_
  * template: _Name of the rendred template_
  * content: _The HTML source_

_Return values:_
  * content


### send_page

(since 0.6-beta)

The final HTML code of a page is passed to this hook before delivering it to the browser.
Final string-based modifications on the content can be made here.

_Arguments:_
  * content: _The HTML source_

_Return values:_
  * content


### render_response

(since 1.0-beta)

This is the _render_page_ equivalent for AJAX calls and the final opportunity for plugins to append
or modify the server response to the client.

_Arguments:_
  * response: _The full response data structure before being serialized to json_

_Return values:_
  * response



## Missing documentation

Hooks that appear to be missing documentation. Obtained by searching for all calls to plugins->exec_hook in the source of git master:

 * attachment_delete
 * attachment_display
 * attachment_get
 * attachments_cleanup
 * contact_form
 * contact_listname
 * contact_photo
 * contact_undelete
 * folder_create
 * folder_delete
 * folder_form
 * folder_rename
 * folder_update
 * identity_select
 * loginform_content
 * responses_list
 * save_hook
 * saved_search_create
 * saved_search_delete
 * saved_search_get
 * saved_search_list
 * spell_dictionary_get
 * spell_dictionary_save
 * template_plugin_include