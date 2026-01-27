# Bug Report

### Describe the bug

I'm getting a syntax error when trying to use `reactive()` or `readonly()` with non-object values. The code seems to have been corrupted with Python code inserted into the TypeScript source, causing the entire reactivity system to fail.

### Reproduction

```js
import { reactive } from 'vue'

// This throws a syntax error
const state = reactive(123)

// This also fails
const obj = reactive({ count: 0 })
```

### Expected behavior

When passing a non-object value to `reactive()`, it should:
1. Return the original value unchanged
2. Show a development warning (in dev mode) explaining that the value cannot be made reactive

The reactivity system should continue to work normally for valid object inputs.

### System Info
- Vue version: 3.x
- Build tool: Vite

### Additional context

The application completely fails to load and shows syntax errors in the console. It looks like there might be some file corruption or merge conflict that wasn't resolved properly in the reactive.ts file.

---
Repository: /testbed
