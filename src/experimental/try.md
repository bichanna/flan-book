# `try` Expression
In Feo, this is how you would typically handle runtime exceptions:
```js
result := unsafe some_func("abc")
match error?(result) {
    true -> {
        // error handling
    },
    false -> {
        // do something with the result
    }
}
```
It's quite tedious to write all of that code. That's when `try` expression comes in handy.

The code above can be rewritten with a `try` expression like this:
```js
result := unsafe some_func("abc")
try result {
    // error handling
} else {
    // do something with the result
}
```
