# Bug Report

### Describe the bug
MDX JSX syntax is not being parsed correctly. When using JSX components in MDX files, they're being treated as regular text instead of being recognized as JSX elements.

### Reproduction
```mdx
import { MyComponent } from './components'

# Hello World

<MyComponent prop="value">
  Some content here
</MyComponent>
```

The JSX component `<MyComponent>` is not being parsed as a JSX element. Instead, it appears to be treated as plain text or markdown content.

### Expected behavior
JSX components should be properly recognized and parsed in MDX files. The `<MyComponent>` should be handled as a JSX element with its props and children correctly processed.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
