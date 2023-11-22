[libnotifications](https://github.com/wiiu-env/libnotifications/tree/main), or, in other words, the way to use those neat popup notifications, is *not* part of the Aroma WUPS library. But, seeing as how it is commonly used in plugins, I figured I may as well include it here for convenience, and also so people know where to find it (check the hyperlink). 

This is more or less a reformatting of the comments in the [header files](https://github.com/wiiu-env/libnotifications/tree/main/include/notifications) of the libnotifications source code, so 99% of the credit here goes to Maschell.

# Enums

## `NotificationModuleStatus`

`NOTIFICATION_MODULE_RESULT_SUCCESS` = 0

The library has been initialized successfully. Other functions can now be used.

`NOTIFICATION_MODULE_RESULT_MODULE_NOT_FOUND` = -0x1

The module could not be found. Make sure the module is loaded.

`NOTIFICATION_MODULE_RESULT_MODULE_MISSING_EXPORT` = -0x2

The module is missing an expected export.

`NOTIFICATION_MODULE_RESULT_UNSUPPORTED_VERSION` = -0x3

The version of the loaded module is not compatible with this version of the lib.

`NOTIFICATION_MODULE_RESULT_INVALID_ARGUMENT` = -0x4

Invalid argument was provided to the function called.

`NOTIFICATION_MODULE_RESULT_LIB_UNINITIALIZED` = -0x5

The library is not initialized.

`NOTIFICATION_MODULE_RESULT_UNSUPPORTED_COMMAND` = -0x06

The loaded module version doesn't not support this function.

`NOTIFICATION_MODULE_RESULT_OVERLAY_NOT_READY` = -0x10

The overlay is not ready. See `NotificationModule_IsOverlayReady`.

`NOTIFICATION_MODULE_RESULT_UNSUPPORTED_TYPE` = -0x11



`NOTIFICATION_MODULE_RESULT_ALLOCATION_FAILED` = -0x12

Allocation of the Notification has failed.

`NOTIFICATION_MODULE_RESULT_INVALID_HANDLE` = -0x13



`NOTIFICATION_MODULE_RESULT_UNKNOWN_ERROR` = -0x1000



## `NotificationModuleNotificationType`

`NOTIFICATION_MODULE_NOTIFICATION_TYPE_INFO` = 0, 

Static notification, fades out after fixed time. Can not be updated after creation.

`NOTIFICATION_MODULE_NOTIFICATION_TYPE_ERROR` = 1, 

Static notification, fades out after fixed time, shakes for a fixed time. Can not be updated after creation.

`NOTIFICATION_MODULE_NOTIFICATION_TYPE_DYNAMIC` = 2, 

Dynamic notification, only fades out when told to fade out. Can be updated after creation.


## `NotificationModuleStatusFinish`

`NOTIFICATION_MODULE_STATUS_FINISH` = 0

Fades out the Notification after `durationBeforeFadeOutInSeconds` seconds

`NOTIFICATION_MODULE_STATUS_FINISH_WITH_SHAKE` = 1

Fades out the Notification after `durationBeforeFadeOutInSeconds` seconds, shakes it for `shakeDurationInSeconds` seconds

## `NotificationModuleNotificationOption`

`NOTIFICATION_MODULE_DEFAULT_OPTION_BACKGROUND_COLOR` = 0

Background Color of the Notification. Type: `NMColor`

`NOTIFICATION_MODULE_DEFAULT_OPTION_TEXT_COLOR`

Text Color of the Notification. Type: `NMColor`

`NOTIFICATION_MODULE_DEFAULT_OPTION_DURATION_BEFORE_FADE_OUT`
    
Time in seconds before the Notification will fade out: Type: float. Example: 2.5f = 2.5 seconds
    
`NOTIFICATION_MODULE_DEFAULT_OPTION_FINISH_FUNCTION`
    
Function that will be called when the Notification starts to fade out. Type: NotificationModuleNotificationFinishedCallback

`NOTIFICATION_MODULE_DEFAULT_OPTION_FINISH_FUNCTION_CONTEXT`
    
Context that will be passed to the NOTIFICATION_MODULE_DEFAULT_TYPE_FINISH_FUNCTION callback. Type: void* 

# Structs

## _NMColor
| Variable type | Variable name | Description |
|---------------|---------------|-------------|
| `uint8_t`     | `r`           | red value   |
| `uint8_t`     | `g`           | blue value  |
| `uint8_t`     | `b`           | green value |
| `uint8_t`     | `a`           | alpha value |


# Macros

`NOTIFICATION_MODULE_API_VERSION_ERROR` =  0xFFFFFFFF

# Functions

## `NotificationModule_GetStatusStr(NotificationModuleStatus status);`

* return: char

* status: `NotificationModuleStatus`

Returns a NotificationModuleStatus as a string.

## `NotificationModule_InitLibrary();`

* return: `NotificationModuleStatus`

Initializes the library. **This function has to be called before any other function of this lib (except NotificationModule_GetVersion) can be used.**

## `NotificationModule_DeInitLibrary();`

* return: `NotificationModuleStatus`

Deinitializes the NotificationModule lib.

## `NotificationModule_GetVersion(NotificationModuleAPIVersion *outVersion);`

* return: `NotificationModuleStatus`

* *outVersion: pointer to variable where the version will be stored.

Retrieves the API Version of the loaded NotificationModule.

## `NotificationModule_IsOverlayReady(bool *outIsReady);`

* return: `NotificationModuleStatus`

* *outIsReady: pointer to variable where the boolean of whether the overlay is ready or not is stored.

Checks if the Overlay for Notification is ready. **Notifications can only be added if the overlay is ready.**

## `NotificationModule_SetDefaultValue(NotificationModuleNotificationType type, NotificationModuleNotificationOption optionType,...);``

* return: `NotificationModuleStatus`
