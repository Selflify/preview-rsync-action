# Selflify Preview Rsync Action

Upload a built site directory to a Selflify preview server over SSH and `rsync`.

## What it does

- prepares the remote preview directory under `/var/www/<site>/<path-name>`
- syncs the build output with `rsync --delete`
- writes a `__preview_commit__/$GITHUB_SHA` marker for readiness checks

## Usage

```yaml
- uses: Selflify/preview-rsync-action@v1
  with:
    ssh-private-key: ${{ secrets.PREVIEW_SSH_PRIVATE_KEY }}
    preview-server-host: ${{ secrets.PREVIEW_SERVER_HOST }}
    preview-ssh-user: root
    preview-root-dir: /var/www
    site: marketing
    path-name: pr-42
    output: dist
```

## Marketplace-style repository layout

- `action.yml` exposes the composite action
- `README.md` is the public usage page
- `LICENSE` keeps the repo ready for public publishing
- `v1` is the stable ref workflows should pin to

## Publishing flow

1. push the repository updates
2. create or move the `v1` tag
3. optionally create a GitHub Release
4. publish the repo from the GitHub Marketplace UI if you want a Marketplace listing
