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

### 1. Create a GitHub Release

New versions of the Trustee Application are distributed via **GitHub Releases**.

1. Go to the repository's **Releases** page and click **Draft a new release**.
2. Create a new tag following the convention: `trustee-app-vX.Y.Z` (e.g. `trustee-app-v4.2.0`).
3. Upload the installer files as release assets, following the naming convention:

| Platform | Pattern                                          |
|----------|--------------------------------------------------|
| Windows  | `Trustee.Application_<version>_x64-setup.exe`   |
| macOS    | `Trustee.Application_<version>_universal.dmg`   |

4. Publish the release.

### 2. Update `index.md`

1. Update the **"Latest release"** section with the new version number and GitHub Release download links.  
   Use the release asset URL format:  
   `https://github.com/aion-dk/apps/releases/download/trustee-app-vX.Y.Z/Trustee.Application_X.Y.Z_<platform>.<ext>`
2. Move the previous latest release into the **"Older versions"** table.

### 3. Commit and push

```bash
git add index.md
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


