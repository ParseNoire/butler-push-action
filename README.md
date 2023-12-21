# `butler` push action

Pushes a local directory to itch.io using `butler`.

## Usage

```yaml
name: my-workflow

on: push

jobs:
  push:
    runs-on: ubuntu-latest
    container: ghcr.io/parsenoire/butler:latest
    steps:
      - uses: parsenoire/butler-login-action@v1
        with:
          credentials: ${{ secrets.BUTLER_API_KEY }}
      - uses: parsenoire/butler-push-action@v1
        with:
          path: /path/to/export
          target: user/project:channel
```

While the image [ghcr.io/parsenoire/butler](https://ghcr.io/parsenoire/butler) from GitHub Container Registry is used in this example, this action should work in environments where `butler` is installed in the runner's PATH.

This example also uses [parsenoire/butler-login-action](https://github.com/parsenoire/butler-login-action) to authenticate `butler`. If your runner environment handles authentication in a different way, you can omit or change that step.
