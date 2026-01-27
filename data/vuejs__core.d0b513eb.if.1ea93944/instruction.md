# Bug Report

### Describe the bug

The compiler is throwing unexpected errors during template compilation. It seems like assertion logic is inverted - errors are being thrown when conditions are true instead of when they're false.

### Reproduction

```js
// Any template that triggers internal compiler assertions
const template = `
  <div v-if="show">
    <component :is="dynamicComponent" />
  </div>
`

compile(template)
// Throws: "unexpected compiler condition"
```

This happens with various template patterns that should be valid. The compiler seems to be failing on conditions that should pass validation.

### Expected behavior

The compiler should only throw assertion errors when something is actually wrong, not when conditions are met correctly. Valid templates should compile without errors.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
