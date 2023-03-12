# Macros
Impala's macros are just text-replacement templates, similar to C language's. So, a macro is a piece of code that is given a name.

A variable-like macro can be defined with `def` keyword:
```js
def PI 3.1415

radius := 12
area := #PI * radius * radius
// expands to `area := 3.1415 * radius * radius`
```

You can also define macros that work in a similar way as a function call.
```js
def PI 3.1415
def CIRCLE_AREA(r: expr) #PI * ^r * ^r

#CIRCLE_AREA(10)
// exapends to `3.1415 * 10 * 10`
```

Another example with tokens:
```js
def BINARY_OP(left: expr, op: token, right: expr) ^left ^op ^right

#BINARY_OP(10, +, 20) // expands to `10 + 20`
#BINARY_OP(100, -, 5) // expands to `100 - 5`
```

You can also reassign macros with `redef` keyword.
```js
def PI 3.1415
redef PI 3.141592653589793238 // redefine PI

radius := 12
area := #PI * radius * radius
// expands to `area := 3.141592653589793238 * radius * radius`
```
