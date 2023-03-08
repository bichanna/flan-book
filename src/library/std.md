# `std`
`std` module defines basic functions for working with Impala values and functions, iterators, and control flow.

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
 - [`if`](#ifcond-then-else)
 - [`filter`](#filterxs-f)
 - [`reduce`](#reducexs-seed-f)
 - [`flatten`](#flattenxs)
 - [`append`](#appendxs-ys)
 - [`join`](#joinxs-ys)
 - [`zip`](#zipxs-ys-zipper)
 - [`partition`](#partitionxs-by)
 - [`unique`](#uniquexs-pred)
 - [`first`](#firstxs)
 - [`last`](#lastxs)
 - [`take`](#takexs-n)
 - [`take_last`](#take_lastxs-n)
 - [`find`](#findxs-pred)
 - [`rfind`](#rfindxs-pred)
 - [`index_of`](#index_ofxs-x)
 - [`rindex_of`](#rindex_ofxs-x)
 - [`contains?`](#containsxs-x)
 - [`loop`](#loopmax-f)
 - [`aloop`](#aloopmax-f-done)
 - [`sort!`](#sortxs-pred)
 - [`sort`](#sortxs-pred-1)

## `identity(x)`
`identity` returns its first argument.
```js
"Hello" == identity("Hello") // true
```

## `is(x)`
`is` returns a predicate that reports whether its argument is equal to `x`.
```js
f := is(2)
f(2)   // true
f("a") // false
```

## `default(x, base)`
`default` returns `x` if `x` is not `null`, or `base` otherwise. It is useful when taking optional arguments in functions with default values.
```js
func some_func(n, times) {
    // times = 1 by default
    times := default(times, 2)
    // do something
}
```

## `to_hex(n)`
`to_hex` takes a number and returns its hexadecimal representation in a string. It fails for negative values.
```js
to_hex(50159747054) // "BADC0FFEE"
```

## `from_hex(s)`
`from_hex` takes a hexadecimal representation of a number and parses it to an integer. It returns `null` if the input is not a valid hexadecimal number.
```js
from_hex("BADC0FFEE") // 50159747054
```

## `clamp(min, max, n, m)`
`clamp` takes values `n`, `m` and "clamps" or constrains it to the range [`min`, `max`], inclusive. If `n > m`, `n` takes priority and clams `m` down to the lower
value. In the returned value, the following are guaranteed:
- `min <= n <= max`
- `min <= m <= max`
- `n <= m`

## `slice(xs, min, max)`
`slice` takes an iterable `xs` (string or list) and returns a "slice" of the original from the range [`min`, `max`).
The slice is a copy, and mutating it will not mutate the original.

Both `min` and `max` are optional and will default to `0` and `len(xs)` respectively.
```js
name := "Sol David"
slice(name, 0, 3) // "Sol"
```

## `clone(x)`
`clone` takes any Impala value and produces a shallow copy of it that will not mutate if the original mutates.
```js
list := [1, 2, 3]
new_list := clone(list)

[list, _] = pop(list) // list is [1, 2]
new_list // still [1, 2, 3]
```

## `range(start, end, step)`
`range` returns a list of numbers in range [`start`, `end`), incrementing by `step`.
It is analogous to Python's `range` builtin, and will default to `step = 0` and `start = 0` when those optional values are missing.
```js
range(0, 11, 2) // [0, 2, 4, 6, 8, 10]
```

## `reverse(xs)`
`reverse` reverses the order of all elements in a given iterable, producing a copy.
```js
reverse([1, 2, 3]) // [3, 2, 1]
```

## `map(xs, f)`
`map` produces a copy of the given iterable where each element has been put through some mapper predicate `f`.
If `f` is a function, it receives arguments (`element`, `index`).
```js
[1, 2, 3] |> map() <~ (element, index) element * 5 // [5, 10, 15]
```

## `each(xs, f)`
`each` calls the given iterator function `f` for each element of the given iterable `xs`.
The iterator function receives arguments (`element`, `index`).
```js
[1, 2, 3] |> each() <~ (element, index) print(element)
// prints "123" to the console
```

## `if(cond, then, else)`
When `cond` is `true`, predicate `then` gets called. When `cond` is `false`, predicate `else` gets called.
```js
if("abc" == "abc", -> {
    println("gets executed")
}) <~ () {
    println("don't get executed")
}
```


## `filter(xs, f)`
`filter` produces an iterable containing only the elements of `xs` that return `true` when passed to the filter predicate `f`.
If `f` is a function, it receives arguments (`element`, `index`).
```js
list := [10, 4, 23, 13, 45] |> filter() <~ (element, index) element >= 15
list // [23, 45]
```

## `reduce(xs, seed, f)`
`reduce` accumulates elements of the iterable `xs` on a value, starting with `seed` and passing it to the reducer function `f`.
The reducer receives arguments (`accumulator`, `element`, `index`).
```js
// an example "sum" function implemented with reduce
numbers |> reduce(0) <~ (accumulator, elem) accumulator + elem
```

## `flatten(xs)`
`flatten` takes a list of lists and flattens it to a list of elements. The flattening is only one level deep.
```js
list := [[1, 2, 3], [4, 5], [6, 7]]
flatten(list) // [1, 2, 3, 4, 5, 6, 7]
```

## `append(xs, ys)`
`append` joins two iterable values (strings or lists) together, mutating the first argument `xs`.
If mutation is not desired, use `std.join`.
```js
names := ["Nobu", "Damian"]
append(names, ["Sol", "Thomas"])
names // ["Nobu", "Damian", "Sol", "Thomas"]
```

## `join(xs, ys)`
`join` joins two iterable values (strings or lists) together, while mutating neither values. If efficiency is desired, used `std.append`.
```js
names := ["Nobu", "Damian"]
join(names, ["Sol", "Thomas"]) // ["Nobu", "Damian", "Sol", "Thomas"]
names // ["Nobu", "Damian"], not mutated
```

## `zip(xs, ys, zipper)`
`zip` "zips" together each pair of items from two iterables. If the zipper function is not given, each pair of items are put into a 2-element list.
Otherwise, `zipper` is called on each pair of items and the result is placed into the resulting list.
```js
zip([1, 2, 3], [4, 5, 6]) // => [[1, 2], [3, 4], [5, 6]]

zip([1, 2, 3], [4, 5, 6], fn(a, b) a * b) // => [4, 10, 18]
```

## `partition(xs, by)`
`partition` divides the sequence of items in the iterable `xs` into a list of lists (partitions).

If `by` is an integer, each partition will contain that number of items. If `by` is a function, the partition will be cut anywhere the result of the function changes from one item to the next. For any other values of `by`, partition returns null.
```js
list := [1, 2, 3, 4, 5, 6]
partition(list, 3) // [[1, 2, 3], [4, 5, 6]]
```

## `unique(xs, pred)`
`unique` takes a list `xs`, and returns a similar list where no element of `xs` occurs twice in a row.
Elements may occur twice in the list if they are separated by other elements.
`unique` takes an optional `pred` predicate, by which elements' equality may be compared. `unique` runs in `O(n)` time.
```js
list := [1, 1, 2, 2, 3]
unique(list) // [1, 2, 3]
```

## `first(xs)`
`first` returns the first item in an iterable. It's trivial, but useful to have in the stdlib for use in pipelines or iterators.
```js
name := "Nobu"
first(name) // "N"
```

## `last(xs)`
`last` returns the last item in an iterable. It's trivial, but useful to have in the stdlib for use in pipelines or iterators.
```js
name := "Nobu"
last(name) // "u"
```

## `take(xs, n)`
`take` accepts an iterable and returns a version of it containing the first N elements.
```js
email := "nobu.bichanna@gmail.com"
take(email, 4) // "nobu"
```

## `take_last(xs, n)`
`take_last` accepts an iterable and returns a version of it containing the last N elements.
```js
email := "nobu.bichanna@gmail.com"
take_last(email, 9) // "gmail.com"
```

## `find(xs, pred)`
`find` returns the index of the first item in the iterable `xs` for which the predicate returns `true`. If no match is found, find returns `-1`.
```js
nobu? := is("Nobu")
names := ["Sol", "Nobu", "Damian", "Thomas", "Maks", "Nobu"]
find(names, nobu?) // 1
```

## `rfind(xs, pred)`
`rfind` returns the index of the last item in the iterable `xs` for which the predicate returns `true`, searching backwards from the end.
If no match is found, `rfind` returns `-1`.
```js
nobu? := is("Nobu")
names := ["Sol", "Nobu", "Damian", "Thomas", "Maks", "Nobu"]
rfind(names, nobu?) // 5
```

## `index_of(xs, x)`
`index_of` returns the index of the first item equal to `x` in the iterable `xs`. If no match is found, `index_of` returns `-1`.
```js
names := ["Sol", "Nobu", "Damian", "Thomas", "Maks", "Nobu"]
index_of(names, "Nobu") // 1
```

## `rindex_of(xs, x)`
// `rindex_of` returns the index of the last item equal to `x` in the iterable `xs`, searching backwards from the end. If no match is found, `rindex_of` returns `-1`.
```js
names := ["Sol", "Nobu", "Damian", "Thomas", "Maks", "Nobu"]
index_of(names, "Nobu") // 5
```

## `contains?(xs, x)`
`contains?` reports whether an iterable contains an item equal to `x`.
```js
names := ["Sol", "Nobu", "Damian", "Thomas", "Maks", "Nobu"]
contains?(names, "Nobu") // true
```

## `loop(max, f)`
`loop` takes a loop count `max` and a callback, and invokes the callback `max` times.
It can be used to infinitely loop if `max < 0`. Callback is called with two arguments:
- `count`: the current loop count starting from `0`
- `breaker`: a function to be called to exit early from the loop, which takes an optional return value to be returned by the `loop()` call
```js
loop(100) <~ (count, breaker) { // prints "Hello, world!" to the console 100 times
    println("Hello, world!")
}
```

## `aloop(max, f, done)`
`aloop` takes a loop count `max` and a callback, and invokes the callback `max` times *asynchronously*.
It can be used to infinitely loop if `max < 0`. Callback is called with three arguments:
- count: the current loop count starting from `0`
- next: a function to be called when the current iteration is done
- done: a function to be called to exit early from the loop
```js
aloop(100) <~ (count, next, done) {
    // do something...
    next()
}
```

## `sort!(xs, pred)`
`sort!` sorts items in the list `xs` by each item's `pred` value, using the Hoare partitioning strategy. If `pred` is not given, each item is sorted by its own value.
It mutates the original list for efficiency. If mutation is not desired, use sort below.
```js
list := [3, 4, 2, 5, 1]
sort!(list)
list // [1, 2, 3, 4, 5]
```

## `sort(xs, pred)`
`sort` returns a copy of `xs` that is sorted by `pred`, or by each item's value if `pred` is not given.
If the performance cost of a copy is not desirable, use `sort!`.
```js
list := [3, 4, 2, 5, 1]
list = sort(list)
list // [1, 2, 3, 4, 5]
```
