# `json`
`json` module implements a JSON parser and serializer for Feo values.

 - [`escape_char`](#escape_charc)
 - [`escape`](#escapes)
 - [`serialize`](#serializec)
 - [`parse`](#parses)

## `escape_char(c)`
string escape '"'
```js
escape_char("   ") // "\\t"
```

## `escape(s)`
escapes whole string
```js
escape("Hello\nWorld") // "Hello\\nWorld"
```

## `serialize(c)`
`serialize` takes a Feo value and returns its JSON representation.
```js
obj := {
    name: "nobu",
    email: "nobu.bichanna@gmail.com",
    cool?: true,
    siblings: 1
}
serialize(obj)
/*
    {
        "name": "nobu",
        "email": "nobu.bichanna@gmail.com",
        "is_cool": true,
        "siblings": 1
    }
*/
```

## `parse(s)`
`parse` takes a potentially valid JSON string, and returns its Feo representation if valid JSON, or throws an error if the parse fails.
```js
parse("{\"name\": \"nobu\", \"is_cool\": true}")
/*
    {
        name: "nobu",
        is_cool: true
    }
*/
```
