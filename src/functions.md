# Functions

## Named Functions
Named functions in Feo are defined using the `func` keyword.
```js
func greet(name) {
    println("Hello, " + name + "!")
}
```

Functions in Feo are first class values and can be assigned to variables, passed to functions, or anything else you might do with any other data type.
```js
// This function takes a function as an argument
func twice(f, x) {
    f(f(x))
}

func add_one(x) x + 1

func add_two(x) twice(add_one, x)
```

### Default Arguments
If a function is not passed a sufficient amout of arguments, it becomes `null` by default:
```js
func some_func(a, b) {}
some_func(:hello) // a = :hello and b = null
```
There is [`default`](./library/std.md#defaultx-base) function in [`std` module](./library/std.md).
```js
{default: default} := import("std")

func some_func(a, b) {
    b = default(b, "Hello")
}
```

### Rest Parameters
You can add `+` after parameter name if you are unsure about the number of arguments to pass in the functions.
```js
{each: each} := import("std")

func sum(nums+) {
    reduce(nums, 0) <| func(accumulator, elem) accumulator + elem
}

sum(1, 4, 5, 3, 6)
```

## Pipe Operator
Feo provides syntax for passing the result of one function to the arguments of another function, the pipe operator (`|>`).
This is similar in functionality to the same operator in Elixir or F#.

The pipe operator allows you to chain function calls without using a plethora of parenthesis.
```js
names := []
append(append(append(append(names, "Nobu"), "Sol"), "Damian"), "Thomas")
names // ["Nobu", "Sol", "Damian", "Thomas"]
```
This can be expressed more naturally using the pipe operator, eliminating the need to track parenthesis closure.
```js
names
|> append("Nobu")
|> append("Sol")
|> append("Damian")
|> append("Thomas")
```
Each line of this expression applies the function to the result of the previous line.

## Anonymous Functions
Anonymous functions can be defined with a similar syntax:
```js
func run() {
    add := func(x, y) x + y

    add(1, 2) // 3
}
```
