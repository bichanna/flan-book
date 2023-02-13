# `std`
`std` library defines basic functions for working with Oak values and functions, iterators, and control flow.

 - [`identity`](#identityx)
 - [`is`](#isx)
 - [`default`](#defaultx-base)
 - [`to_hex`](#to_hexn)
 - [`from_hex`](#from_hexs)
 - [`clamp`](#clampmin-max-n-m)
 - [`slice`](#slicexs-min-max)
 - [`clone`](#clonex)
 - [`range`](#rangestart-end-step)
 - [`reverse`](#reversexs)
 - [`map`](#mapxs-f)
 - [`each`](#eachxs-f)
 - [`filter`](#filterxs-f)
 - [`reduce`](#reducexs-seed-f)
 - [`flatten`](#flattenxs)
 - [`append`](#appendxs-ys)

### `identity(x)`
`identity` returns its first argument.
```js
"Hello" == identity("Hello") // true
```

### `is(x)`
`is` returns a predicate that reports whether its argument is equal to `x`.
```js
f := is(2)
f(2)   // true
f("a") // false
```

### `default(x, base)`
`default` returns `x` if `x` is not `null`, or `base` otherwise. It is useful when taking optional arguments in functions with default values.
```js
func some_func(n, times) {
    // times = 1 by default
    times := default(times, 2)
    // do something
}
```

### `to_hex(n)`
`to_hex` takes a number and returns its hexadecimal representation in a string. It fails for negative values.
```js
to_hex(50159747054) // "BADC0FFEE"
```

### `from_hex(s)`
`from_hex` takes a hexadecimal representation of a number and parses it to an integer. It returns `null` if the input is not a valid hexadecimal number.
```js
from_hex("BADC0FFEE") // 50159747054
```

### `clamp(min, max, n, m)`
`clamp` takes values `n`, `m` and "clamps" or constrains it to the range [`min`, `max`], inclusive. If `n > m`, `n` takes priority and clams `m` down to the lower
value. In the returned value, the following are guaranteed:
- `min <= n <= max`
- `min <= m <= max`
- `n <= m`

### `slice(xs, min, max)`
`slice` takes an iterable `xs` (string or list) and returns a "slice" of the original from the range [`min`, `max`).
The slice is a copy, and mutating it will not mutate the original.

Both `min` and `max` are optional and will default to `0` and `len(xs)` respectively.
```js
name := "Sol David"
slice(name, 0, 3) // "Sol"
```

### `clone(x)`
`clone` takes any Feo value and produces a shallow copy of it that will not mutate if the original mutates.
```js
list := [1, 2, 3]
new_list := clone(list)

[list, _] = pop(list) // list is [1, 2]
new_list // still [1, 2, 3]
```

### `range(start, end, step)`
`range` returns a list of numbers in range [`start`, `end`), incrementing by `step`.
It is analogous to Python's `range` builtin, and will default to `step = 0` and `start = 0` when those optional values are missing.
```js
range(0, 11, 2) // [0, 2, 4, 6, 8, 10]
```

### `reverse(xs)`
`reverse` reverses the order of all elements in a given iterable, producing a copy.
```js
reverse([1, 2, 3]) // [3, 2, 1]
```

### `map(xs, f)`
`map` produces a copy of the given iterable where each element has been put through some mapper predicate `f`.
If `f` is a function, it receives arguments (`element`, `index`).
```js
[1, 2, 3] |> map(func(element, index) element * 5) // [5, 10, 15]
```

### `each(xs, f)`
`each` calls the given iterator function `f` for each element of the given iterable `xs`.
The iterator function receives arguments (`element`, `index`).
```js
[1, 2, 3] |> each(func(element, index) print(element))
// prints "123" to the console
```

### `filter(xs, f)`
`filter` produces an iterable containing only the elements of `xs` that return `true` when passed to the filter predicate `f`.
If `f` is a function, it receives arguments (`element`, `index`).
```js
list := [10, 4, 23, 13, 45] |> filter(func(element, index) element >= 15)
list // [23, 45]
```

### `reduce(xs, seed, f)`
`reduce` accumulates elements of the iterable `xs` on a value, starting with `seed` and passing it to the reducer function `f`.
The reducer receives arguments (`accumulator`, `element`, `index`).
```js
// an example "sum" function implemented with reduce
numbers |> reduce(0) <| func(accumulator, elem) accumulator + elem
```

### `flatten(xs)`
`flatten` takes a list of lists and flattens it to a list of elements. The flattening is only one level deep.
```js
list := [[1, 2, 3], [4, 5], [6, 7]]
flatten(list) // [1, 2, 3, 4, 5, 6, 7]
```

### `append(xs, ys)`
`append` joins two iterable values (strings or lists) together, mutating the first argument `xs`.
If mutation is not desired, use `std.join`.
```js
names := ["Nobu", "Damian"]
append(names, ["Sol", "Thomas"])
names // ["Nobu", "Damian", "Sol", "Thomas"]
```
