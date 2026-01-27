# Bug Report

### Describe the bug

I'm getting a build error after pulling the latest changes. It looks like there's a syntax issue in the `kindOf.ts` file - the function appears to have been accidentally replaced with Python code instead of TypeScript.

### Reproduction

```ts
import { kindOf } from './utils/kindOf'

const result = kindOf({ foo: 'bar' })
console.log(result)
```

When I try to build or run the code, I get syntax errors because the `kindOf` function is no longer valid TypeScript. The file seems to contain Python function definitions instead.

### Expected behavior

The `kindOf` utility function should return the type of the value passed to it, working correctly in both development and production environments.

### System Info
- TypeScript version: latest
- Node version: 18.x

This is blocking my work, any help would be appreciated!

---
Repository: /testbed
