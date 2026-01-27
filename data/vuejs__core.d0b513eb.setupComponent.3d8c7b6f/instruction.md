# Bug Report

### Describe the bug

Components are not rendering properly when using the composition API setup function. The component setup appears to be skipped entirely, resulting in components that don't initialize their state or reactive data correctly.

### Reproduction

```js
import { defineComponent, ref } from 'vue'

const MyComponent = defineComponent({
  setup() {
    const count = ref(0)
    
    return {
      count
    }
  },
  template: '<div>{{ count }}</div>'
})
```

When this component is mounted, the setup function doesn't execute as expected, and the template has no access to the returned state.

### Expected behavior

The setup function should run during component initialization, and the returned state should be available in the template. The component should render with the initial count value of 0.

### System Info
- Vue version: 3.x
- Environment: Both SSR and client-side rendering affected

---
Repository: /testbed
