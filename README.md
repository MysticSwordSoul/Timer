# Aaj kitna padhe

A study timer that works offline and installs like an app. It is plain static files with no build step.

## Files
- `index.html` – the whole app
- `sw.js` – service worker that makes it work offline
- `manifest.webmanifest` + `icons/` – lets phones and desktops install it
- `_headers`, `vercel.json`, `.nojekyll` – optional hosting settings

## Deploy
Upload this folder's contents so that `index.html` sits at the root.

- **Netlify:** drag the folder onto app.netlify.com/drop.
- **Cloudflare Pages:** create a project, choose "Direct upload", add the folder. Leave the build command empty.
- **Vercel:** run `npx vercel --prod` inside the folder, or import the repo. Framework preset: Other, no build command.
- **GitHub Pages:** push the files to a repo, then Settings > Pages > deploy from branch (root).

It must be served over HTTPS (all hosts above do this) for install and offline mode to work. Opening `index.html` directly from disk still works as a timer, just without install.

## Updating
After you edit any file, change `VERSION` at the top of `sw.js` (for example `v2`). That tells installed copies to fetch the new files.

## Data
Study time is stored in the browser's localStorage, per device and per web address. Changing the domain starts with empty data.
