# 2026-04-22 Session Notes

- Added a repo-local `AGENTS.md` for future OpenCode sessions.
- Verified this repo is a single Jekyll site based on `al-folio`, with GitHub Pages build in `.github/workflows/jekyll.yml` using Ruby `3.1`.
- Captured high-signal repo guidance in `AGENTS.md`: main commands, real content sources (`_pages/About.md`, `_data/cv.yml`, `_bibliography/papers.bib`, `_news/*.md`), and repo gotchas.
- Design review conclusion: the site works structurally, but looks too close to the default `al-folio` template and lacks a strong academic visual identity.
- Main design issues discussed: template feel is too strong, homepage hierarchy is flat, there is no custom visual system, and the site does not foreground the owner's research identity clearly enough.
- Positive note: the information architecture is serviceable (`About`, `Publications`, `CV`, `News`) and the repo can be improved without a full rebuild.
- High-priority future design directions discussed:
  - redesign the homepage first screen / hero area
  - define a restrained academic visual theme instead of using default template styling
  - prioritize research focus and selected publications over generic news flow
  - clean or hide upstream demo content in `_posts/` and `_projects/`
- Evaluated `https://github.com/nextlevelbuilder/ui-ux-pro-max-skill`.
- Conclusion on that skill: useful as a reference for design-system thinking, anti-patterns, and UI review checklists, but not a strong primary framework for this repo.
- Reasoning for the above: the skill is optimized more for product/landing-page UI across many stacks, while this repo is a Jekyll academic personal site that needs a more restrained, trust-building, research-focused design language.
- Recommended future approach: keep Jekyll/al-folio structure, then apply a custom academic redesign directly in this repo instead of depending heavily on the external UI skill.
