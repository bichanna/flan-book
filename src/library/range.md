# `range`
`range` module implements functions for working with memory efficient iterators.

 - [`range`](#rangestart-stop-step)
 - [`each`](#eachr-f)
 - [`map`](#mapr-f)
 - [`reverse`](#reverser)
 - [`filter`](#filterr-f)
 - [`reduce`](#reducer-seed-f)
 - [`slice`](#slicer-min-max)
 - [`list`](#listr)

## `range(start, stop, step)`
`range` returns a range object of numbers in range `[start, end)`, incrementing by `step`.
It is analogous to Python's `range` builtin function, and will default to `step = 0` and `start = 0` when those optional values are missing.
```js
range(1, 100000)
/*
    {
        start: 1,
        stop: 100000,
        step: 1,
    }
*/
```

## `each(r, f)`
`each` calls the given iterator function `f` for each element of the given range object `r`.
The iterator function receives arguments `(element, index)`.
```js
range(1, 2000) |> each() <~ (element, index)
    println(element)
```

## `map(r, f)`
`map` produces a list of the given range object `r` where each element has been put through some mapper predicate `f`.
If `f` is a function, it receives arguments `(element, index)`.
```js
range(0, 2000) |> map() <~ (element, index)
    element * index
// [0, 1, 4, ..., 3996001]
```

## `reverse(r)`
`reverse` reverses the order of all elements in a given range object `r`, producing a copy.
```js
reverse(range(1, 4000))
/*
    {
        start: 4000,
        stop: 1,
        step: -1,
    }
*/
```

## `filter(r, f)`
`filter` produces an iterable containing only the elements of the range object `r` that return `true` when passed to the filter predicate `f`.
If `f` is a function, it receives arguments `(element, index)`.
```js
list := range(0, 100) |> filter() <~ (element, index) element >= 90
list // [90, 91, 92, 93, 94, 95, 96, 96, 97, 98, 99]
```

## `reduce(r, seed, f)`
`reduce` accumulates elements of the range object `r` on a value, starting with `seed` and passing it to the reducer function `f`.
The reducer receives arguments `(accumulator, element, index)`.
```js
// example "sum" function
func sum(start, stop, step) {
    step = default(step, 1)
    range.range(start, stop, step) |> range.reduce(0) <~ (acc, elem) acc + elem
}
```

## `slice(r, min, max)`
`slice` takes a range object `r` and returns a "slice" (list) of the original from the range `[min, max)`.
The slice is a copy, and mutating it will not mutate the original.

Both `min` and `max` are optional and will default to `0` and `len(xs)` respectively.
```js
slice(range(0, 100), 5, 11) // [6, 7, 8, 9, 10]
```

## `list(r)`
`list` takes a range object `r` and returns a list version of the range.
```js
range(0, 100) |> list() // [0, 1, 2, ..., 98, 99]
```
