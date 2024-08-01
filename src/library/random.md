# `random`
`random` module implements pseudo-random number generators for various distributions.

Almost all module functions depend on the basic function [`random`](#random), which generates a random float uniformly in the half-open range `0.0 <= x < 1.0`.

*Warning*: The pseudo-random generators of this module should not be used for security purposes.

 - [`random`](#random)
 - [`random_range`](#random_rangestart-stop-step)
 - [`choice`](#choicexs)
 - [`shuffle`](#shufflexs)

## `random()`
`random` returns the next random floating point number in the range `0.0 <= x < 1.0`.
```js
random() // 0.09731976238249829
```

## `random_range(start, end, step)`
`random_range`returns a randomly selected element from [`range(start, end, step)`](./std.md#rangestart-end-step).
```js
random_range(2, 10, 2) // 6
```

## `choice(xs)`
`choice` returns a random element from the non-empty list `xs`.
```js
choice(["Nobu", "Anna", "Thomas", "Damian"]) // "Anna"
```

## `shuffle(xs)`
`shuffle` shuffles a sequence `xs` and returns a new shuffled list.
```js
shuffle(["Nobu", "Anna", "Thomas", "Damian"]) // ["Thomas", "Damian", "Anna", "Nobu"]
```
