# `Testing`
`testing` is a testing library for Impala, and it provides a set of tools for constructing tests.

 - [`run`](#runtest_obj)
 - [`assert_equal`](#assert_equala-b)
 - [`assert_not_equal`](#assert_not_equala-b)
 - [`assert_true`](#assert_truex)
 - [`assert_false`](#assert_falsex)
 - [`assert_null`](#assert_nullx)
 - [`assert_not_null`](#assert_not_nullx)
 - [`assert_contains`](#assert_containsa-b)
 - [`assert_not_contain`](#assert_not_containa-b)
 - [`assert_error`](#assert_errora-t-msg)

## `run(test_obj)`
`run` tests the given `test_obj` object.

The `test_obj` is an object that looks like this:
```js
{
    // The title of the test suite
    title: "The title of this particular test suite",
    // The function that is executed once before all tests and returns
    // an object that is passed to all tests as an argument
    setup: func() {
        { name: "Nobu" }
    }
    // The function that is executed once after all tests are run
    cleanup: func(t) { // t is an object that is created in the setup function
        // clean up something
    }
    // A list of smaller test chunks
    tests: [
        {
            // The title of this small test chunk
            name: "The name of this test",
            // The function that tests something
            test: func(t) {
                // test something
            }
        }
    ]
}
```

## `assert_equal(a, b)`
`assert_equal` tests that `a` and `b` are equal. If the values do not compare equal, the test will fail.
```js
assert_equal("abc", "abc") // checks that "abc" == "abc"
```

## `assert_not_equal(a, b)`
`assert_not_equal` tests that `a` and `b` are not equal. If the values do compare equal, the test will fail.
```js
assert_not_equal("abc", "ABC") // checks that "abc" != "ABC"
```

## `assert_true(x)`
`assert_true` tests that `x` is `true`.
```js
assert_true(some_func()) // checks that some_func() == true
```

## `assert_false(x)`
`assert_false` tests that `x` is `false`.
```js
assert_false(some_func()) // checks that some_func() == false
```

## `assert_null(x)`
`assert_null` tests that `x` is `null`.
```js
assert_null(some_func()) // checks that some_func() == null
```

## `assert_not_null(x)`
```js
assert_not_null(some_func()) // checks that some_func() != null
```

## `assert_contains(a, b)`
```js
assert_contains(["a", "b", "c"], "c") // checks if ["a", "b", "c"] contains "c"
```

## `assert_not_contain(a, b)`
```js
assert_not_contain(
    ["a", "b", "c"],
    "d"
) // checks if ["a", "b", "c"] doesn't contains "d"
```

## `assert_error(a, t, msg)`
```js
assert_error(
    some_func(),
    :error_type,
    "error message"
) // checks if unsafe some_func() == error(:error_type, "error_message")
```
