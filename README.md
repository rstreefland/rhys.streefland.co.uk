# rhys.streefland.co.uk

Personal website built with Hugo 0.101.0 and custom layouts. No theme, JavaScript, external fonts, or frontend dependencies are needed.

## Editing

- Content: `content/`
- Templates: `layouts/`
- Styles: `assets/css/site.css`
- Custom domain: `static/CNAME`

## Adding a blog post

1. Run `hugo new posts/my-post.md`.
2. Edit the post and set `draft: false`.
3. Run `hugo --minify --cleanDestinationDir`.
4. Commit the source changes and generated `docs/` output.

The deployment workflow rebuilds the site on pushes to master. The old theme submodule is unused and is no longer fetched by CI.

See [PERFORMANCE.md](PERFORMANCE.md) for measured payload sizes, local timing results and measurement limitations.
