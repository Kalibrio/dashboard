# dashboard.atomicscaling.com

Static GitHub Pages site for the Atomic Scaling dashboards.

- `/` — trading dashboard (`index.html`)
- `/fv` — FansVine creator dashboard, password-protected (`fv/index.html`, AES-256-GCM, decrypted in the browser)

## Source

Both pages are authored in `Kalibrio/atomic-scaling-os`, branch `claude/dashboard-project-setup-iy7t57`:

- `docs/dashboard/index.html` → copied here as `index.html`
- `docs/fv/index.html` → encrypted by `docs/fv/encrypt.mjs` into `fv/index.html`

## Rebuild

```bash
SRC=../Kalibrio/atomic-scaling-os
cp $SRC/docs/dashboard/index.html index.html
FV_PASSWORD='<password>' node $SRC/docs/fv/encrypt.mjs $SRC/docs/fv/index.html fv/index.html
git add -A && git commit -m "build: refresh dashboards" && git push
```

Live data: drop a `data.json` next to each page (schema documented inside the source files).
