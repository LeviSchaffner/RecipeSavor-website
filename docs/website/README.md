RecipeSavor website (for GitHub Pages)

Files:
- `index.html` — landing page
- `css/site.css` — styles
- `assets/` — images and logos
- `CNAME` — contains the custom domain `levimakes.dev`

Local preview

You can preview the site locally using a static server. If you have Node.js installed:

```bash
cd RecipeSavor-ios/website
npx serve -s .  # or: npx http-server -c-1
```

Deploy to GitHub Pages (recommended)

Option A — push `website` as `gh-pages` branch (easy using `gh-pages` package):

1. From repo root, run:

```bash
# from repo root
git checkout -b gh-pages
rm -rf * # careful: only if you intend to publish the website folder contents
# instead, it's simpler to use a subtree or the gh-pages npm tool
```

Simpler: use the `gh-pages` npm helper (recommended):

```bash
npm install --save-dev gh-pages
# add to package.json scripts:
# "deploy": "gh-pages -d website"
npm run deploy
```

Option B — push `website` into `docs/` and enable GitHub Pages from `main/docs` in repository settings.

Cloudflare / levimakes.dev setup

1. In your GitHub repository settings -> Pages, set the Source to `gh-pages` branch (or `main/docs`) and note the GitHub Pages target (username.github.io/repo).
2. In Cloudflare DNS, create a CNAME record for `levimakes.dev` pointing to `username.github.io` (or the Pages target). If you need an apex record for `levimakes.dev`, use an ALIAS/ANAME if your DNS provider supports it, or follow Cloudflare instructions to use CNAME flattening.
3. Ensure your GitHub Pages site has the `CNAME` file (already added) with `levimakes.dev`.
4. In Cloudflare, enable SSL (Flexible/Full as appropriate). GitHub Pages supports HTTPS for custom domains; after DNS propagation GitHub will provision a certificate.

Notes

- Replace the placeholder images in `website/assets/` with your transparent PNG screenshots (same filenames to keep markup). The hero uses `phone-screens.png` which is a composite placeholder — you can replace it or update `index.html` to point to individual images.
- I can also add a simple `package.json` with a `deploy` script that uses `gh-pages` if you want me to wire automated deploy commands.
