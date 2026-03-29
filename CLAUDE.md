Valenzano Lab Website Redesign — Project Instructions
Context
This project rebuilds the website for the Valenzano Lab at the Leibniz Institute on Aging (FLI) in Jena, Germany. The current site lives at https://valenzano-lab.github.io/labsite/ and is a plain HTML GitHub Pages site. The goal is a redesigned site built with Quarto, deployable via GitHub Pages, with a blog.
The GitHub repository is valenzano-lab/labsite. The current plain HTML site is preserved on a branch called legacy-html-site. All new development happens on a branch called quarto-redesign, which will eventually be merged into main. The rendered site output (what GitHub Pages serves) goes to a gh-pages branch, which is managed automatically by quarto publish gh-pages and is never hand-edited.
Design philosophy
The primary reference for inspiration is https://matsen.fhcrc.org/. The key principle to borrow: the homepage is the science. Research content belongs on the landing page, not hidden behind navigation. Visitors should understand what the lab does and why it is distinctive within seconds of arrival, without clicking.
Avoid generic academic lab aesthetics: no stock photo banners, no "welcome to our lab" openers, no science-as-bullet-points formatting. Lead with claims, not descriptions.
Lab identity
Full name: Valenzano Lab — Evolution and Ecology of Aging
PI: Prof. Dario Riccardo Valenzano, Scientific Director and group leader, FLI Jena
Model organism: African turquoise killifish (Nothobranchius furzeri) — the shortest-lived vertebrate species bred in captivity
Field site: Gonarezhou National Park, Zimbabwe (active field research since 2010; molecular lab established at Chipinda Pools in 2023)
One-sentence lab identity: We use African killifish — in the lab and in the wild — to understand why and how animals age, from genes to ecosystems.
Research areas (homepage sections)
Each of the following is a full section on the homepage, structured as: declarative section header → figure or photo → ~100 word explanatory paragraph.

Evolutionary Ecology of Aging — Two timescales: how individuals age (mechanisms, genetics, ecology) and why species age the way they do (natural selection, neutral evolution, lifespan diversity across killifish species).
Microbiome and Aging — Host-microbiome crosstalk during aging: how hosts shape their microbiome, how microbiome composition affects health and lifespan, whether microbial evolution within a host lifespan exacerbates systemic aging and pathology.
Immune System and Aging — Evolution of adaptive immunity across killifish species; clonal B cell diversity and somatic mutation during aging; how immune aging drives age-dependent microbiome dysbiosis.
Field Research in Gonarezhou — Population ecology, demography, and population genetics of wild turquoise killifish in Zimbabwe. Long-term monitoring, eDNA-based conservation, and collaborative biodiversity research with ZimParks, the University of Zimbabwe, and the Gonarezhou Conservation Trust.

Navigation
Flat, no dropdowns. Pages:

index.qmd — Home (contains all research sections)
blog.qmd — Blog listing page (auto-generated from posts)
publications.qmd — Publications
people.qmd — People
tools.qmd — Lab tools
join.qmd — Join us
dario.qmd — Dario

Blog posts live in posts/YYYY-MM-DD-slug/index.qmd. Each post has a title, date, author, and one or more categories (e.g. field-work, preprint, methods, commentary).
Quarto project structure
labsite/
├── _quarto.yml          # Site config: navigation, theme, output settings
├── _extensions/         # Any Quarto extensions (if needed)
├── index.qmd            # Homepage
├── blog.qmd             # Blog listing page
├── publications.qmd
├── people.qmd
├── tools.qmd
├── join.qmd
├── dario.qmd
├── styles.css           # Custom CSS overrides
├── posts/               # Blog posts
│   └── YYYY-MM-DD-slug/
│       ├── index.qmd
│       └── [figures or assets for this post]
└── files/
    └── pictures/        # Existing image assets (migrated from current site)
_quarto.yml skeleton
yamlproject:
  type: website
  output-dir: _site

website:
  title: "Valenzano Lab"
  description: "Evolution and Ecology of Aging — FLI Jena"
  favicon: files/pictures/lablogo_s3.png
  navbar:
    left:
      - text: "Home"
        href: index.qmd
      - text: "Blog"
        href: blog.qmd
      - text: "Publications"
        href: publications.qmd
      - text: "People"
        href: people.qmd
      - text: "Tools"
        href: tools.qmd
      - text: "Join us"
        href: join.qmd
      - text: "Dario"
        href: dario.qmd
    right:
      - icon: github
        href: https://github.com/valenzano-lab
  page-footer:
    center: "© Valenzano Lab, FLI Jena"

format:
  html:
    theme: [cosmo, styles.css]
    toc: false
    link-external-newwindow: true
The base theme cosmo is a clean, typographically conservative Quarto/Bootstrap theme. It is the closest to the Distill/Matsen aesthetic. All customization goes in styles.css — the _quarto.yml should stay minimal.
Blog configuration
blog.qmd should use the Quarto listing type. Example front matter:
yaml---
title: "Blog"
listing:
  contents: posts
  sort: "date desc"
  type: default
  categories: true
  feed: true
---
Post front matter template:
yaml---
title: "Post title"
date: 2026-03-01
author: "Dario Valenzano"
categories: [field-work, killifish]
image: "thumbnail.jpg"   # optional
description: "One sentence summary shown in the listing."
---
Visual assets
Existing photos live in files/pictures/. Key assets:

lablogo_s3.png — lab logo
website_s.jpg — hero/landscape image
notho-postcard.png — killifish illustration
Malugwe.png — Gonarezhou field site photo
rousseau.png — used on current projects page
fish_tag.png — tagged fish image

Field photography from Zimbabwe and fish photography from the lab are the primary visual differentiators of this site. Use them prominently and at large size, not as thumbnails.
Writing style rules
These apply to all text written for the site and must be enforced consistently:

No em-dashes. Use commas, colons, or restructure the sentence.
Active and declarative sentences. Main point at the opening of each paragraph.
No filler openers: never start with "Welcome to," "We are a," "Our lab is."
Species names in italics: Nothobranchius furzeri.
Aphoristic closing sentences are acceptable only when the claim is specific and falsifiable, not generic inspiration.
Aim for the register of good science writing: clear, precise, confident, not promotional.

Technical constraints

Output must be deployable on GitHub Pages via quarto publish gh-pages
No JavaScript frameworks beyond what Quarto/Bootstrap includes by default
Mobile responsive (Quarto/Bootstrap handles this by default)
Prefer plain Quarto Markdown (.qmd) over raw HTML blocks wherever possible
Custom CSS goes in styles.css only, never inline

Local development commands
bash# Preview site locally with live reload
quarto preview

# Render without serving
quarto render

# Deploy to GitHub Pages (run from main branch when ready to go live)
quarto publish gh-pages
Branching model

legacy-html-site — frozen original site, never touched
quarto-redesign — active development branch
main — receives merge from quarto-redesign only when ready to go live
gh-pages — auto-managed by Quarto, never hand-edited

What to preserve from the current site

Publications content and structure
People page content
Lab logo and general color palette (dark navy with teal accent) — the styles.css should reinforce these, adjusting the cosmo theme defaults accordingly

Scope
Tasks within scope:

_quarto.yml configuration
index.qmd — full homepage with all four research sections
blog.qmd — listing page
First template blog post in posts/ to establish the format
styles.css — theme customization
Copywriting for all homepage sections
Migration of existing pages to .qmd format

When writing or editing files, always show the full file unless explicitly asked for a diff. When proposing design decisions, state the reasoning. Push back if a proposed change contradicts the design principles above.
