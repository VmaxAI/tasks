# Bug Report

### Describe the bug

I'm experiencing an issue with file path matching in Docusaurus where files that ARE contained within the root folders are incorrectly throwing an error saying they're not contained in any root folder.

### Reproduction

When processing files that are located inside the configured root folders, I'm getting errors like:

```
createAbsoluteFilePathMatcher unexpected error, absoluteFilePath=/path/to/my/docs/file.md was not contained in any of the root folders: /path/to/my/docs
```

This is happening even though the file path clearly starts with the root folder path. The error message is confusing because the file IS actually within the root folder, but the matcher is rejecting it.

### Expected behavior

Files that are located within the specified root folders should be matched successfully without throwing an error. The matcher should only throw an error when a file path is genuinely outside of all configured root folders.

### Additional context

This seems to affect file path processing across the board - any file that should be matched is instead being rejected. The logic appears to be inverted somehow.

---
Repository: /testbed
