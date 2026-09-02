# Cert Study Kits

Self-study kits and learning notes, built diagram-first so concepts are visible, not just described. Published as a site with GitHub Pages.

## Live site

https://carolinemutua.github.io/cert-study-kits/

## Kits

| Kit | Goal |
| --- | --- |
| `gh-600-agentic-ai-developer/` | Study kit for GitHub Certified: Agentic AI Developer (Exam GH-600) |
| `gh-300-github-copilot/` | Study kit for the GitHub Copilot certification (Exam GH-300) |
| `claude-certified-architect/` | Study kit for the Claude Certified Architect (Foundations) exam |
| `git-github-ci/` | Notes on version control, pull requests, and CI workflows |
| `continuous-deployment/` | How a merge becomes a live deployment through a real pipeline |

## Structure

Each kit is a folder of Markdown pages rendered by the [just-the-docs](https://just-the-docs.com/) theme, with Mermaid diagrams enabled. Content leads with a diagram, then explains the flow underneath it. A certification kit follows the same shape: an orientation page with exam facts, a dated sprint plan weighted to the scored areas, domain deep-dives that each lead with a diagram, a practice bank with collapsible answers and flashcards, and a resources page of first-party sources.

## Continuous integration

Every pull request into `main` runs the `build` workflow in `.github/workflows/`, which builds the Jekyll site with `actions/jekyll-build-pages`. A pull request should be green before it is merged, so a broken site is never published.

## Local preview

Requires Ruby and Bundler.

Windows (PowerShell):

```powershell
gem install bundler jekyll
bundle exec jekyll serve
```

macOS or Linux (bash or zsh):

```bash
gem install bundler jekyll
bundle exec jekyll serve
```

Then open http://localhost:4000/cert-study-kits/.

## Contributing a new kit

1. Create a folder named for the topic, with an `index.md` that sets `nav_order` and `has_children: true`.
2. Add child pages (`plan.md`, `domains.md`, `practice.md`, `resources.md`) with `parent:` set to the kit title.
3. Lead each concept with a Mermaid diagram, then explain it underneath.
4. Cite only first-party or well-maintained sources on the resources page.
5. Open a pull request and let the `build` workflow pass before merging.
