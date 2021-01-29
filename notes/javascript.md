- All arguments to a javascript function are optional!

# Scopes
There are two scopes:
- global scope 
- function scope

# Scope chain
    - we first look for a variable in the current scope 
    - then recursively in its parent scopes
    - parent scope is the scope where the function is __defined__, not __executed__!
    - if not found in the `global` scope, the variable is `undefined`


# Types in javascript
- Object Type
- Primitive Types: single, immutable value
    - true, false
    - `undefined`
    - `null`
    - Number type: always represented as `float64`. Integers are just a subset of `Number`
    - Symbol
