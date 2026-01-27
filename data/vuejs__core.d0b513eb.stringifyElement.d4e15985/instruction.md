# Bug Report

### Describe the bug

When using static node stringification in templates, the first attribute/prop of an element is being skipped and not rendered in the output. This causes the element to be missing its initial attribute.

### Reproduction

```vue
<template>
  <div id="first" class="second" data-value="third">
    Content
  </div>
</template>
```

When this template is compiled with static stringification enabled, the resulting HTML is missing the `id` attribute:

```html
<!-- Expected -->
<div id="first" class="second" data-value="third">Content</div>

<!-- Actual -->
<div class="second" data-value="third">Content</div>
```

The first prop is consistently dropped regardless of what it is (regular attributes, v-bind with constants, etc.).

### Steps to reproduce

1. Create a template with multiple attributes on an element
2. Compile with static node stringification
3. Observe that the first attribute is missing from the stringified output

### Expected behavior

All attributes should be included in the stringified static nodes, including the first one.

### System Info

- Vue version: 3.x
- Compiler: @vue/compiler-dom

---
Repository: /testbed
