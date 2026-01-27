# Bug Report

### Describe the bug

I'm experiencing issues with `<TransitionGroup>` components during server-side rendering. When using the `tag` prop along with other props, the other props are being completely ignored and not rendered in the SSR output.

### Reproduction

```vue
<template>
  <TransitionGroup tag="ul" class="list" id="my-list">
    <li v-for="item in items" :key="item">{{ item }}</li>
  </TransitionGroup>
</template>
```

When rendering this component on the server, the expected output should include the `class` and `id` attributes on the `ul` element, but they're missing from the rendered HTML.

### Expected behavior

The SSR output should include all props passed to the TransitionGroup component on the rendered tag element. For the example above, it should render:

```html
<ul class="list" id="my-list">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
```

But instead, only the tag is rendered without any of the additional props.

### System Info
- Vue version: 3.x
- SSR: Yes

---
Repository: /testbed
