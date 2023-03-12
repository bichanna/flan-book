# Macros
Impala's macros are just text-replacement templates, similar to C language's. So, a macro is a piece of code that is given a name.

A variable-like macro can be defined with `def` keyword:
```js
def PI 3.1415

radius := 12
area := #PI * radius * radius
// expands to `area := 3.1415 * radius * radius`
```


You can also redefine macros with `redef` keyword.
```js
def PI 3.1415
redef PI 3.141592653589793238 // redefine PI

radius := 12
area := #PI * radius * radius
// expands to `area := 3.141592653589793238 * radius * radius`
```
