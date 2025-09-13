# INSUREX ZONE LLC — Static Website

A statically built website (Vite output) ready to serve locally, push to GitHub, and deploy on Vercel.

## Project Structure

- `index.html` — App entry, mounts the SPA root.
- `assets/` — Built JS and CSS assets referenced by `index.html`.
- `logonew.jpeg`, `website.jpg` — Static images.
- `vercel.json` — Vercel config for static hosting with SPA fallback.
- `.vercelignore` — Excludes local/dev files from deployment.
- `.gitignore` — Excludes local/dev files from source control.

## Run Locally

You can serve this static site with any static server. Two simple options:

### Option A: Python (built-in on most systems)

```bash
# From the project root
python -m http.server 5500 -d .
# Visit http://127.0.0.1:5500/
```

### Option B: Node "serve" (if you have Node.js)

```bash
# Install once (globally or use npx)
npm -g install serve
# or: npx serve -l 5500

# From the project root
serve -l 5500 .
# Visit http://127.0.0.1:5500/
```

## Deploy to Vercel

1. Create a new GitHub repository and push this folder:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: static site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. Go to https://vercel.com → Add New Project → Import your GitHub repo.
3. Framework Preset: "Other" (Static Site). No build command needed.
4. Root Directory: project root (where `index.html` is).
5. Deploy. Vercel will host files as-is using `vercel.json` routes. The SPA fallback ensures client-side routes resolve to `index.html`.

## Notes

- If you later add client-side routes (e.g., `/about`), they will work thanks to the SPA fallback in `vercel.json`.
- If you rebuild assets, ensure `index.html` references the new hashed filenames inside `assets/`.
- To change the favicon, update the `<link rel="icon" ...>` in `index.html`.
