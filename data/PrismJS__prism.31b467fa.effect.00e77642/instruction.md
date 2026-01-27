# Bug Report

### Describe the bug

The show-language plugin is displaying the wrong language name for code blocks. Instead of showing the actual language that was used in the code block, it seems to be trying to read from the wrong property.

### Reproduction

```html
<pre class="language-javascript"><code>
const x = 42;
</code></pre>
```

When the show-language plugin renders, it displays nothing or an incorrect language name instead of "JavaScript".

### Expected behavior

The plugin should correctly extract and display the language name from the code block. For example, a `language-javascript` class should display "JavaScript" in the toolbar.

### Additional context

This seems to have started happening recently. The language label either doesn't appear at all or shows undefined/incorrect values. The `data-language` attribute override still works, but the automatic language detection from the Prism environment is broken.

---
Repository: /testbed
