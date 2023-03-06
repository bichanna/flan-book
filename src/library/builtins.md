# Built-in Functions
The Impala interpreter has a number of functions and types built into it that are always available.
All of them are listed here.

 - [`abs`](#absx)
 - [`import`](#importx) 
 - [`int`](#intx) 
 - [`float`](#floatx)
 - [`string`](#stringx)
 - [`atom`](#atomx)
 - [`type`](#typex)
 - [`len`](#lenxs)
 - [`append`](#appendxs-x)
 - [`append!`](#appendxs-x-1)
 - [`pop`](#popxs-i)
 - [`pop!`](#popxs-i-1)
 - [`keys`](#keysobj)
 - [`values`](#valuesobj)
 - [`args`](#args)
 - [`env`](#env)
 - [`get`](#getobj-key)
 - [`print`](#printx)
 - [`println`](#printlnx)
 - [`eprint`](#epintx)
 - [`eprintln`](#eprintln)
 - [`error`](#errort-msg)
 - [`error?`](#errorx)

## `abs(x)`
`abs` returns the absolute value of a number.

## `import(x)`

`import` imports the module `x`.

## `int(x)`
`int` converts `x` to an integer.

## `float(x)`
`float` converts `x` to a float.

## `string(x)`
`string` converts `x` to a string.

## `atom(x)`
`atom` converts `x` to an atom.

## `type(x)`
`type` returns the type of `x` as an atom: `:int`, `:float`, `:string`, `:atom`, `:list`, or `:object`.
```js
pi := 3.1415
type(pi) // :float
```

## `len(xs)`
`len`returns the length of a string, a list, or an object.
```js
list := ["Hello", "World"]
len(list) // 2
```

## `append(xs, x)`
`append` creates a new list or string, `x` appended to `xs`.
```js
list := [1, 2]
list = append(list, 3)
list // [1, 2, 3]
```

## `append!(xs, x)`
`append!` appends `x` to `xs`, a list or string, mutating it.
```js
list := [1, 2]
append!(list, 3)
list // [1, 2, 3]
```

## `pop(xs, i)`
`pop` creates a new list or string, the item at index `i` popped from `xs`, and returns a list of the new value and the popped value.
`i` is optional and defaults to `len(xs) - 1`.
```js
list := [1, 2, 3]
[list, popped] := pop(list) // list is [1, 2], and popped is 3
```

## `pop!(xs, i)`
`pop!` pops the value of `xs` at index `i`, mutating the list or string. `i` is optional and defaults to `len(xs) - 1`.
```js
list := [1, 2, 3]
popped := pop!(list) // popped is 3
```

## `keys(obj)`
`keys` returns a list of the keys of the object `obj`.
```js
obj := {name: "Nobu", email: "nobu.bichanna@gmail.com"}
keys(obj) // [:name, :email]
```

## `values(obj)`
`values` returns a list of the values of the object `obj`.
```js
obj := {name: "Nobu", email: "nobu.bichanna@gmail.com"}
values(obj) // ["Nobu", "nobu.bichanna@gmail.com"]
```

## `args()`
`args` returns a list of command line arguments.

## `env()`
`env` returns all environment variables as an object.

## `get(obj, key)`
`get` returns the value of the item with the key `key`, which could be an atom or a string. It is unsafe (might throw an error).
```js
obj := {name: "Nobu"}
get(obj, :name) // "Nobu"
```

## `print(x)`
`print` prints `x` to the standard output stream.
```js
print("Hello, world\n")
```

## `println(x)`
`println` prints `x` to the standard output stream with a new line at the end.
```js
println("Hello, world")
```

## `eprint(x)`
`eprint` prints `x` to the standard error stream.
```js
eprint("something wrong happened!\n")
```

## `eprintln(x)`
`eprintln` prints `x` to the standard error stream with a new line at the end.`
```js
eprintln("something wrong happened!")
```

## `error(t, msg)`
`error` creates a new error with type `t` and `msg`.
```js
err := unsafe error(:some_error, "some error!")
err.error_type    // :some_error
err.error_message // "some error!"
```

## `error?(x)`
`error?` checks if `x` is an error object or not.
```js
result := unsafe (10 / 0)
match error?(result) {
    true -> "Math still works!",
    false -> "Math is broken ;(",
}
```
