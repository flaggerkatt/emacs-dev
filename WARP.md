# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is an Emacs development repository. This repository is currently empty and ready for Emacs Lisp development.

## Common Commands

### Emacs Lisp Development
- **Load an Elisp file**: `emacs -Q -l <file.el>` (starts Emacs without config)
- **Byte-compile**: `emacs -batch -f batch-byte-compile <file.el>`
- **Run Elisp in batch mode**: `emacs -batch -l <file.el> --eval "<expression>"`
- **Check syntax**: `emacs --batch --eval "(check-parens)" <file.el>`

### Testing
- **ERT (Emacs Lisp Regression Testing)**: `emacs -batch -l <file.el> -l <test-file.el> -f ert-run-tests-batch-and-exit`
- **Run specific test**: `emacs -batch -l <file.el> -l <test-file.el> --eval "(ert-run-tests-batch-and-exit 'test-name)"`

### Package Development
- **Create package archive**: `emacs -batch -l package-build.el -f package-build-archive <package-name>`
- **Install package locally**: `emacs -batch --eval "(package-install-file \"<package-file.el>\")"`

## Architecture Guidelines

### Emacs Lisp Conventions
- Use `;;;` for file-level comments, `;;` for code-level comments, and `;` for inline comments
- Follow naming conventions: `package-name-function-name` for public functions, `package-name--function-name` for private functions
- Include proper docstrings for all interactive functions and user-facing variables
- Use `defcustom` for user-configurable variables, not `defvar`
- Mark interactive functions with `(interactive)` form

### File Organization
- Main package file should have `provide` statement at the end: `(provide 'package-name)`
- Test files typically end in `-test.el` or `-tests.el`
- Use `require` or `autoload` for dependencies

### Common Patterns
- Use `with-current-buffer` for buffer-local operations
- Prefer `save-excursion` and `save-restriction` to preserve buffer state
- Use `condition-case` or `ignore-errors` for error handling
- For hooks, use `add-hook` and `remove-hook`

## Development Notes

This repository structure follows standard Emacs package development practices. As the codebase grows, this file should be updated with specific build commands, testing procedures, and architectural decisions relevant to the actual code being developed.
