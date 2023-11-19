# Enums

## `wups_storage_type_t`
`WUPS_STORAGE_TYPE_INVALID` = 0

Invalid storage type.

`WUPS_STORAGE_TYPE_STRING` = 1

String storage type.

`WUPS_STORAGE_TYPE_INT` = 2

32 bit unsigned integer storage type.

`WUPS_STORAGE_TYPE_ITEM` = 3

Raw binary data storage type. Internally is converted into Base64.

## `WUPSStorageError`

`WUPS_STORAGE_ERROR_SUCCESS` = 0

This means there was no error in accessing storage. 

`WUPS_STORAGE_ERROR_NOT_OPENED` = -1

*This means you haven't yet opened anything.

`WUPS_STORAGE_ERROR_ALREADY_OPENED` = -2

*This means you have already called `WUPS_OpenStorage`.

`WUPS_STORAGE_ERROR_INVALID_ARGS` = -3

`WUPS_STORAGE_ERROR_NOT_FOUND` = -4

`WUPS_STORAGE_ERROR_NOT_INITIALIZED` = -5

*This means you haven't yet initialized your storage.

`WUPS_STORAGE_ERROR_INVALID_BACKEND_PARAMS` = -6

`WUPS_STORAGE_ERROR_INVALID_JSON` = -7

`WUPS_STORAGE_ERROR_IO` = -8

`WUPS_STORAGE_ERROR_B64_DECODE_FAILED` = -9

*This means that the encoding of Item (binary) data to base64 failed. 

`WUPS_STORAGE_ERROR_BUFFER_TOO_SMALL` = -10

`WUPS_STORAGE_ERROR_MALLOC_FAILED` = -11

`WUPS_STORAGE_ERROR_NOT_ACTIVE_CATEGORY` = -13

# Macros




# Functions

`WUPS_InitStorage(wups_loader_init_storage_args_t args)`

Call this to initialize storage for your plugin. 

`WUPS_GetStorageStatusStr()`

Call this to get the status of your storage access. Will return one of the Storage errors
