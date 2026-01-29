# Bug Report

### Describe the bug

When running `browserify help advanced`, the command hangs and doesn't exit properly. The help text is displayed correctly, but the process never terminates and I have to manually kill it with Ctrl+C.

### Reproduction

```bash
browserify help advanced
# Help text displays but command never exits
# Process stays running indefinitely
```

This also happens with:
```bash
browserify --help=advanced
browserify -h advanced
```

### Expected behavior

The help command should display the advanced help text and then exit cleanly, just like it did in previous versions. The process should terminate automatically after showing the help content.

### System Info
- browserify version: latest
- Node version: v18.x
- OS: macOS

This is blocking our CI pipeline since the help commands are timing out. Any help would be appreciated!

---
Repository: /testbed
