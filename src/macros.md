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
def CIRCLE_AREA(r) #PI * ^r * ^r

#CIRCLE_AREA(10)
// exapends to `3.1415 * 10 * 10`
```


You can also reassign macros with `redef` keyword.
```js
def PI 3.1415
redef PI 3.141592653589793238 // redefine PI

radius := 12
area := #PI * radius * radius
// expands to `area := 3.141592653589793238 * radius * radius`
```
