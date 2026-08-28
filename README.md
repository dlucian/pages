# pages.daniliuc.com

Evergreen static hosting for Lucian's HTML pages and images, served by
GitHub Pages under a domain we own. The git history is the archive: if the
host ever changes, copy the tree, repoint DNS, and every URL keeps working.

## URL scheme

The URL scheme is the contract. Paths are never renamed or deleted.

| Path | Content |
|---|---|
| `/a/<slug>/` | Self-contained HTML pages (one directory per page, `index.html` inside) |
| `/img/<yyyy>/<mm>/<name>` | Images: screenshots for PRs and issues, images linked from vault notes |
| `/lib/<name>` | Shared libraries and fonts for the HTML pages |

## Rules

- **Everything here is public.** Do not commit anything private; private
  files live in Seafile. History is forever — check before you push.
- Compress images before committing: WebP for photos and screenshots,
  SVG or PNG for diagrams. Keep single files under 1 MB where possible.
- Pages are self-contained: inline CSS/JS or reference `/lib/`, never a
  third-party CDN that can rot.
- Publish with `ezri-pages-publish` (in `dlucian/ezri` at `bin/`), which
  routes to the scheme above, commits, pushes, and prints the final URL.

## Serving

GitHub Pages, branch `master`, root. Custom domain `pages.daniliuc.com`
(the `CNAME` file), DNS CNAME to `dlucian.github.io`. `.nojekyll` disables
the Jekyll build so files serve verbatim. Deploys land ~30-60 seconds
after a push.
