# repro-vscode-eslint-ignorefiles

This is meant to reproduce the issue outlined here: https://github.com/Microsoft/vscode-eslint/issues/550#issuecomment-434010041

## Non-working scenario (Reproduction)

1. Step into `packages/pk1/` on the CLI
2. Run `yarn run lint` and see `eslint` erroring on missing semicolon `packages/pkg1/.includeme2/test.js` (this is correct because `packages/pkg1/.eslintignore` explicitly icludes the `.includeme2`).
3. Open the repository in VS Code with `vscode-eslint` (1.7.0) at the time of writing) installed
4. Open `packages/pkg1/.includeme2/test.js`
  - Expected: See missing semicolon highlighted as error
  - Actual: No error is displayed

## Working scenario  (Reproduction)

1. Open `.includeme1/test.js`
  - Expected: See missing semicolon highlighted as error
  - Actual: _passes_