# Web Components

Web components allow you to create reusable custom HTML elements which encapsulate their functionality.
Main building blocks:

- Custom Elements
- Shadow DOM
- HTML Templates

## Custom Elements

Custom Elements let you create your own custom HTML tags from scratch or by extending existing html element classes. They provide methods to manage the lifecycle of your element like:

- `constructor()`: called on initiation of an element
- `connectedCallback()`: called when the element is added to the DOM
- `disconnectedCallback()`: called when the element is removed from the DOM
- `attributeChangedCallback(attributeName, oldValue, newValue)`: called when an attribute is added, removed, updated, or replaced

## Shadow DOM

The Shadow DOM is used to encapsulate styles and markup in our components. Create ith with `element.attachShadow({ mode: open })`. It creates a **shadowRoot** that we can reference and interact with.

## HTML Templates

HTML Templates let us define the markup and CSS of our component. Use the `<template>` tag to store markup on your page for late use. Use **slots** to make the template dynamic and add custom text.
