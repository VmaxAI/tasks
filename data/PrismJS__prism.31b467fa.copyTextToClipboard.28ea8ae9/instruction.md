# Bug Report

### Describe the bug

The copy to clipboard functionality is not working at all. When I click the copy button on code blocks, nothing gets copied to the clipboard and no success message appears.

### Reproduction

```html
<pre><code class="language-javascript">
console.log('test');
</code></pre>
```

Steps to reproduce:
1. Add a code block with the copy-to-clipboard plugin enabled
2. Click the copy button
3. Try to paste - nothing is copied
4. The success callback never fires

This seems to affect all browsers that support the modern Clipboard API (Chrome, Firefox, Edge, etc.). The copy button appears but clicking it does nothing.

### Expected behavior

When clicking the copy button:
- The code content should be copied to the clipboard
- The success callback should be triggered
- Users should be able to paste the copied content

### System Info
- Prism version: Latest
- Browser: Chrome 120, Firefox 121
- OS: Windows/macOS

---
Repository: /testbed
