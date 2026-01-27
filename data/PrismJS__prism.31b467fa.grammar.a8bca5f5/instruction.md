# Bug Report

### Describe the bug

I'm experiencing an issue with the Inform7 language syntax highlighting where certain keywords and properties are not being recognized properly. It seems like the pattern matching has been cut off or truncated, causing the syntax highlighting to fail for a large portion of valid Inform7 code.

### Reproduction

When writing Inform7 code with properties like `wearable` or other properties that should be highlighted, the syntax highlighting stops working:

```inform7
The player carries a wearable item.
The box is a closed openable container.
```

The highlighting works for some properties but breaks for others. It appears that properties starting with certain letters later in the alphabet aren't being recognized at all.

### Expected behavior

All valid Inform7 properties and keywords should be properly highlighted according to the language specification. Properties like `wearable`, `worn`, and other valid property names should receive the correct syntax highlighting.

### System Info
- Language: Inform7
- Issue appears to affect property and keyword recognition

---
Repository: /testbed
