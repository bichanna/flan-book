# `file`
`file` module offers filesystem APIs to Impala programs.

Some functions in `file` are implemented in both synchronous and asynchronous variants.
Sync variants of functions block, and return the value immediately for ease of use.
For better performance, we can pass a callback to the function to invoke its asynchronous variant.
In that case, the function will not block. Instead, the callback will be called some time later with the return value.

 - [`read_buf_size`](#read_buf_size)
 - [`sync_read_file`](#sync_read_filepath)
 - [`async_read_file`](#async_read_filepath-fn)
 - [`write_file`](#write_filepath-file-flag)
 - [`list_files`](#list_filespath)

## `read_buf_size`
`read_buf_size` is the size of the buffer used to read a file in streaming file-read operations in `fs` module.
This may be changed to alter the behavior of `fs`, but it will affect the behavior of libfs globally in your program.
```js
read_buf_size := 4096
```

## `sync_read_file(path)`
`sync_read_file` reads the entire contents of a file at `path` and returns the file contents as a string if successful or throw an error.
```js
content := unsafe sync_read_file("./test.txt")
```

## `async_read_file(path, fn)`
`async_read_file` reads the entire contents of a file at `path` and returns the file contents as a string to `fn` if successful or `null` on an error.
```js
async_read_file("./test.txt", func(content) {
    println(content)
})
```

## `write_file(path, file, flag)`
`write_file` writes data in `file` to a file at `path` and returns `true` on success and throws an error on error.
`flag` can control the behavior of `write_file`. Possible options for `flag` are `:append` and `:truncate`.
```js
result := unsafe write_file("./test.txt", "Hello, world!", :append)
```

## `list_files(path)`
`list_files` returns a list of files and directories in a directory at `path`.
If the directory does not exist or is not a directory, or if the read failed, it throws an error.
```js
files := unsafe list_files("./")
```
