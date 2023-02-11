# Modules
In Feo, Modules are simply files with the “.feo” extension containing Feo code that can be imported inside another Feo program.
You can import other modules using the built-in `import` function with relative paths.
```js
// src/a_module.feo

pub func func_in_a() {
    "Hello from a_module"
}
```
Here, we have a function `func_in_a` in module `src/a_module`.

From module `src/entry`, you can import the module `src/a_module` like this.
```js
// src/entry.feo

a_mod := import("src/a_module")

a_mod.func_in_a() // "Hello from a_module"
```

You can similarly import the module `src/a_module` from another module `src/directory/b_module`, relative to the `src/entry` module.
```js
// src/directory/b_module.feo

a_mod := import("src/a_module")

a_mod.func_in_a() // "Hello from a_module"
```


Because `import` function returns an object containing public variables and functions, you can import specific functions like so:
```js
// src/entry.feo

{func_in_a: func_from_a} := import("src/a_module")

func_from_a() // "Hello from a_module"
```
