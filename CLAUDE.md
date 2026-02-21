# bjro.github.io

Personal blog built with Jekyll and the Minimal Mistakes theme, hosted on GitHub Pages.

## Development

```bash
bundle install                    # Install Ruby dependencies
bundle exec jekyll serve          # Serve locally at http://localhost:4000
bundle exec jekyll build          # Build to _site/
```

The site auto-rebuilds on file changes during `jekyll serve`. Changes to `_config.yml` require a server restart.

## Tools (via mise)

Go, Rodney, and Showboat are available via `mise exec` (see `mise.toml`).

```bash
mise exec -- rodney --version     # Browser automation
mise exec -- showboat --version   # Demo document generator
```

## Visual Verification

The `@qa` subagent uses **Rodney** (browser automation) and **Showboat** (demo artifacts) to verify the site renders correctly:

- Rodney drives a persistent headless Chrome session via CLI commands (`rodney start`, `rodney open`, `rodney assert`, etc.)
- Showboat captures each verification step as a persistent demo document at `.demos/<name>.md`
- Demo artifacts include screenshots and command outputs as reviewable evidence

To run QA verification, invoke the `@qa` subagent via the Task tool.

## Structure

- `_posts/` — Blog posts (Markdown with YAML front matter)
- `_config.yml` — Jekyll configuration and site metadata
- `_sass/` — SASS style overrides for the Minimal Mistakes theme
- `assets/images/` — Blog post images
- `index.html` — Homepage layout
- `_site/` — Generated output (gitignored)
