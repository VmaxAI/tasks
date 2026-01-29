# Bug Report

### Describe the bug

I'm seeing an issue with translation extraction warnings where the wrong warnings are being displayed for each file. When multiple files have translation warnings, all files show the same warning messages (from the first file) instead of their own specific warnings.

### Reproduction

1. Have multiple source code files with different translation extraction warnings
2. Run translation extraction
3. Observe that all warning messages show the warnings from the first file, not the actual warnings for each respective file

For example, if you have:
- `file1.tsx` with warning "Missing translation key A"
- `file2.tsx` with warning "Missing translation key B"

Both files will display "Missing translation key A" in the logs instead of their respective warnings.

### Expected behavior

Each file should display its own translation extraction warnings. The warning log for `file2.tsx` should show "Missing translation key B", not the warnings from `file1.tsx`.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
