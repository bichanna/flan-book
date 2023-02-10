# Booleans
A Boolean can be either `true` or `false`.

Feo defines a handful of operators that work with Booleans.

`&&` evaluates the right hand side if the left hand side is `true`.

`||` evaluates the right hand side if the left hand side is `false`.

You can also use `and` and `or` keywords instead of `&&` and `||` respectively.

```js
false && false // => false
false && true  // => false
true && false  // => false
true && true   // => true
false and true // => false

false || false // => false
false || true  // => true
true || false  // => true
true || true   // => true
true or false  // => true
```

Feo supports negation of Booleans using either the `!` unary operator.
```js
!true  // => false
!false // => true
```
