# Bug Report

### Describe the bug

I'm experiencing an issue with SSR rendering when using `v-for` combined with scoped slots. The component fails to render correctly when both directives are present on the same element.

### Reproduction

```vue
<template>
  <MyComponent>
    <template v-for="item in items" v-slot="slotProps">
      {{ slotProps.data }} - {{ item }}
    </template>
  </MyComponent>
</template>
```

When rendering this component on the server, the output is incorrect. The `v-for` seems to interfere with the slot props handling.

### Expected behavior

The component should render properly with both `v-for` and scoped slots working together. The slot props should be accessible within each iteration of the loop.

### System Info
- Vue version: 3.x
- SSR environment: Node.js

This seems to be related to how the SSR compiler handles the combination of these directives. Any help would be appreciated!

---
Repository: /testbed
