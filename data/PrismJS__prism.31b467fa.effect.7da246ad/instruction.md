# Bug Report

### Describe the bug

The show-language plugin is not respecting the `data-language` attribute when displaying language labels. It seems like the logic for determining which title to display has been changed, and now the `data-language` attribute is only used as a fallback instead of being prioritized.

### Reproduction

```html
<pre data-language="Custom Label"><code class="language-javascript">
console.log('test');
</code></pre>
```

When the above code block is rendered with the show-language plugin enabled, the toolbar shows "JavaScript" instead of "Custom Label".

### Expected behavior

The plugin should prioritize the `data-language` attribute value when present. If a custom label is specified via `data-language`, that should be displayed in the toolbar instead of the automatically detected language name.

Previously this was working correctly - custom labels set through `data-language` would override the default language display name.

### System Info
- Prism version: latest
- Browser: tested in Chrome and Firefox

---
Repository: /testbed
