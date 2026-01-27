# Bug Report

### Describe the bug

I'm experiencing an issue where custom components are being incorrectly treated as native HTML elements in the template compiler. When I use a custom component in my template, Vue is treating it as a native tag instead of a component, which causes rendering issues.

### Reproduction

```vue
<template>
  <MyCustomComponent />
</template>

<script>
import MyCustomComponent from './MyCustomComponent.vue'

export default {
  components: {
    MyCustomComponent
  }
}
</script>
```

The component `MyCustomComponent` is being treated as a native HTML tag instead of being recognized as a Vue component. This causes the component not to render properly.

Similarly, when using standard HTML tags, they're also not being recognized correctly:

```vue
<template>
  <div>Hello</div>
  <svg><circle /></svg>
</template>
```

Both regular HTML tags and SVG tags seem to be affected by this issue.

### Expected behavior

- Custom components should be recognized as components, not native tags
- Standard HTML tags (like `div`, `span`, etc.) should be correctly identified as native HTML tags
- SVG tags should be correctly identified as native SVG tags
- MathML tags should be correctly identified as native MathML tags

### System Info

- Vue version: 3.x
- Build tool: Vite

This seems to have broken component resolution entirely. Any help would be appreciated!

---
Repository: /testbed
