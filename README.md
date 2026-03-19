# Electa Applications — Download Portal

This repository hosts the public download page for the Electa desktop applications.  
It is published via **GitHub Pages** at the URL configured in the repository settings.

The site is built with [Jekyll](https://jekyllrb.com/) using the [Minimal](https://github.com/pages-themes/minimal) remote theme.

---

## Repository structure

```
├── _config.yml          # Jekyll site configuration (title, theme, etc.)
├── _layouts/            # Layout overrides (currently empty — using theme defaults)
├── _sass/               # Custom SCSS partials
├── assets/
│   ├── css/style.scss   # SCSS entry point (compiles to style.css)
│   └── img/             # Logo and other images
├── index.md             # Main page content (rendered by Jekyll)
├── keys-app/            # Keys Application installers
├── trustee-app/         # Trustee Application installers
├── Gemfile              # Ruby dependencies (for local preview)
└── README.md            # ← You are here
```

---

## Publishing a new app version

### 1. Add the installer files

Copy the new installer(s) into the appropriate directory:

- **Trustee Application** → `trustee-app/`
- **Keys Application** → `keys-app/`

Follow the existing naming convention:

| App      | Pattern                                              |
|----------|------------------------------------------------------|
| Trustee  | `Trustee Application_<version>_<platform>.<ext>`     |
| Keys     | `Assembly.Voting.Keys.<version>.<ext>` (Windows)     |
|          | `Assembly.Voting.Keys-<version>.<ext>` (macOS)       |

### 2. Update `index.md`

1. Update the **"Latest release"** section with the new version number and download links.
2. Move the previous latest release into the **"Older versions"** table.
3. URL-encode any spaces in filenames with `%20` (e.g. `Trustee%20Application_3.2.0_universal.dmg`).

### 3. Commit and push

```bash
git add .
git commit -m "Add Trustee Application vX.Y.Z"
git push
```

GitHub Pages will rebuild the site automatically. It typically takes 1–2 minutes for changes to appear.

---

## Local preview

To preview the site locally before pushing:

```bash
# Install dependencies (first time only)
bundle install

# Serve locally
bundle exec jekyll serve
```

Then open [http://localhost:4000](http://localhost:4000).

> **Note:** `Gemfile.lock` is git-ignored because GitHub Pages uses its own pinned dependency versions.

---

## Removing old versions

To keep the repository size manageable, you may want to remove very old installers. When doing so:

1. Delete the file(s) from `keys-app/` or `trustee-app/`.
2. Remove the corresponding row(s) from the **"Older versions"** table in `index.md`.
3. Commit and push.

> **Tip:** Even after deleting files from the working tree, they remain in Git history and the repo size stays large. If repo size becomes a concern, consider using [Git LFS](https://git-lfs.com/) for binary assets or a `git filter-repo` rewrite.
