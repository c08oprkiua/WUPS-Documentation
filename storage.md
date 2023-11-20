# Enums

The Aroma Plugin System contains functions for storing and retrieving data.

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




# Functions
All these functions return a `WUPSStorageError`, with the exception of `closeItem` and `WUPS_GetStorageStatusStr`

`WUPS_GetStorageStatusStr(WUPSStorageError status)`

Call this to get an entered `WUPSStorageError` error, `status`, but as a string. 

`WUPS_InitStorage(wups_loader_init_storage_args_t args)`

Call this to initialize storage for your plugin. 

`WUPS_OpenStorage`

`closeItem(wups_storage_item_t *item)`

*Closes an item?

`WUPS_CloseStorage`



`WUPS_DeleteItem`

`WUPS_CreateSubItem`

`WUPS_GetSubItem`

`WUPS_StoreString`

`WUPS_StoreBool`

`WUPS_StoreInt`

`WUPS_StoreBinary`

`WUPS_GetString`

`WUPS_GetBool`

`WUPS_GetInt`

`WUPS_GetBinary`

