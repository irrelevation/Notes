# You don't know JS

## Some interesting bits

- `null` is of type `Object`
- An ES6 module is a singleton.
- `for..of` and the spread operator `...` consume iterators. They can be used with _iterables_ as well.
  In that case the iterator protocol creates an iterator instance from the iterable, that will be used for consumption.
- The enclosing scope of a closure doesn't have to be a function.

## Scope & Closure

The _definition context_ of a function is called its scope. A function is attached to its scope via closure.
The scope determines how references to variables are resolved.
Scope is **static**: It contains the fixed set of variables available at the location and time of function definition.
Scopes can be nested inside each other. Inside a scope only variables from that scope or higher out scopes are available.
This is called **lexical scope**.

## `this`

The _execution context_ of a function can be accessed via its `this` keyword.
It is **dynamic**, dependant on _how_ it is called, regardless _where_ it is defined or called.

## Prototypes

Prototypes determine the resolution of property access. Prototypes link an object on creation to another existing object.
A series of objects that are linked via prototypes is called the **prototype chain**. Property and method access is delegated along the prototype chain.
