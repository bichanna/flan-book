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
                t.assert_equal(result, expected)
            }
        },
        {
            name: "test lowercase",
            test: func(t) {
                result := strings.lowercase("HELLO, WORLD")
                expected := "hello, world"
                t.assert_true(result == expected)
            }
        },
        {
            name: "test capital",
            test: func(t) {
                result := strings.capital("hello, world")
                expected := "Hello, World"
                t.assert_equal(result, expected)
            }
        }
    ]
})
```
