# Deep JS Foundations

## Types

### Primitive Types

"In JavaScript, everything is an object." - false

ECMAScript Language Primitive Types

- **undefined** - only value is undefined
- **null**
- **string** - string literal
- **number** - all JS numbers
- **bigint**
- **boolean** - true and false
- **symbol** - used to create pseudo private/obscure keys on objects

object

- functions are callable objects (subtype)
- arrays are a subtype of objects with numerical indexing

### typeof Operator

In JavaScript, variables don't have types, values do. We aren't asking the type of a variable, we're asking the type of the value. tyoeof will return a string.

```
var v
typeof v // "undefined"
v = "1" // string
v = 2 // number
v = true // boolean
v = {} // object
v = Symbol() // symbol

// Weird situations

v = null; // object - historically undefined for resetting primitive types, null for resetting objects
v = function(){} // function
v = [1, 2, 3] // object - instead Array.isArray(arr)
```

- Abstract Operations
- Coercion
- Equality
- TypeScript, Flow, etc.

## Scope

- Nested Scope
- Hoisting
- Closure
- Modules

## Objects (Oriented)

- this
- class { }
- Prototypes
- OO vs. OLOO
