# nitik1998.github.io

Source for my personal website — **[nitik1998.github.io](https://nitik1998.github.io)**.

I'm **Nitik Jain**, a robotics researcher and applied-AI engineer pursuing an
M.S.E. in Robotics at **Johns Hopkins University**, working at the intersection of
**robot learning, vision-language-action models, perception, and generative &
medical AI**. The site collects my research, projects, publications, experience,
and CV.

[![Deploy site](https://github.com/nitik1998/nitik1998.github.io/actions/workflows/deploy.yml/badge.svg)](https://github.com/nitik1998/nitik1998.github.io/actions/workflows/deploy.yml)

## What's here

| Page | Path |
| --- | --- |
| About / home | `/` |
| Publications | `/publications/` |
| Projects | `/projects/` |
| Industry experience | `/industry-experience/` |
| Back to society | `/back-to-society/` |
| Blog (WIP) | `/blog/` |
| CV (web + PDF) | `/cv/` |

## Tech

Built on the [**al-folio**](https://github.com/alshedivat/al-folio) Jekyll theme,
with a custom terminal-inspired look (banner, `$ ls ~/…` section headers, and a
`grep`-style ⌘K / Ctrl-K search). Visual cues for the banner were inspired by
[Leandro A. Bugnon's site](https://lbugnon.github.io/).

- **Content:** `_pages/`, `_projects/`, `_news/`, `_bibliography/papers.bib`
- **Data:** `_data/` (`cv.yml`, `socials.yml`, `affiliations.yml`)
- **Theme/layout:** `_layouts/`, `_includes/`, `_sass/`, `assets/css/main.scss`
- **Assets:** `assets/img/`, `assets/pdf/`

## CV

The CV is two-tier: a **web version** at `/cv/` (rendered by al-folio from
`_data/cv.yml`) and a **typeset PDF** download (`assets/pdf/Nitik_Jain_CV.pdf`),
linked on `/cv/` and from the homepage.

## Local development

System Ruby lacks dev headers here, so the site is built inside a conda env:

```bash
# one-time setup (pin ruby 3.3 — newer Ruby breaks Jekyll 4.x)
conda create -y -n jekyll -c conda-forge "ruby=3.3" compilers make
conda run -n jekyll bundle install

# build + preview
conda run --no-capture-output -n jekyll bundle exec jekyll build
python3 -m http.server 8080 --directory _site   # → http://localhost:8080
```

## Deployment

Pushing to **`main`** triggers the **Deploy site** GitHub Action
(`.github/workflows/deploy.yml`): it builds the site with `JEKYLL_ENV=production`,
purges unused CSS, and publishes `_site` to the **`gh-pages`** branch, which
GitHub Pages serves at the root domain. No manual deploy step is needed.

## Credits & license

- Theme: [al-folio](https://github.com/alshedivat/al-folio) by Maruan Al-Shedivat
  and contributors (MIT).
- Banner design inspiration: [Leandro A. Bugnon](https://lbugnon.github.io/).

Site content © Nitik Jain. Theme code under the MIT License (see `LICENSE`).
