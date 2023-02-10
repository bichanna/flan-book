## Lists
Lists are ordered collections of values. They're one of the most common data structures in Feo.

Lists are *homogeneous*, meaning the elements of a list can be of different types.
```js
[:err, "something wrong happened"]
[["abc", "hello"], 23, 3.14]
```
Under the hood, lists are just Rust `Vector`s.

A built-in function `append` is provided to append a value to a list.
```js
names := ["Nobu", "Damian", "Thomas"]
names |> append("Sol")

names // ["Nobu", "Damian", "Thomas", "Sol"]
```

You can access each element by `[]`.
```js
ages := [16, 15, 15, 14]
ages[0] // 16
```
