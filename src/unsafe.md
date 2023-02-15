# Exceptions

Until now errors have never been mentioned, but if you have tried out the examples you have probably seen some.
There are two distinguishable kinds of errors: *syntax errors* and *exceptions*.

## Syntax Errors
Syntax errors, also known as parsing errors, are perhaps the most common kind of complaint you get while you are still learning Feo.
```js
some_file:1:14 error: expected ']'
names["hello"
```

## Runtime Exceptions
Even if an expression is syntactically correct, it may cause an error when an attempt is made to execute it:
```js
some_file:1:11 zero division error: division by zero
n := 10 / 0
```

## Handling Runtime Exceptions
It is possible to write programs that handle exceptions. The previous line of code can be handled like this:
```js
result := unsafe (10 / 0)
match error?(result) {
    true -> println!("Math still works!"),
    false -> println!("Math is broken :("),
}
```
If an expression evaluates without any errors, the `unsafe` expression returns the value:
```
func return_one() 1

result := unsafe return_one()
result // 1
```

An exception is just an object that has two properties: `error_type` and `error_message`. For example:
```js
{
    error_type: :zero_division,
    error_message: "division by zero"
}
```

### User-defined Runtime Errors
Programs may name their own exceptions by creating a new exception:
```js
error(:user_defined, "user-defined error!")
```
