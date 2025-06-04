# Build
https://www.youtube.com/watch?v=Q-YA_dA8C20
## Github: Create new repo under qmul-ceg
- name: `qmul-ceg/eldb-docs`
- Public
- Add Readme file
- Add .gitignore: Python
- Licence: GNU GPL v3.0
- default branch: `main`
## Local: Install MKdocs Material + Support Packages
- install [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) - `pip install mkdocs-material`
	- also installs [MkDocs](https://www.mkdocs.org), [Python-Markdown](https://python-markdown.github.io/), [Pygments (Python syntax highlighter)](https://pygments.org/) and [PyMdown Extensions (Markdown Extensions)](https://facelessuser.github.io/pymdown-extensions/).
- install [Awesome Nav for MkDocs](https://lukasgeiter.github.io/mkdocs-awesome-nav/) - `pip install mkdocs-awesome-pages-plugin`
- install [Publisher for MkDocs](https://mkdocs-publisher.github.io/setup/installation/) - `pip install mkdocs-publisher`
	- also reinstalls MkDocs, Material for MkDocs and PyMdown Extensions
- **any additional installs need to be added to the github ci.yml - see below**
## Local: Create New MkDocs Project
- create mkdocs folder/files - `mkdocs new .`
	- ~> creates `mkdocs.yml` and `docs/index.md`
- open mkdocs.yml - add material theme:
```yaml
theme:
  name:material
```
- add plugins in mkdocs.yml
```yaml
plugins:
    - search
    - awesome-nav
        filename: nav.yml
    # - pub-meta
    - pub-obsidian:
        obsidian_dir:.obsidian
        templates_dir:_templates
        backlinks:
	      enabled: true
        links:
        wikilinks_enabled: true
```
- create `docs/nav.yml` containing navigation info
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
- add markdown files
## Local: View local version
- run mkdocs - `mkdocs serve`
	- ~> runs webserver showing *index.md* at http://127.0.0.1:8000/
	- view in browser
- saving a file (Ctrl-S) ~> updates and reloads in browser
## Local: Github Pages Setup
Creates a Github Action that runs whenever a Commit is Pushed.
- create `eldb-docs\.github\workflows\ci.yml` containing:
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
      - uses: actions/setup-python@v5
        with:
          python-version: 3.x
      - uses: actions/cache@v4
        with:
          key: ${{ github.ref }}
          path: .cache
      - run: pip install mkdocs-material
      - run: pip install mkdocs-awesome-nav
      - run: pip install mkdocs-publisher
      - run: mkdocs gh-deploy --force
```
~> updates to repo will now automatically deploy
## Github: Set Repo to Use Github Pages
- Settings > Pages
	- Source: Deploy from a branch
	- Branch: gh-pages
	- Save
