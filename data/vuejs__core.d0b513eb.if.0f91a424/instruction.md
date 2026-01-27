# Bug Report

### Describe the bug

I'm having an issue with v-model on components in compatibility mode. It seems like the model event handlers are being called even when the compatibility feature is disabled, which is the opposite of what should happen.

### Reproduction

```js
// Component using v-model in compat mode
const MyComponent = {
  compatConfig: {
    COMPONENT_V_MODEL: false  // Disabled
  },
  template: '<input @input="$emit(\'input\', $event.target.value)" />'
}

// Parent component
const app = {
  data() {
    return { value: 'test' }
  },
  template: '<MyComponent v-model="value" />'
}
```

When I type in the input, the parent's `value` gets updated even though `COMPONENT_V_MODEL` compatibility is explicitly disabled. The model events should not be emitted when this compat flag is turned off.

### Expected behavior

When `COMPONENT_V_MODEL` compatibility is disabled, the component should not emit model update events. The v-model binding should not work in this case.

### System Info
- Vue version: 3.x (compat build)
- Build: ESM

---
Repository: /testbed
