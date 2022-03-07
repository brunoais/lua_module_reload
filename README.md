# Module reload for LUA

Initially designed for transport fever but may work with any other instance of embedded LUA executino environment.

# Usage



### Import this module normally

`require "modules"`

At the top of the file

### Replace your calls to require for your code

In all instances you use the `require` function in your code, such as:

```
local main = require "main"

```

Replace them with:

```
local main = modules.tryRequire("main")
```

When you are developing or bugfixing, you can then activate reloading by calling:

`modules.defaultAllReload()`

After that, all calls to `modules.tryRequire("main")` will load a fresh version of the `main` module or will cause a print to console explaining the why the require failed (e.g. syntax errors).

If you don't want a certain module to ever reload or vice-versa, you can call `modules.registerReload("main", false)`, so the module doesn't load
unless it requests to load explicitely.

Requesting to reload explicitely is done by calling `modules.tryRequire("main", true)`

**Note:** Reloading a module **does not** cause it's required modules to reload. The workaround is to call `modules.defaultAllReload()`, then `modules.tryRequire("main")`, then `modules.defaultNoneReload()`

# License

Code license is under a slightly modified Apache license 2.0. The slight modification legally binds you to give credit if you use the software.
