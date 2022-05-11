# The Document Object Model

The DOM is a tree data structure. It consists of nodes. There are different types of nodes like element-nodes, text-nodes, attribute-nodes and comment-nodes.

## DOM Manipulation

| Code                                                                                                         | Function                                                                                    |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------- |
| [`Node.appendChild(node)`](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)                | Appends a node                                                                              |
| [`Node.append(...nodesOrDOMStrings)`](https://developer.mozilla.org/en-US/docs/Web/API/Element/append)       | Appends one or more nodes or text                                                           |
| [`document.createElement(tagName)`](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement) | Creates an element                                                                          |
| [`Element.innerText`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/innerText)                | Sets the text. Gets the visible Text                                                        |
| [`Element.textContent`](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)                   | Sets the text. Gets the text as per html (including invisible elements)                     |
| [`Element.innerHTML = <string>`](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)         | Sets or gets the HTML contained in the element<br />WARNING: Danger of Cross Site Scripting |
| [`Element.remove()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/remove)                        | Removes the element from the DOM tree                                                       |
| [`Node.removeChild(child)`](https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild)               | Removes a child Element from the DOM tree                                                   |
| [`Element.getAttrribute(name)`](https://developer.mozilla.org/en-US/docs/Web/API/Element/getAttribute)       | Gets the value of an attribute                                                              |
| `Element.attributeName`                                                                                      | Gets the value of an attribute                                                              |
| [`Element.setAttribute(name, value)`](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute) | Sets the value of the specified attribute                                                   |
| `Element.attributeName` = value                                                                              | Sets the value of the specified attribute                                                   |
| [`Element.removeAttribute(name)`](https://developer.mozilla.org/en-US/docs/Web/API/Element/removeAttribute)  | Removes the specified attribute                                                             |
| [`Element.classList`](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)                    | Read only property to get class attributes as a list instead of a string                    |
| [`Element.classList.add()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)              | Add a class                                                                                 |
| [`Element.classList.remove()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)           | Remove a class                                                                              |
| [`Element.classList.replace()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)          | Replace a class                                                                             |
| [`Element.classList.toggle()`](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)           | Toggle a class                                                                              |
| [`Element.dataset`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/dataset)                    | Get / set data attributes                                                                   |
| [`Element.style.property = value`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style)       | Get / set the inline style (use camelCase instead of "-" for compound property names)       |

---

## Dom Traversal

| Code                                         | Function                                                                                                    |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `document.getElementById(id)`                | Get an element by Id                                                                                        |
| `document.getElementsByClassName(className)` | Gets a list of elements by class name                                                                       |
| `document.querySelector(<CSS selector>)`     | Get a single element by CSS selector                                                                        |
| `document.querySelectorAll(<CSS selector>)`  | Get all elements by CSS selector                                                                            |
| `Element.querySelector(<CSS selector>)`      | Like `document.querySelector`but it traverses down the tree starting at the element the method is called on |
| `Element.closest(<CSS selector>)`            | Like `Element.querySelector` but traversing **up** the tree, selecting the closest parent by CSS selector   |
| `Element.nextElementSibling`                 | Get next sibling that is an element                                                                         |
| `Element.previousElementSibling`             | Get previous sibling that is an element                                                                     |
| `Element.children`                           | Get all child elements                                                                                      |
| `Element.parentElement`                      | Get the parent element                                                                                      |

## Shadow DOM

> Shadow DOM allows hidden DOM trees to be attached to elements in the regular DOM tree
> -- <cite>[MDN][1]</cite>

The Shadow DOM provides encapsulation.
It allows you to render a tree without exposing it in the DOM.

[1]: https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM
