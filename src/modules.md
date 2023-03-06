# Modules
In Impala, modules are simply files with the “.impl” extension containing Impala code that can be imported inside another Impala program.
Functions annotated with `public` keyword are public functions, meaning they could be exported outside of their own module to be used by other modules.

You can import other modules using the built-in `import` function with relative paths.
```js
// src/a_module.impala

// public function func_in_a
public func func_in_a() {
    "Hello from a_module"
}
```
Here, we have a function `func_in_a` in module `src/a_module`.

From module `src/entry`, you can import the module `src/a_module` like this.
```js
// src/entry.impl

a_mod := import("src/a_module")

a_mod.func_in_a() // "Hello from a_module"
```

You can similarly import the module `src/a_module` from another module `src/directory/b_module`, relative to the `src/entry` module.
```js
// src/directory/b_module.impl

a_mod := import("src/a_module")

a_mod.func_in_a() // "Hello from a_module"
```


Because `import` function returns an object containing public variables and functions, you can import specific functions like so:
```js
// src/entry.impl

{func_in_a: func_from_a} := import("src/a_module")

func_from_a() // "Hello from a_module"
```
