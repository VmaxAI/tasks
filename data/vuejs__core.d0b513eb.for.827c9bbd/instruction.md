# Bug Report

### Describe the bug

I'm experiencing an issue where the first prop on an element is being completely ignored during template compilation. It seems like the compiler is skipping the first property when searching for props, which causes bindings and attributes at index 0 to not be found.

### Reproduction

```vue
<template>
  <div id="container" class="wrapper" data-test="value">
    Content
  </div>
</template>
```

When the compiler tries to find the `id` prop (which is the first prop in the props array), it returns `undefined` instead of the actual prop object. This affects both static attributes and dynamic bindings that happen to be the first prop on an element.

Another example with dynamic binding:
```vue
<template>
  <input :value="text" type="text" />
</template>
```

The `:value` binding is not being detected correctly when it's the first prop.

### Expected behavior

All props should be found regardless of their position in the props array. The first prop should be processed the same way as any other prop.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This seems to have started happening recently. Any prop that's not in the first position works fine, but the first one is consistently missed.

---
Repository: /testbed
