# dashboard.atomicscaling.com

Static GitHub Pages site for the Atomic Scaling dashboards.

- `/` — trading dashboard (`index.html`)
- `/fv` — creator dashboard, password-protected (`fv/index.html`, AES-256-GCM, decrypted in the browser)

## Source

Authored in the private repo `Kalibrio/dashboard-src` (local clone `../dashboard-src`):

- `dashboard/index.html` → copied here as `index.html`
- `fv/index.html` → encrypted by `fv/encrypt.mjs` into `fv/index.html`

## Rebuild

```bash
SRC=../dashboard-src
cp $SRC/dashboard/index.html index.html
FV_PASSWORD='<password>' node $SRC/fv/encrypt.mjs $SRC/fv/index.html fv/index.html
git add -A && git commit -m "build: refresh dashboards" && git push
```

Live data: drop a `data.json` next to each page (schema documented inside the source files).
