# `math`
For functions dealing with coordinate pairs and angles, the coordinate plane is assumed to be a Cartesian plane with +x to the east and +y to the north,
where the angle is measured in radians from the +x axis, counterclockwise.

 - [`PI`](#pi)
 - [`E`](#e)
 - [`sign`](#signn)
 - [`abs`](#absn)
 - [`sqrt`](#sqrtn)
 - [`hypot`](#hypotx0-y0-x1-y1)
 - [`scale`](#scalex-a-b-c-d)
 - [`comb`](#combn-k)
 - [`sum`](#sumxs)
 - [`prod`](#prodxs)
 - [`min`](#minxs)
 - [`max`](#maxxs)
 - [`clamp`](#clampx-a-b)
 - [`mean`](#meanxs)
 - [`median`](#medianxs)
 - [`std_dev`](#std_devxs)
 - [`round`](#roundn-decimals)

## `PI`
π, the circle constant.
```js
PI := 3.14159265358979323846264338327950288419716939937510
```

## `E`
e, the base of the natural logarith.
```js
e := 2.71828182845904523536028747135266249775724709369995
```

## `sign(n)`
`sign` returns `-1` for all negative numbers, and `1` otherwise.
```js
sign(4)  // 1
sign(-3) // -1
```

## `abs(n)`
`abs` returns the absolute value of a real number.
```js
abs(-123) // 123
abs(123)  // 123
```

## `sqrt(n)`
`sqrt` returns the principal square root of a real number, or `null` if the number is negative.
```js
sqrt(64) // 8
sqrt(-64) // null
```

## `hypot(x0, y0, x1, y1)`
`hypot` returns the Euclidean distance between two points, equivalent to the hypotenuse of a right triangle with the given two points as vertices.
If `x1` and `y1` default to `0`.
```js
hypot(3, 4) // 5
```

## `scale(x, a, b, c, d)`
`scale` maps the value `x` in the range `[a, b]` to the range `[c, d]`. If `[c, d]` are not provided, they are assumed to be `[0, 1]`.
`x` may be outside the range `[a, b]`, in which case the value is scaled to be an equal amount outside of the range `[c, d]`.

## `comb(n, k)`
`comb` returns the number of ways to choose `k` items from `n` items without repetition and without order. If `k > n`, `comb` returns `0`.
```js
comb(4, 1) // 4
```

## `sum(xs)`
`sum` takes a list of values and returns their sum.
```js
sum([1, 2, 3, 4]) // 10
```

## `prod(xs)`
`prod` takes a list of values and returns their product.
```js
prod([1, 2, 3, 4]) // 24
```

## `min(xs)`
`min` takes a list of values and returns the minimum value in the list.
```js
min([2, 4, 3, 5, 6, 1]) // 1
```

## `max(xs)`
`max` takes a list of values and returns the maximum value in the list.
```js
max([2, 4, 3, 5, 6, 1]) // 6
```

## `clamp(x, a, b)`
`clamp` returns a value bounded by some upper and lower bounds `a` and `b`.
If the given `x` is between `a` and `b`, it is returned as-is, and if it is outside the bounds, the closer of the two bounds is returned.
```js
clamp(5, 3, 8) // 5
clamp(2, 3, 8) // 3
clamp(9, 3, 8) // 8
```

## `mean(xs)`
`mean` returns the arithmetic mean, or average, of all given values. If the list is empty, mean returns `null`.
```js
mean([2, 3, 4]) // 3
```

## `median(xs)`
`median` returns the median, or "middle value", of all given values.
If there is an even number of values given, median computes the mean of the middle two values in the list. If the list is empty, median returns `null`.
```js
median([3, 4, 1, 7, 5]) // 4
```

## `std_dev(xs)`
`std_dev` returns the population standard deviation computed from the given list of values. If the list is empty, `std_dev` returns `null`.

## `round(n, decimals)`
`round` takes a number `n` and returns a floating-point number that represents `n` round to the nearest `decimals`-th decimal place.
For negative values of `decimals`, no rounding occurs and `n` is returned exactly.
```js
round(PI, 2) // 3.14
```
