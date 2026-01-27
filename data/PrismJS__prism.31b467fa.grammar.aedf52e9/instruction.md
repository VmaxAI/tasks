# Bug Report

### Describe the bug

The HLSL language grammar is not working correctly after a recent update. When trying to use syntax highlighting for HLSL code, class names and keywords are not being recognized properly.

### Reproduction

```js
import Prism from 'prismjs';
import 'prismjs/components/prism-hlsl';

const code = `
Buffer myBuffer;
float4 main() : SV_Target {
    return float4(1.0, 0.0, 0.0, 1.0);
}
`;

const highlighted = Prism.highlight(code, Prism.languages.hlsl, 'hlsl');
console.log(highlighted);
```

### Expected behavior

HLSL-specific types like `Buffer`, `float4`, and keywords should be properly tokenized and highlighted. The `class-name` token should include HLSL buffer types, and scalar/vector/matrix types should be recognized as keywords.

Currently the highlighting seems broken - class names and keywords are not being detected at all in HLSL code blocks.

### System Info
- Prism version: latest
- Browser: Firefox 121

---
Repository: /testbed
