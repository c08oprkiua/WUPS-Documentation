# Enums

# Macros

## `WUPS_PLUGIN_NAME("{your plugin's name here}")`

This sets the visible name of your plugin. 

## `WUPS_PLUGIN_DESCRIPTION("{a description of your plugin here}")`

This sets the visible description of your plugin. 

## `WUPS_PLUGIN_VERSION("{version of your plugin here}")`

This sets the visible revision of your plugin. 

## `WUPS_PLUGIN_AUTHOR("{author(s) of your plugin here}")`

This sets the visible author(s) of your plugin.

## `WUPS_PLUGIN_LICENSE("{your plugin's license here}")`

This sets the visible license that your plugin is licensed under (eg. MIT, GNUv3, etc.).

## `WUPS_FS_ACCESS()`

This tells WUPS that your plugin wants SD/USB access.

## `WUPS_USE_WUT_DEVOPTAB()`

Use the WUT devoptabs.

# Signals (Event Hooks)

These are all function-like macros that are called by WUPS upon various system events. Define them like a function (ie. `{signal}() {your code here}` to use them.

## `INITIALIZE_PLUGIN()`

*Called to initialize the plugin

## `ON_APPLICATION_START()`

*Called when an application is started 

## `ON_APPLICATION_ENDING()`

*Called when an application is being closed

## `ON_APP_STATUS_CHANGED(status)`

# Functions
