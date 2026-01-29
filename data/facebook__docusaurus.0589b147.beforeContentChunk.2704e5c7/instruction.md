# Bug Report

### Describe the bug

I'm encountering an issue with fenced code blocks in MDX where the content parsing logic seems to be broken. The code block content is not being processed correctly, which causes rendering problems.

### Reproduction

```mdx
```js
const example = 'test';
console.log(example);
```
```

When I try to render this simple fenced code block, the content doesn't appear as expected. The parser seems to be handling the code flow incorrectly.

### Expected behavior

Fenced code blocks should parse and render their content properly. The code inside the fence should be captured and displayed correctly in the output.

### Additional context

This seems to affect any fenced code block with content. Empty code blocks might work fine, but as soon as there's actual content between the fences, the behavior becomes unpredictable.

---
Repository: /testbed
