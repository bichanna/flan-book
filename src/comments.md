# Comments
Feo allows you to write comments in your code, just like any other languages.

In Feo, comments must start with two slashes and continue until the end of the line. Here's an example of a comment:
```js
// Hello, world!
```

Comments can be also placed at the end of lines containing code:
```js
func do_something(a, b) {
    a(b) // doing something!
}
```

Comments may also be indented:
```js
func multiply(x, y) {
    // multiplying x by y
    x * y
}
```

## Multi-line Comment
For comments that extend beyond a single line, you might want to use multi-line comments that start with `/*` and end with `*/`:
```js
/*
    Hello, world! This is a very very very very very very very
    long comment. I have a lot to say, so much that it will take 
    multiple lines of comments.
*/
```
