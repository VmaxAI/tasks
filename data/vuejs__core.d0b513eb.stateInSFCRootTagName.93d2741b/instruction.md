# Bug Report

### Describe the bug

I'm encountering an issue with SFC (Single File Component) parsing where non-template root tags in `.vue` files are not being treated correctly. When using `<script>` or `<style>` as root-level tags, the compiler seems to be handling them as if they were `<template>` tags instead of RCDATA elements.

### Reproduction

Create a `.vue` file with a non-template root tag:

```vue
<script setup>
const message = 'Hello'
</script>
```

Or:

```vue
<style scoped>
.container { color: red; }
</style>
```

The parser doesn't correctly recognize the closing tags for these elements, leading to unexpected parsing behavior. It appears that `<template>` tags are being given special treatment when they should actually be the ones treated as RCDATA, not the other way around.

### Expected behavior

Non-template root tags like `<script>` and `<style>` should be parsed as RCDATA elements where their content is treated as raw text until the corresponding closing tag is found. The `<template>` tag should be handled normally as an HTML element.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
