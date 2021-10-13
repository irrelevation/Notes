# JavaScript Basics

## Loading Javascript Files

Use the `defer` or `async` keyword to load JavScript concurrently to parsing the HTML file. `async` will execute scripts as soon as they are available. `defer`will defer the execution of scripts until parsing of the HTML file has completed and will preserve execution order of the scripts:

```html
<script src="javascript.js" defer></script>
<script src="javascript.js" async></script>
```

## Reference vs Value

Objects and arrays are compared by reference. Other primitive types are compared by value. Same goes for passing parameters to a function.

## Nullish Coalescing

The nullish coalescing operator `a ?? b`returns `b` if `a` is null or undefined.

## Logical Nullish Assignment

The logical nullish assignment operator `a ??= b` only assigns if `a` is nullish.

## Optional Chaining

The `?.`optional chaining operator works like `.`the normal chaining operator except it doesn't raise an error but short circuits returning `undefined` if the object you are trying to access doesn't exist. This gets rid of a lot of `&&`chaining. There are several use cases:

```javascript
obj.val?.prop
obj.val?.[expr]
obj.arr?.[index]
obj.func?.(args)
```

## Spreading & Destructuring

```javascript
# This will overwrite object1 with object2's properties
const newObject = {oject1..., object2...};

const [element0, element1, ...rest] = someArray;
const {key1, key2: newName, key3 = fallbackValue, ...rest} = someObject;
```

 You can nest destructuring syntax.
