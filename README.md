# Check a Casama plugin

A GitHub Action that checks an [Agent Plugins 1.0](https://docs.casama.ai/develop/plugins) package
the way Casama checks it at install. It runs [`@casama/plugin-check`](https://www.npmjs.com/package/@casama/plugin-check)
from npm; the checker's source is in [casama-ai/casama](https://github.com/casama-ai/casama/tree/main/packages/plugin-check).

```yaml
name: Plugin check
on: [push, pull_request]
jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: casama-ai/plugin-check-action@v1
        with:
          path: .
```

Inputs:

- `path`: the plugin folder, relative to the repository root (default `.`).
- `strict`: also fail when Casama would skip or ignore something (default `true`).
- `version`: the `@casama/plugin-check` version to run (default `0.1.0`).

Start a plugin with `casama init plugin`, or copy
[`examples/hello-plugin`](https://github.com/casama-ai/casama/tree/main/examples/hello-plugin).

Apache-2.0.
