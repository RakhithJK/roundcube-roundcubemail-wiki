# Plugin Events in JavaScript

> NOTE: This page requires review and update

There are yet a few events that your script can subscribe to:

## Global Events

### init

The first event to be triggered when a page loads.
This is the place where plugins can add their UI elements and register custom commands.

_Arguments:_
  * task
  * action


### selectfolder

Triggered when a user selects a new folder (either in mail or address book task).
Please note that this is called before the message list is reloaded.

_Arguments:_
  * folder: _New selected folder name_
  * old: _Previously selected folder_


### listupdate

Similar to the _selectfolder_ event but triggered after the message list (or contacts) list was updated.

_Arguments:_
  * folder
  * rowcount


### insertrow

This hook is triggered after a new row was added to the message list or the contacts list respectively.

_Arguments:_
  * uid: _Row UID_
  * row: _Reference to the according DOM node_


### group_insert

This hook is triggered after a new contact group was added to the folders list.

_Arguments:_
  * id: _Group ID_
  * name: _Group name_
  * li: _Reference to the list item node_


### group_update

This hook is triggered after contact group was updated in the folders list.

_Arguments:_
  * id: _Group ID_
  * name: _Group name_
  * li: _Reference to the list item node_


### group_delete

This event is triggered just before a contact group is removed from the folders list.

_Arguments:_
  * id: _Group ID_
  * li: _Reference to the list item to be removed_


### before* and after*

As you might have seen in the code the RoundCube client is based on _commands_ which can be triggered by different UI elements. To make this document as short as possible we just describe two general events: `before<command>` and `after<command>`.

These events are triggered before and after the RoundCube client executes a certain command. An event handler of the `before*` events can return `false` in order to prevent the command to be executed.