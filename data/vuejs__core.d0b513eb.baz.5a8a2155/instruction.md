# Bug Report

### Describe the bug

I'm encountering an issue with the `emits` property validation on functional components. When defining an `emits` object with validators that should be invalid, the type checking doesn't seem to catch the error properly.

### Reproduction

```tsx
const Bar = (props: { foo: number }) => {
  return <div>{props.foo}</div>
}

Bar.emits = {
  update: value => value > 1,
}

// This should throw a type error but doesn't
Bar.emits = { baz: () => { void 1 } }
```

### Expected behavior

TypeScript should raise an error when assigning an invalid `emits` configuration to a functional component. The validator function format appears incorrect but no type error is being reported.

### System Info
- Vue version: 3.x
- TypeScript version: 5.x

---
Repository: /testbed
