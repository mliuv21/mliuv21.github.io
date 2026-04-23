# Repository Notes

- This repo is a single Jekyll site based on `al-folio`, not a JS/TS app or monorepo.
- GitHub Pages deploy is defined in `.github/workflows/jekyll.yml`: pushes to `main` build with Ruby `3.1` and run `bundle exec jekyll build --baseurl "${{ steps.pages.outputs.base_path }}"`.
- No repo-local lint, typecheck, or test configs were found. The main verification step is a clean Jekyll build.

# Commands

- Install gems: `bundle install`
- Build once: `bundle exec jekyll build`
- Local dev server: `bundle exec jekyll serve --lsi`
- Docker dev server: `docker-compose up` on `http://localhost:8080`
- Rebuild Docker image against the current `Gemfile`: `docker-compose -f docker-local.yml up`
- Both Docker compose files delete `Gemfile.lock` inside the container before serving; do not assume lockfile-based reproducibility here.

# Source Of Truth

- `_config.yml` is the wiring hub: it includes `_pages`, defines Jekyll Scholar, enables custom plugins, and configures collections for `_news` and `_projects`.
- Home page source is `_pages/About.md` because it has `permalink: /`; page files live under `_pages/`, not repo root.
- Publications are rendered from `_bibliography/papers.bib` via `_pages/Publications.md` and the `scholar` config in `_config.yml`.
- The selected papers block on the home page comes from `_includes/selected_papers.html`, which filters bibliography entries with `selected={true}`.
- CV content comes from `_data/cv.yml`; `_pages/CV.md` only selects the `cv` layout and the downloadable PDF (`assets/pdf/LMZ_Resume__public.pdf`).
- Home page news items come from `_news/*.md`; `_pages/About.md` has `news: true`.

# Repo-Specific Gotchas

- Do not hand-edit `_site/`. It is tracked in git, but CI rebuilds from source; treat it as generated output unless the user explicitly asks for committed build artifacts.
- `_projects/` and `_posts/` still contain upstream `al-folio` demo content. Confirm with the user before deleting or repurposing large sets of sample files.
- Bibliography output is customized by `_plugins/hideCustomBibtex.rb`, which removes fields listed in `_config.yml` under `filtered_bibtex_keywords`. If publication rendering changes, inspect both together.
- `_plugins/external-posts.rb` fetches RSS entries from `external_sources` in `_config.yml`, so blog output can depend on network content, not only local `_posts/` files.
- `_pages/Projects.md` is non-standard: it uses `layout: project`, but there is no matching `_layouts/project.html` in this repo. Verify the intended projects-page behavior before trying to “fix” or extend it.
