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

### BigInt

Integer that can grow infinitely large (limited by memory of system). Don't mix that well with regular numbers.

```
var v = 42n
// or
var v = BigInt(42)
typeof v // "bigint"
```

- Abstract Operations
- Coercion
- Equality
- TypeScript, Flow, etc.

### undefined vs. undeclared

- Undeclared - never been created in any scope we have access to
- Undefined - Variable that has been initialized - there is a variable, but at the moment it has no value
- Uninitialized (TDZ - temporal dead zone) - Variable that has never been initialized - certain variables (block scoped ones for example) don't get initialized
  - If you access `var` before it's declared, it is `undefined`. But if you do the same for `let` and `const`, they throw a `ReferenceError`.

typeof - only operator that can reference something that doesn't exist without throwing an error

### Special Values: `NaN` and `isNaN`

`NaN`

- Not a Number
- actually is a sentinal value that indicates an invalid number
  - A sentinel value is a special value in the context of an algorithm which uses its presence as a condition of termination, typically in a loop or recursive algorithm
- Propogates all the way out, NaN combined with any number is NaN
- `NaN` !== `NaN` - NaNs aren't equal to each other. Only value in JS that doesn't have the identity property - means it is not equal to itself
- `typeof NaN === 'number'` - NaN is an invalid number

`isNaN`

```
var n = Number('regular string') // NaN
isNaN(n) // true
isNaN('regular string') // true
```

- In the second example, the string is not NaN yet we are getting `true`. The `isNaN` utility coerces values to numbers before it checks if it is NaN.

`Number.isNaN`

```
var n = Number('regular string') // NaN
isNaN(n) // true
isNaN('regular string') // false
```

- `Number.isNaN` tells us whether we are feeding in the NaN value (no coercion done)

### Special Values: Negative Zero

- Zero value with the sign bit on it
- Early JS hid negative zero from developers

```
var trendRate = -0

// weird cases
trendRate === -0 // true
trendRate === 0 // true
trendRate.toString() // 0
trendRate < 0 // false
trendRate > 0 // false
```

- Starting in ES6 we got a way to determine negative zero: `Object.is` (colloquially a quadruple equals)

```
Object.is(trendRate, -0) // true
Object.is(trendRate, 0) // false
```

- Theoretical reason to use negative 0: Mathematically the absolute value could represent speed, sign could represent direction (when car stops make it look the same direction as before it stops)

### Fundamental Objects

aka: Built-In Objects, Native Functions

Bolted on object-orientedness of JS.

Use new:

- Object()
- Array()
- Function()
- Date()
- RegExp()
- Error()

Don't use new:

- String()
- Number()
- Boolean()
  Use as function to coerce value to that primitive type, not a constructor

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
