# Operational Notes

## Working rules
- The phase follows from `plan/current-task.md`: empty → plan the next task, sub-tasks → implement them.
- Keep context roughly in sync with the code, detailed only for the part in focus.
- Module details belong in the module's `README.md`, not here.
- Unit tests: `node testing/unittests/test.mjs [module...]` - see `testing/unittests/README.md`.
- New module directory → `npm run sync-allmodules` (or create it via `npm run add-module`), else its styles are missing and `initialize` never runs.
- `log` / `olog` output is switched per module in `debugmodule/debugmodule.coffee` (`modulesToDebug`): the user keeps every module listed and comments / uncomments them. Enable the module there when adding debug output, comment it out again when done.
- implicit-dom-connect only creates the global for an id that the code uses as `idName.` (property access). An id only passed as an argument (`fn(idName)`) stays undefined → add a `# idName.` comment line as workaround (the user's convention).

