# Bug Report

### Describe the bug

I'm experiencing an issue with custom elements not being recognized properly by the compiler. When I define a custom element using `isCustomElement`, the compiler seems to be treating it as a component instead of a native element, which breaks the expected behavior.

Additionally, there seems to be a problem with the `is` attribute detection on elements. When I use the `is` attribute on the first prop of an element, it's not being recognized correctly and the element isn't being treated as a component.

### Reproduction

```js
// Configure custom element
app.config.compilerOptions.isCustomElement = tag => tag.startsWith('my-')

// Template with custom element
const template = `<my-custom-element></my-custom-element>`

// The custom element is incorrectly treated as a component
// instead of being treated as a native custom element
```

Also having issues with `is` attribute:

```html
<!-- This should be treated as a component but isn't detected -->
<div is="MyComponent"></div>
```

### Expected behavior

1. Elements matching the `isCustomElement` predicate should be treated as native custom elements, not as Vue components
2. The `is` attribute should be detected on elements regardless of its position in the props array

### System Info
- Vue version: 3.x
- Compiler: compiler-core

---
Repository: /testbed
