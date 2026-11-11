# McGill Athletes in Business (ABS) website

The club website: a single static page with no build step.

- `index.html` holds the whole page: content, styles and a small script for the menu, scroll fade-ins and the placement filters.
- `assets/` holds images. Put real ABS photos here and point the `background-image` URLs in `index.html` at them. The current photos are stock images from Unsplash.

## Updating content

Each section in `index.html` starts with a comment (`<!-- EVENTS -->`, `<!-- TEAM -->`, and so on). Edit the text there.

- **New event:** copy one `<article class="card">` block in the Events section.
- **Placements:** each `<div class="place">` is one role. `data-r` sets the filter: `qc` (Montréal), `ca` (rest of Canada), `us` or `intl`. Update the counts on the filter buttons to match.
- **Team:** edit the `leaders` and `teams` blocks each year.

## Hosting

The site can be hosted for free with GitHub Pages. In the repo, go to Settings → Pages, then under "Build and deployment" choose "Deploy from a branch", with branch `main` and folder `/ (root)`.
