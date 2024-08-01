# Language Tour
In this book, we explore the fundamentals of the Flan language, namely its syntax, core data structures, and flow control features. If you have some prior programming experience, this will hopefully be enough to get you started with Flan.

## Overly Simplifed Overview

In Flan, everything is an expression. That means everything evaluates to some value, like `2 * 3`, which is `6`.

### Types

Flan has 7 primitive types and 3 complex ones:
```js
null         // Null
_            // "Empty" value, equal to everything
1, 2, 4      // Integers
3.45         // Floats
true, false  // Booleans
"Hello!"     // Strings
:ok          // Atoms

[:error, 1, "blah", false] // Lists
{age: 16, name: "Nobu"}    // Objects
func (x, y) x + y          // Functions
```

### Assignment
You can bind values on the right side to names on the left, potentially by destructuring an object or list by `:=`.
```js
num := 1
[a, b] := [123, 456] // a is 123, and b is 456

{
    full_name: name, // name is "Nobuharu Shimazu"
    email_address: email, // email is "nobu.bichanna@gmail.com"
} := {
    full_name: "Nobuharu Shimazu",
    email_address: "nobu.bichanna@gmail.com"
}
```
Reassignment operator `=`:
```js
age := 15
age = 16 // age is now 16
```

### Control Flows
`match` expression is the only control flow in Flan.
```js
name := "Nobu"
match name {
    "Nobu" -> println("Cool name!"),
    "Sol" -> println("Nice name."),
    "Damian" -> println("Eh, nice, I guess?"),
    _ -> println("Hello, " + name),
}
```

But there is also a short-hand `match`, which is known as the ternary operator.
```js
damian_stinks := false
command := damian_stinks ? "go take a shower" : "go take a nap"

// de-sugars to this:
command = match damian_stinks {
    true -> "go take a shower",
    _ -> "go take a nap",
}
```

### Functions
You can define a function like so:
```js
func add(x, y) x + y
// same as
add := func(x, y) x + y
```

### Pipe Operator
It takes a value on the left and makes it the first argument to a function call on the right:
```js
func add(x, y) x + y
10 |> add(15) |> add(12) // 37
```
