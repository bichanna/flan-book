# Match Expression
The `match` expression is the most common kind of flow control in Feo code.
It allows us to say "if the data has this shape then do that", which we call *pattern matching*.

Here, we match on an Int and return a specific string for the values 0, 1, and 2.
The final pattern n matches any other value that did not match any of the previous patterns.
```js
match some_number {
  0 -> "zero",
  1 -> "one",
  2 -> "two",
  _ -> "some other number", // This matches anything
}
```

Pattern matching on a Boolean value is the Feo alternative to the `if else` statement found in other languages.
```js
match some_bool {
  true -> "It's true.",
  false -> "It's not true.",
}
```

Feo's case is an expression, meaning it returns a value and can be used anywhere we would use a value.
For example, we can name the value of a case expression with a variable binding.
```js
description := match true {
    true -> "blah blah",
    false -> "halb halb",
}

description // "blah blah"
```

## Destructuring
A `match` expression can be used to destructure values that contain other values, such as lists and objects.
```js
match [number % 3, number % 5] {
    [0, 0] -> "FizzBuzz",
    [0, _] -> "Fizz",
    [_, 0] -> "Buzz",
    [a, b] -> a + b,
}
```
