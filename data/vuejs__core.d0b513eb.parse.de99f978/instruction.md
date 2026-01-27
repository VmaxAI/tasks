# Bug Report

### Describe the bug

I'm experiencing an issue with the template parser where custom parser options are being overridden by default options. When I pass specific parser options to `parse()`, they don't seem to be respected and the default `parserOptions` take precedence instead.

### Reproduction

```js
import { parse } from '@vue/compiler-dom'

const customOptions = {
  delimiters: ['[[', ']]'],
  comments: false
}

const ast = parse('<div>[[message]]</div>', customOptions)

// The AST is parsed with default delimiters {{ }} instead of [[ ]]
// Custom options are ignored
```

### Expected behavior

Custom parser options passed to `parse()` should override the default `parserOptions`. In the example above, the parser should recognize `[[` and `]]` as delimiters instead of the default `{{` and `}}`.

### System Info
- Vue version: 3.x
- Package: @vue/compiler-dom

---
Repository: /testbed
