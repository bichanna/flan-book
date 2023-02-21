# Strings And Atoms

## Strings
In Feo, strings can be written as text surrounded by double quotes.
```js
"This is a string"
```

Also, they can span multiple lines.
```js
"Multi-line
string!"
```

Under the hood, strings are just Rust `String`s, which are encoded with [UTF-8](https://en.wikipedia.org/wiki/UTF-8), and are able to contain any valid unicode.
```js
"🖕🏻こんにちはFeo 👺"
```

### Concatenation
The addition operator can be used to join strings together, but not atoms:
```js
name = "Nobu"
name + "haru" // "Nobuharu"
```

### Escape Sequences
Feo supports common string escape sequences. Here's all of them:

| Sequences | Result |
| ----------- | ----------- |
| \n | Newline |
| \r | Carriage Return |
| \t | Tab |
| \\" | Double Quote |
| \\\ | Backslash |
| \0 | Null Terminator |

For example, to include double quote (`"`) character in a string literal, it must be escaped by placing a backslash (`\`) character before it.
```js
"Here's a double quote: \""
```
Another example:
```js
// A Windows filepath C:\Users\Nobu
"C:\\Users\\Nobu"
```

## Atoms
For immutable strings, use atoms:
```js
:some_atom
```
