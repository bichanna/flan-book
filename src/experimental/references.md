# References
A reference is a name that refers to the specific location in memory of a value.
References take the form of variables and attributes.

```js
{println: fprintln} := import("fmt")

func swap(a, b) {
    tmp := deref a // *a in C
    a <- deref b
    b <- tmp
}

a := 1
b := 2
swap(ref a, ref b) // swap(&a, &b) in C

fprintln("a = {} and b = {}") // "a = 2 and b = 1"
```

Keywords introduced in the snippet above are `ref`, `deref`, and `<-`:
 - `ref` returns the reference of the expression.
 - `deref` returns the value of the reference.
 - `<-` assigns a value (not a reference) to the address the reference is referring to.
