## Lists
Lists are ordered collections of values. They're one of the most common data structures in Feo.

Lists are *heterogeneous*, meaning the elements of a list can be of different types.
```js
[:err, "something wrong happened"]
[["abc", "hello"], 23, 3.14]
```
Under the hood, lists are just Rust `Vector`s.

A built-in function [`append`](./library/builtins.md#appendxs-x) is provided to append a value to a list.
```js
names := ["Nobu", "Damian", "Thomas"]
names = append(names, "Sol")

names // ["Nobu", "Damian", "Thomas", "Sol"]
```

You can index an element in a list by using `.`.
```js
ages := [16, 15, 15, 14]
ages.0 // 16
```
