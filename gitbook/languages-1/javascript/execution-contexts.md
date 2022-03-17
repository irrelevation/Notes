# JavaScript Execution Contexts

| Global execution context | Function execution context |
| --- | --- |
| Creates a Global Variable object that stores function and variables declarations	| Doesn't create a Global Variable object. Rather, it creates an argument object that stores all the arguments passed to the function |
| Creates the `this` object that stores all the variables and functions in the Global scope as methods and properties	| Doesn't create the `this` object, but has access to that of the environment in which it is defined. Usually the `window` object |
| Can't access the code of the Function contexts defined in it	| Due to scoping, has access to the code(variables and functions) in the context it is defined and that of its parents |
| Sets up memory space for variables and functions defined globally	| Sets up memory space only for variables and functions defined within the functio. |

## Resources

- [Excellent article](https://www.freecodecamp.org/news/execution-context-how-javascript-works-behind-the-scenes)
