# Bug Report

### Describe the bug

I'm encountering an issue with RCDATA parsing in the compiler. When entering RCDATA mode (for elements like `<textarea>` or `<title>`), the tokenizer doesn't properly initialize the sequence index, which causes problems with parsing the closing tag.

### Reproduction

```js
const template = `
  <textarea>
    some content here
  </textarea>
`

// The closing tag is not properly detected
compile(template)
```

Another example with title tags:

```js
const template = `<title>Page Title</title>`
// Similar issue - the closing sequence matching fails
```

### Expected behavior

The tokenizer should correctly enter RCDATA mode and properly track the sequence index for matching closing tags. The closing tags should be detected and parsed correctly.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

This seems to be related to how the sequence index is initialized when entering RCDATA state. The closing tag detection appears to be broken for RCDATA elements.

---
Repository: /testbed
