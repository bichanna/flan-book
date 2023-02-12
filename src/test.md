## Testing
The `testing` module provides a set of tools for constructing tests.

Here's a simple example to test three functions in `strings` module:
```js
strings := import("strings")
testing := import("testing")

testing.test({
    title: "Test strings module",
    tests: [
        {
            name: "test uppercase",
            test: func(t) {
                result := strings.uppercase("hello, world")
                expected := "HELLO, WORLD"
                testing.assert_equal(result, expected)
            }
        },
        {
            name: "test lowercase",
            test: func(t) {
                result := strings.lowercase("HELLO, WORLD")
                expected := "hello, world"
                testing.assert_true(result == expected)
            }
        },
        {
            name: "test capital",
            test: func(t) {
                result := strings.capital("hello, world")
                expected := "Hello, World"
                testing.assert_equal(result, expected)
            }
        }
    ]
})
```

The `testing` module provides several assert methods to check for and report failures.
The following table lists all the assert functions.

| Function | Checks that |
| ----------- | ----------- |
| `assert_equal(a, b)` | `a == b` |
| `assert_not_equal(a, b)` | `a != b` |
| `assert_true(x)` | `bool(x) == true` |
| `assert_false(x)` | `bool(x) == false` |
| `assert_null(x)` | `x == null` |
| `assert_not_null(x)` | `x != null` |
| `assert_contains(a, b)` | `std.contains?(a, b) == true` |
| `assert_not_contain(a, b)` | `std.contains?(a, b) == false` |
