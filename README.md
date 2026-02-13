# CI Images

Shared CI images for kaiserlich-dev repos.

## Available Images

| Image | Tags | Contents |
|-------|------|----------|
| `ghcr.io/kaiserlich-dev/ci-images/ruby` | `3.3.5`, `3.4.1` | Ruby + build-essential + git |
| `ghcr.io/kaiserlich-dev/ci-images/node` | `20`, `22` | Node.js + python3/make/g++ (native modules) |

## Usage

In any repo's workflow:

```yaml
env:
  CI_IMAGE: ghcr.io/kaiserlich-dev/ci-images/ruby:3.3.5
  BUNDLE_CACHE: /opt/cache/${{ github.event.repository.name }}/bundle

jobs:
  lint:
    runs-on: [self-hosted, linux, x64]
    steps:
      - uses: actions/checkout@v4
      - run: mkdir -p ${{ env.BUNDLE_CACHE }}
      - name: Lint
        run: |
          docker run --rm \
            -v "${{ github.workspace }}:/app" \
            -v "${{ env.BUNDLE_CACHE }}:/usr/local/bundle" \
            -w /app ${{ env.CI_IMAGE }} bash -c "
              bundle install --quiet &&
              bundle exec rubocop -f github
            "
```

## Adding versions

Add to the matrix in `.github/workflows/build.yml` and push.
