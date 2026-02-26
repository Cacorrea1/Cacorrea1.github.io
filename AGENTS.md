# AGENTS.md

## Cursor Cloud specific instructions

### Overview

This is a minimal **GitHub Pages static site** (Jekyll + Slate theme) that embeds a Google Teachable Machine image classifier (TensorFlow.js) and a Dialogflow chatbot iframe. The entire site is two source files: `_config.yml` and `index.md`.

### Running the dev server

```bash
sudo bundle exec jekyll serve --host 0.0.0.0 --port 4000
```

The site is then available at `http://localhost:4000/`.

### Important caveats

- **Bundler must run with `sudo`** because system Ruby gems are installed in `/var/lib/gems/3.2.0/` which requires root write access.
- The `github-pages` gem is used instead of plain `jekyll` so that `index.md` is processed without front matter (matching GitHub Pages behavior). Using plain `jekyll` will not render `index.md` into `index.html` because the file lacks YAML front matter.
- The GitHub Metadata warning (`No GitHub API authentication could be found`) is expected and harmless in local development.
- The Sass `@import` deprecation warnings come from the upstream Slate theme and do not affect functionality.
- **Webcam access** is required for the Teachable Machine classifier to work in the browser — this won't function in headless environments.
- The Dialogflow chatbot iframe loads from an external URL and requires internet access.

### Build

```bash
sudo bundle exec jekyll build
```

Output goes to `_site/`.

### Lint / Tests

There are no lint rules or automated tests in this repository.
