# Bug Report

### Describe the bug

I'm experiencing an issue where the first prop/attribute on an element is being completely ignored during template compilation. When I have multiple props on an element, only the second one onwards seem to be processed correctly.

### Reproduction

```vue
<template>
  <div id="app" class="container" data-test="value">
    <!-- The id prop is not being found/processed -->
  </div>
  
  <input type="text" v-model="value" placeholder="test">
  <!-- The type attribute is skipped -->
</template>
```

When trying to access or check for the first attribute/prop on any element, it returns `undefined` even though it clearly exists in the template. The second and subsequent props work fine.

This seems to affect both static attributes and dynamic bindings. For example:

```vue
<button :disabled="isDisabled" @click="handleClick">
  <!-- :disabled binding is not detected -->
</button>
```

### Expected behavior

All props and attributes should be processed correctly regardless of their position. The first prop on an element should be accessible just like any other prop.

### System Info
- Vue version: 3.x
- Build tool: Vite

This is breaking prop detection logic in my components. Any help would be appreciated!

---
Repository: /testbed
