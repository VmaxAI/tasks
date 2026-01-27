# Bug Report

### Describe the bug

I'm getting a really strange error when trying to compile SFCs with only a regular `<script>` tag (no `<script setup>`). The compiler is throwing an error saying "SFC contains no <script> tags" even though the script tag is clearly present.

### Reproduction

```vue
<template>
  <div>Hello World</div>
</template>

<script>
export default {
  name: 'MyComponent',
  data() {
    return {
      message: 'test'
    }
  }
}
</script>
```

When compiling this component, I get:
```
[@vue/compiler-sfc] SFC contains no <script> tags.
```

### Expected behavior

The component should compile successfully since it has a valid `<script>` tag. This used to work fine before, but now it's failing on components that don't use `<script setup>`.

### System Info
- Vue version: 3.x
- Node: 18.x

This is blocking me from using regular script blocks in my components. Any help would be appreciated!

---
Repository: /testbed
