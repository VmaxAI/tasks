# Bug Report

### Describe the bug

I'm experiencing an issue with the AviSynth language definition where the syntax highlighting seems to be broken or incomplete. After a recent update, code that should be properly highlighted is no longer being recognized correctly.

### Reproduction

When trying to use AviSynth syntax highlighting, the grammar appears to be cut off or incomplete. For example:

```avisynth
# Basic AviSynth script
video = AviSource("input.avi")
filtered = video.ConvertToYV12()
return filtered
```

The highlighting doesn't work as expected and seems to stop processing partway through the language definition.

### Expected behavior

The AviSynth grammar should properly highlight all language keywords, built-in functions, and properties. Functions like `AviSource`, `ConvertToYV12`, and other standard filters should be recognized and highlighted correctly.

### Additional context

This appears to have started happening recently. The language definition seems to be truncated or not loading completely. I noticed the issue affects both the main `avisynth` identifier and the `avs` alias.

---
Repository: /testbed
