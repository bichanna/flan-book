# `fmt`
`fmt` is the string formatting library for Flan.

 - [`format`](#formatraw-values)
 - [`print`](#printraw-values)
 - [`println`](#printlnraw-values)

## `format(raw, values+)`
`format` returns the format string `raw`, where each substring of the form "{}" has been replaced by the corresponding value given in the arguments.
```js
name := "Nobu"
format("Hello, {}!", name) // "Hello, Nobu!"
```

## `print(raw, values+)`
`print` prints the result of `format(raw, values+)` to the standard output stream.
```js
// Don't be confused with built-in function `print`!
fmt.print("Hello, {}!", "Nobu") // Hello, Nobu!
```

## `println(raw, values+)`
`println` prints the result of `format(raw, values+)` to the standard output stream with a newline.
```js
// Don't be confused with built-in function `println`!
fmt.println("Hello, {}!", "Nobu") // Hello, Nobu!\n
```
