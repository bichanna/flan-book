# `strings`
`strings` module provides a set of utility functions for working with strings and data encoded in strings in Impala programs.

 - [`upper?`](#upperc)
 - [`upper`](#uppers)
 - [`lower?`](#lowerc)
 - [`lower`](#lowers)
 - [`digit?`](#digitc)
 - [`space?`](#spacec)
 - [`letter?`](#letterc)
 - [`word?`](#wordc)
 - [`join`](#joinstrings-joiner)
 - [`starts_with?`](#starts_withs-prefix)
 - [`ends_with?`](#ends_withs_suffix)
 - [`index_of`](#index_ofs-substr)
 - [`rindex_of`](#rindex_ofs-substr)
 - [`contains?`](#containss-substr)
 - [`replace`](#replaces-old-new)
 - [`split`](#splits-sep)
 - [`pad_start`](#pad_starts-n-pad)
 - [`pad_end`](#pad_ends-n-pad)
 - [`trim_start`](#trim_starts-prefix)
 - [`trim_end`](#trim_ends-suffix)
 - [`trim`](#trims-part)

## `upper?(c)`
`upper?` reports whether a given char is an uppercase ASCII letter.
```js
upper?("a") // false
upper?("A") // true
```

## `upper(s)`
`upper` returns the uppercase string from the given string `s`.
```js
upper("nobu") // "NOBU"
```

## `lower?(c)`
`lower?` reports whether a given char is a lowercase ASCII letter.
```js
lower?("a") // true
lower?("A") // false
```

## `lower(s)`
`lower` returns the lowercase string from the given string `s`.
```js
lower("NOBU") // "nobu"
```

## `digit?(c)`
`digit?` reports whether a given char is an ASCII digit.
```js
digit?("1") // true
digit?("a") // false
```

## `space?(c)`
`space?` reports whether a given char is an ASCII whitespace.
```js
space?("\n") // true
space?("a") // false
```

## `letter?(c)`
`letter?` reports whether a given char is an ASCII letter.
```js
letter?("a") // true
letter?("A") // true
```

## `word?(c)`
`word?` reports whether a given char is a letter or a digit.
```js
word?("1") // true
word?("a") // true
```

## `join(strings, joiner)`
`join` concatenates together a list of strings into a single string, where each original string in the list is separated by `joiner`.
Joiner is the empty string by default.
```js
join(["Nobu", "Shimazu"], " ") // "Nobu Shimazu"
```

## `starts_with?(s, prefix)`
`starts_with?` reports whether a string starts with the substring `prefix`.
```js
starts_with?("abcdefg", "abc") // true
```

## `ends_with?(s, suffix)`
`ends_with?` reports whether a string ends with the substring `suffix`.
```js
ends_with?("abcdefg", "efg") // true
```

## `index_of(s, substr)`
`index_of` returns the first index at which the given substring `substr` appears in the string `s`. If the substring does not exist, it returns `-1`.
```js
index_of("nobu.bichanna@gmail.com", "bichanna") // 5
```

## `rindex_of(s, substr)`
`rindex_of` returns the last index at which the given substring `substr` appears in the string `s`. If the substring does not exist, it returns `-1`.
```js
rindex_of("nobu.bichanna@gmail.com", "a") // 16 
```

## `contains?(s, substr)`
`contains?` reports whether the string `s` contains the substring `substr`.
```js
contains?("nobu.bichanna@gmail.com", "com") // true
contains?("nobu.bichanna@gmail.com", "asd") // false
```

## `replace(s, old, new)`
`replace` returns a string where all occurrences of the substring `old` has been replaced by `new` in the string `s`. It does nothing for empty strings.
```js
replace("catcatcat", "t", "ts") // "catscatscats"
```

## `split(s, sep)`
`split` splits the string `s` by every occurrence of the substring `sep` in it, and returns the result as a list of strings.
If `sep` is not specified, split returns a list of every character in the string in order.
```js
split("blah blah blah", " ") // ["blah", "blah", "blah"]
```

## `pad_start(s, n, pad)`
`pad_start` prepends the string `s` with one or more repetitions of pad until the total string is at least `n` characters long. If `len(s) > n`, it returns `s`.
```js
pad_start("hello", 2, "-") // "--hello"
```

## `pad_end(s, n, pad)`
`trim_end` removes any (potentially repeated) occurrences of the string `suffix` from the end of string `s`.
```js
pad_end("hello", 2, "-") // "hello--"
```

## `trim_start(s, prefix)`
`trim_start` removes any (potentially repeated) occurrences of the string `prefix` from the beginning of string `s`.
```js
trim_start("Nobuharu", "Nobu") // "haru"
```
## `trim_end(s, suffix)`
`trim_end` removes any (potentially repeated) occurrences of the string `suffix` from the end of string `s`.
```js
trim_end("Nobuharu", "ru") // "Nobuha"
```

## `trim(s, part)`
`trim` removes any (potentially repeated) ocucrrences of the string `part` from either end of the string `s`.
If `part` is not specified, trim removes all whitespace from either end of the string `s`.
```js
trim("  Hello  ") // "Hello"
```
