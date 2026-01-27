# Bug Report

### Describe the bug

When using `<TransitionGroup>` with dynamic `:tag` prop in SSR, the component props are not being rendered in the output HTML. The props that should be applied to the transition group's root element are missing from the server-rendered markup.

### Reproduction

```vue
<template>
  <TransitionGroup :tag="'div'" class="my-class" id="my-id">
    <div v-for="item in items" :key="item.id">
      {{ item.name }}
    </div>
  </TransitionGroup>
</template>
```

When server-side rendering this component, the expected output should include the `class` and `id` attributes on the rendered `div`, but they are missing in the actual output.

### Expected behavior

The props (like `class`, `id`, etc.) passed to `TransitionGroup` should be included in the SSR output when using a dynamic `:tag` prop. The rendered HTML should contain all the attributes that were passed to the component.

### System Info

- Vue version: 3.x
- SSR environment

---
Repository: /testbed
