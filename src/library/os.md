# `os`
`os` module provides a few functions related to operating system dependent functionality.
If you just want to read or write a file see [`os/file` module](./file.md), and if you want to manipulate paths, see the [`os/path` module](./path.md).

 - [`get_cwd`](#get_cwd)
 - [`chdir`](#chdirpath)
 - [`mkdir`](#mkdirpath)
 - [`rmdir`](#rmdirpath)
 - [`rm`](#rmpath)
 - [`modi_time`](#modi_timepath)
 - [`filesize`](#filesizepath)
 - [`system`](#systemcmd)
 - [`exe_path`](exe_path)

## `get_cwd()`
`get_cwd` returns the current working directory.
```js
cwd := get_cwd()
```

## `chdir(path)`
`chdir` changes the current working directory.
```js
chdir("..")
```

## `mkdir(path)`
`mkdir` creates a new directory at the path. The path should be valid.
```js
mkdir("./new_dir")
```

## `rmdir(path)`
`rmdir` removes an empty directory at the path.
```js
rmdir("./new_dir")
```

## `rm(path)`
`rm` removes a file at the path.
```js
rm("./test.txt")
```

## `modi_time(path)`
`modi_time` returns the modified timestamp of the file.
```js
modi_time("./test.txt")
```

## `filesize(path)`
`filesize` returns the file size in bytes.
```js
filesize("./test.txt")
```

## `system(cmd)`
`system` executes the command in a subprocess and returns the exit code of the child process
```js
system("echo hello")
```

## `exe_path()`
`exe_path` returns the path of the Impala interpreter executable.
```js
path := exe_path()
```
