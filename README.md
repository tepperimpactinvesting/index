# Tepper Impact Investing Club website

Plain HTML/CSS/JS (no framework). Pages are views switched by the URL hash (`#about`, `#member-program`, `#contact`, ...). The site opens on About.

## Repository layout
```
src/template.html   All page content, styles and scripts (edit this)
assets/             Photos, headshots and logos (replace files, keep names)
build.py            Assembles src/ + assets/ into one self-contained index.html
index.html          Built output (generated; do not edit by hand)
.github/workflows/  Auto-build + deploy to GitHub Pages on every push to main
```

## Publish (public link, no domain needed)
1. Create a GitHub repo and upload everything in this folder (the `.github` folder is hidden on some systems, make sure it uploads).
2. Settings -> Pages -> Source: **GitHub Actions**.
3. Push to `main` (or run the workflow from the Actions tab). After a minute the site is live at
   `https://<your-username-or-org>.github.io/<repo-name>/`
4. Share that link. Anyone can view it; nobody can change it.

Alternative without Actions: Source = "Deploy from a branch" -> `main` / root, and commit the built `index.html` yourself after running `python3 build.py`.

## Who can edit
Only people you add under Settings -> Collaborators (or org members with write access) can change files; everyone else can only view the published site. Note: on a free GitHub plan, Pages needs a public repo, so the code and images are readable by anyone even though only collaborators can edit. A private repo with Pages requires a paid plan.

## Edit
- Text, layout, styles: `src/template.html`.
- Event calendar: search for `var EV=` (date, title, type: teach / speaker / sim / vol / other; optional time and location).
- Links (Slack, forms, socials): search for `var L=` and the `href=` values.
- Photos / headshots / logos: replace the file in `assets/` with the same name.
- Preview locally: `python3 build.py`, then open `index.html` in a browser.

## Custom domain (later, optional)
Settings -> Pages -> Custom domain. No `CNAME` file is needed in the repo with the Actions source. At your registrar add four A records (`185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`) and a `www` CNAME to `<username>.github.io`, then tick "Enforce HTTPS".

Note: the in-page photo "upload tiles" only worked inside Claude. On GitHub, add photos by replacing files in `assets/`.
