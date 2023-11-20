# Storage

*The Aroma Plugin System contains a function set for storing and retrieving plugin settings.

# Enums

## `wups_storage_type_t`
`WUPS_STORAGE_TYPE_INVALID` = 0

Invalid storage type.

`WUPS_STORAGE_TYPE_STRING` = 1

String storage type.

`WUPS_STORAGE_TYPE_INT` = 2

32 bit unsigned integer (`uint32_t`) storage type.

`WUPS_STORAGE_TYPE_ITEM` = 3

Raw binary data storage type. Internally is converted into Base64.

## `WUPSStorageError`

`WUPS_STORAGE_ERROR_SUCCESS` = 0

This means there was no error in accessing storage. 

`WUPS_STORAGE_ERROR_NOT_OPENED` = -1

*This means you called `WUPS_CloseStorage` unneccesarily (eg. you never called `WUPS_OpenStorage` or called `WUPS_CloseStorage` twice in a row.

`WUPS_STORAGE_ERROR_ALREADY_OPENED` = -2

*This means you have called `WUPS_OpenStorage` twice without calling `WUPS_CloseStorage` in between.

`WUPS_STORAGE_ERROR_INVALID_ARGS` = -3

This means you provided invalid arguments to whichever function you called.

`WUPS_STORAGE_ERROR_NOT_FOUND` = -4

*This is a nonspecific error for when an error happens, but is not of any other error type.

`WUPS_STORAGE_ERROR_NOT_INITIALIZED` = -5

*This means you haven't yet initialized your storage.

`WUPS_STORAGE_ERROR_INVALID_BACKEND_PARAMS` = -6

*Unused error...?

`WUPS_STORAGE_ERROR_INVALID_JSON` = -7

*Unused error...?

`WUPS_STORAGE_ERROR_IO` = -8

*Unused error...?

`WUPS_STORAGE_ERROR_B64_DECODE_FAILED` = -9

*This means that the encoding of Item (binary) data to base64 failed. 

`WUPS_STORAGE_ERROR_BUFFER_TOO_SMALL` = -10

*This means that the data you were attempting to get is larger than the size parameter passed in to `WUPS_GetBinary()`

`WUPS_STORAGE_ERROR_MALLOC_FAILED` = -11



`WUPS_STORAGE_ERROR_NOT_ACTIVE_CATEGORY` = -13

*This means that the category of information you are trying to obtain or store is not the currently loaded category.

# Macros

## WUPS_USE_STORAGE("{storage dir here}");

*Selects the config file for the storage API. This should be located in `sd:/wiiu/environments/{environment}/plugins/config/` as `{storage dir here}.json`

# Functions
All these functions return a `WUPSStorageError`, with the exception of `closeItem` and `WUPS_GetStorageStatusStr`

`WUPS_GetStorageStatusStr(WUPSStorageError status)`

Call this to get an entered `WUPSStorageError` error, `status`, but as a string. 

`WUPS_InitStorage(wups_loader_init_storage_args_t args)`

**This is called by the backend.** Initializes storage.

`WUPS_OpenStorage`

`closeItem(wups_storage_item_t *item)`

*Closes an item?

`WUPS_CloseStorage`

Closes storage and saves changes.

`WUPS_DeleteItem`

Deletes a key from storage.

`WUPS_CreateSubItem`

Creates a sub item.

`WUPS_GetSubItem`

Gets a sub item. Must be called on a SubItem before getting sub-values from it.

`WUPS_StoreString(wups_storage_item_t *parent, const char *key, const char *string)`

Store a string in storage. 
*`*parent` is the category the string is in, `*key` is the key for the string, and `*string` is the string itself you're trying to store.

`WUPS_StoreBool(wups_storage_item_t *parent, const char *key, bool value)`

Store a boolean value in storage.

`WUPS_StoreInt(wups_storage_item_t *parent, const char *key, int32_t value)`

Store a `uint32_t` integer in storage.

`WUPS_StoreBinary(wups_storage_item_t *parent, const char *key, const void *data, uint32_t size)`

Store raw binary data in storage.

`WUPS_GetString(wups_storage_item_t *parent, const char *key, char *outString, uint32_t maxSize)`

Get a string from storage.

`WUPS_GetBool(wups_storage_item_t *parent, const char *key, bool *outBool)`

Get a boolean value from storage.

`WUPS_GetInt(wups_storage_item_t *parent, const char *key, int32_t *outInt)`

Get a `uint32_t` value from storage.

`WUPS_GetBinary(wups_storage_item_t *parent, const char *key, void *outData, uint32_t maxSize)`

Get raw binary data from storage.
*`*parent` is the parent Item/Subitem, `*key` is the key for the data, `*outData` is a reference to where you want the data output to go, and `maxSize` is the maximum size of the `outData`.
