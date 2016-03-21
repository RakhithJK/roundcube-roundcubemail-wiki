# JavaScript API Documentation

Together with the [[Plugin API]] Roundcube allows plugins and third party scripts to access the client object and register specific event listeners as well as custom actions and buttons.


## Adding event listeners

This is generally done with the following two functions:

```js
    rcmail.addEventListener('event', callback);
    rcmail.removeEventListener('event', callback);
```

The `callback` function gets the event object as one single argument. This event object usually contains event-specific properties. These are listed as _arguments_ below the according event description.

There are yet a few events that your script can subscribe to listed in [[Plugin Events]].


## Custom actions and UI elements

Of course a plugin can add its own buttons somewhere in the document and let them call specific functions directly. Nevertheless we recommend to use the command interface of the RoundCube client. It will automatically handle all UI elements linked with a certain command and allows other plugins to hook into your custom commands.

As you can see in the [example](Plugin-API#client-scripts-and-ui-elements), there are a few methods you should know:

```js
    rcmail.add_element(node, container)
```

This method adds the given DOM node to a specific container of the current page. Containers can be extended with custom buttons and other UI elements. Since each skin can build the HTML page individually it's strongly recommended to use this method rather than appending DOM nodes directly to some contains. Roundcube's default skin defines following containers: 'taskbar', 'toolbar', 'tabs', 'userprefs', 'messagemenu', 'markmenu'.

```js
    rcmail.register_button(command, DomId, type, act, sel, over)
```

Buttons can be linked with the command they're triggering. This is useful if you make use of the `rcmail.enable_command()` method to toggle the command status. All linked buttons will automatically be activated/deactivated.

Arguments:
  * command: _String of the command linked with this button_
  * DomID: _ID of the button node_
  * type: `image|input|link` _Type of the button_
  * act: _CSS class or image src for active state_
  * sel: _CSS class or image src for selected state_
  * over: _CSS class or image src for mouse overs_

```js
    rcmail.register_command(command, handler, enable)
```

Custom commands have to be registered together with the callback function which should be executed if the command is triggered. The third argument activates the command right after registration.

```js
    rcmail.enable_command(command[, command, ...], enable)
```

Finally a plugin can toggle the status of its custom commands using this method. Several commands can be enabled/disabled with one call, the last argument just has to be a boolean value that either enables or disabled all commands in the arguments list.
