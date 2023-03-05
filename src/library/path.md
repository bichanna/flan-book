# `path`
`path` module implements utilities for working with UNIX style paths on file systems and in URIs.

 - [`abs`](#abspath)
 - [`abs?`](#abspath-1)
 - [`rel`](#relpath-from)
 - [`rel?`](#relpath)
 - [`join`](#joinpaths)
 - [`base`](#basepath)
 - [`dir`](#dirpath)
 - [`dir?`](#dirpath-1)
 - [`file?`](#filepath)
 - [`exists?`](#existspath)
 - [`ext`](#extpath)
 - [`list_dir`](#list_dirpath)

## `abs(path)`
`abs` returns the absolute path of `path`.
```js
abs("./abc.txt")
```

## `abs?(path)`
`abs?` returns `true` if the path is absolute, and otherwise `false`.
```js
abs?("./abc.txt") // false
```

## `rel(path, from)`
`rel` returns the relative path of `path` from the `from` directory.
```js
rel("./abc.txt", "../../some_dir")
```

## `rel?(path)`
`rel?` returns `true` if the path is relative, and otherwise `false`.
```js
rel?("./abc.txt") // true
```

## `join(paths)`
`join` joins multiple paths together into a single valid path.
```js
join("./some_dir", "./file.txt")
```

## `base(path)`
`base` base returns the last element of a path, which is typically the file or directory referred to by the path.
```js
base("./abc.txt") // "abc.txt"
```

## `dir(path)`
`dir` returns the portion of the a path that represents the directory containing it. In effect, this is all but the last part of a path.
```js
dir("./some_dir/another_dir/some_file.txt") // "./some_dir/another_dir/"
```

## `dir?(path)`
`dir?` returns `true` if the path is a directory.
```js
dir?("./some_dir/") // true
```

## `file?(path)`
`file?` returns `true` if the path is a file.
```js
file?("./abc.txt") // true
```

## `exists?(path)`
`exists?` returns `true` if the path exists.
```js
exists("./some_file.txt") 
```

## `ext(path)`
`ext` returns the file extension of the path.
```js
ext("./some_file.txt") // "txt"
```

## `list_dir(path)`
`list_dir` returns all the entries in the directory at the path as a list.
```js
list_dir(".")
```
