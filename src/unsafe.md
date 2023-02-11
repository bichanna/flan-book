# Unsafe Expression

Until now errors have never been mentioned, but if you have tried out the examples you have probably seen some.
There are two distinguishable kinds of errors: *syntax errors* and *runtime errors*.

## Syntax Errors
Syntax errors, also known as parsing errors, are perhaps the most common kind of complaint you get while you are still learning Feo.
```js
some_file:1:14 error: expected ']'
names["hello"
```

## Runtime Errors
Even if an expression is syntactically correct, it may cause an error when an attempt is made to execute it:
```js
some_file:1:11 zero division error: division by zero
n := 10 / 0
```

## Handling Runtime Errors
It is possible to write programs that handle selected runtime errors. The previous line of code can be improved like this:
```js
result := unsafe (10 / 0)
match error?(result) {
    true -> println!("Math still works!"),
    false -> println!("Math is broken :("),
}
```
An error is just an object that has two properties: `error_type` and `error_message`. For example:
```js
{
    error_type: :zero_division,
    error_message: "division by zero"
}
```
