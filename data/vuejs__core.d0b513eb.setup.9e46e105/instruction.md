# Bug Report

### Describe the bug

When defining a component with props that include `null` as a type option (e.g., `foo: [String, null]`), the resulting prop type is not correctly inferred. The prop type should be `string | null | undefined`, but it appears to be inferred as just `string | undefined`, losing the `null` type.

### Reproduction

```tsx
import { defineComponent } from 'vue'

const MyComponent = defineComponent({
  props: {
    foo: [String, null],
  },
  setup(props) {
    // TypeScript should infer props.foo as: string | null | undefined
    // But it's being inferred as: string | undefined
    // The null type is missing from the union
    
    const value = props.foo
    // Expected: value should accept null
    // Actual: null is not part of the type
  },
})
```

### Expected behavior

When a prop is defined with `[String, null]`, TypeScript should infer the prop type as `string | null | undefined`. The `null` type should be preserved in the union type, allowing the prop to explicitly accept `null` values in addition to strings and undefined.

### System Info
- Vue version: 3.x
- TypeScript version: latest

---
Repository: /testbed
