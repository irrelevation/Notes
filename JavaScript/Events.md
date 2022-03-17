# JavaScript Events



## Propagation

There are 3 phases of propagation:

1. **Capture Phase**
	The event traverses **down** the DOM tree from the root to the target element.

2. **Target Phase**
	The event reached the target.

3. **Bubbling Phase**
	The event bubbles **up** the DOM tree from the target to the root.

The propagation can be stopped by calling `event.stopPropagation()`. If there are multiple event listeners registered on the current element, this will **not** stop these callbacks from being triggered. You can call `event.stopImmediatePropagation()`instead to achive this.


---



## Event Listeners

A target can have multiple event listeners and they execute in the order they were defined in.

| Code                                                     | Functionality                                                |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| `EventTarget.addEventListener(type, callback[, option])` | Add a callback function that will be called when the event is hits our target. |
| `option = {capture: true}`                               | The callback function will be triggered in the capture phase instead of the target or bubbling phase. |
| `option = {once: true}`                                  | Remove the callback after the event has occured              |
| `EventTarget.removeEventListener(type, callback)`        | Remove the callback (passed by reference)                    |

You can delegate eventhandling by adding an event listener to a parent element (document for global event handling) and checking for the target in the callback function with `event.target.matches(<CSS Selector>)`.


## Event Loop
