# Assignment
The assignment operator `:=` binds values on the right side to names on the left, potentially by destructuring an object or list. For example:
```js
a : = 1 // a is 1

[b, c] := [4, "string"] // b is 4, and c is "string"

{first_name: name} := {first_name: "Nobuharu", last_name: "Shimazu"} // name is "Nobuharu"
```

The nonlocal assignment operator `=` binds values on the right side to names on the left, but only when those variables already exist.
If the variable doesn't exist in the current scope, the operator ascends up parent scopes until it reaches the global scope to find the last scope where that name was bound.
```js
n := 1
m := 2
{
    n = 3
    m := 4
}
n // 3
m // 2
```
