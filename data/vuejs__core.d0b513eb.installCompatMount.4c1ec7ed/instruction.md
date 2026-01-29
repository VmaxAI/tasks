# Bug Report

### Describe the bug

When using the compatibility build with `$mount()`, components without a render function are not rendering properly. The component appears to mount but nothing is displayed even when the component has a valid template.

### Reproduction

```js
const MyComponent = {
  template: '<div>Hello World</div>'
}

const vm = new Vue(MyComponent)
vm.$mount('#app')
```

Expected: The template should be rendered to the DOM.
Actual: Nothing is rendered, the container remains empty.

### Additional context

This seems to affect components that rely on template compilation. When I provide an explicit `render` function, everything works as expected. The issue only occurs when using `$mount()` with a template-based component.

### System Info
- Vue version: 3.x (compat build)
- Browser: Chrome

---
Repository: /testbed
