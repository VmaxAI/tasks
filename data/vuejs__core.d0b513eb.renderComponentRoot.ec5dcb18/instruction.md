# Bug Report

### Describe the bug

I'm experiencing an issue where components with a single attribute are not receiving their fallthrough attributes properly. When a component has exactly one attribute that should be inherited, it's not being applied to the root element.

### Reproduction

```js
// Parent component
<template>
  <ChildComponent class="my-class" />
</template>

// Child component with inheritAttrs (default true)
<template>
  <div>Content</div>
</template>
```

In this case, the `class="my-class"` attribute is not being applied to the child's root `<div>` element. However, if I add a second attribute like `id="test"`, both attributes are correctly applied.

### Expected behavior

The single fallthrough attribute should be applied to the root element, just like it works when there are multiple attributes. The number of attributes shouldn't affect whether they fallthrough or not.

### Additional context

This seems to affect any single attribute - not just `class`, but also `style`, `id`, event handlers, etc. As soon as there are 2 or more attributes, everything works as expected.

---
Repository: /testbed
