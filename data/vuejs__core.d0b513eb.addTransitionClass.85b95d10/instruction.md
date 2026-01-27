# Bug Report

### Describe the bug

I'm experiencing an issue with transition classes not being applied correctly to elements. When I specify transition classes with multiple class names separated by spaces, the behavior seems broken - the classes aren't being added to the element as expected.

### Reproduction

```js
const el = document.createElement('div')

// Try to add transition classes with multiple names
addTransitionClass(el, 'fade-enter-active fade-enter-from')

// Expected: both 'fade-enter-active' and 'fade-enter-from' should be added
// Actual: classes are not applied correctly
console.log(el.classList) // doesn't contain the expected classes
```

### Expected behavior

When calling `addTransitionClass` with a string containing multiple space-separated class names, all individual classes should be added to the element's classList. The internal tracking set should also properly store each individual class name for later removal.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

This seems to affect any component using transitions with multiple classes. The transition animations don't work properly because the classes aren't being applied.

---
Repository: /testbed
