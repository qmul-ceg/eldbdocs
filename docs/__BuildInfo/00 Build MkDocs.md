https://www.youtube.com/watch?v=Q-YA_dA8C20
## Required Software
- Python 3.10+
- a Python IDE (eg PyCharm or Visual Studio Code)
- Git (and/or Github Desktop)
***
## Github website: Create new repo under qmul-ceg
- name: `qmul-ceg/eldbdocs`
- Public
- Add Readme file
- Add .gitignore: Python
- Licence: GNU GPL v3.0
- default branch: `main`
## Clone repo to local
[[01 Clone GitHub Repo]]
## Setup Obsidian Vault
[[02 Obsidian Setup]]
## Setup Python Environment + MkDocs
[[03 Python Setup]]
## Python: Create New MkDocs Project
Create new MkDocs project
```python
## creates mkdocs.yml and docs/index.md
mkdocs new .
```
Create / Add markdown files into `docs/`
### Edit `mkdocs.yml`
```yaml
site_name: CEG East London DataBase Documentation
theme:
  name: material
  custom_dir: overrides
  features:
    - navigation.tabs # page headers displayed in nav sidebar
    - navigation.tabs.sticky # sticky page headers in nav sidebar
    # - navigation.sections #  page headers displayed in nav sidebar
    - navigation.path # displays a breadcrumb path to the current page
    # - toc.integrate # integrate the table of contents into the nav sidebar
    - navigation.top
    - navigation.indexes
    - navigation.instant
    - navigation.instant.progress
    - search.suggest
    - search.highlight
    - content.tabs.link
    - content.code.annotation
    - content.code.copy
  language: en
  palette:
    - scheme: qmul # default # light mode
      primary: custom # indigo # header, sidebar, text links +
      accent: custom # purple # hovered links, buttons, scroll bars
  font:
    text: Source Sans 3
    code: Source Code Pro
  logo: _img/logos/QMUL_clear.png
  favicon: _img/logos/QMUL_purple.jpg

docs_dir: docs
exclude_docs: |
  /__BuildInfo/

watch:
  - overrides
extra_css:
  - assets/stylesheets/extra.css

plugins:
    - search
    - awesome-nav
        filename: nav.yml
    - pub-obsidian:
        obsidian_dir:.obsidian
        # templates_dir:_templates
        backlinks:
	      enabled: true
        links:
          wikilinks_enabled: true
    - git-revision-date-localized:
        type: iso_datetime  

markdown_extensions:
  - pymdownx.betterem # improved md formatting
  - pymdownx.caret # adds underline (^^) (& superscript (^)
  - pymdownx.mark # adds highlighting (==)
  - pymdownx.tilde # adds strikethrough (~)
  - pymdownx.details # collapsable sections (???)
  - pymdownx.superfences # nesting & custom fences
  - pymdownx.highlight:
      anchor_linenums: true # code highlighting
  - pymdownx.inlinehilite # code highlighting
  - pymdownx.snippets # insert md or html snippets
  - admonition # callouts
  - attr_list
  - md_in_html

copyright: |
  &copy; 2024 <a href="https://www.qmul.ac.uk/ceg/" target="_blank" rel="noopener">Clinical Effectiveness Group</a>

extra:
  analytics:
    feedback:
      title: Was this page helpful?
      ratings:
        - icon: material/emoticon-happy-outline
          name: This page was helpful
          data: 1
          note: >-
            Thanks for your feedback!
        - icon: material/emoticon-sad-outline
          name: This page could be improved
          data: 0
          note: >-
            Thanks for your feedback! Help us improve this page by
            using our <a href="..." target="_blank" rel="noopener">feedback form</a>.
```
### Create & Edit `docs/nav.yml`
```.pages
nav:
    - Home: index.md
    - Connecting
        - eldb_connection_overview.md
        - eldb_vpn_setup.md
        - eldb_connect_vpn.md
    - Data Information
        - ...
```
### Create & Edit `eldbdocs\.github\workflows\ci.yml`
Creates a Github Action that runs whenever a Commit is Pushed - deploys the site
```yaml
name: ci 
on:
  push:
    branches:
      - master 
      - main
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
          sparse-checkout: |
            docs
            overrides
      - uses: actions/setup-python@v5
        with:
          python-version: 3.x
      - uses: actions/cache@v4
        with:
          key: ${{ github.ref }}
          path: .cache
      - run: pip install mkdocs-material
      - run: pip install mkdocs-awesome-pages-plugin
      - run: pip install mkdocs-publisher
      - run: pip install mkdocs-git-revision-date-localized-plugin
      - run: mkdocs gh-deploy --force
```
## Github: Set Repo to Use Github Pages
- Settings > Pages
	- Source: Deploy from a branch
	- Branch: gh-pages
	- Save
Creates at: https://qmul-ceg.github.io/eldbdocs/
## Custom Domain
When using the custom domain `https://eldbdocs.qmul-ceg.net` a CNAME file contain just the domain name needs to be created in the `/docs` folder:
```txt
eldbdocs.qmul-ceg.net
```

