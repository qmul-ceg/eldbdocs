# Build
https://www.youtube.com/watch?v=Q-YA_dA8C20
## Github: Create new repo under qmul-ceg
- name: `qmul-ceg/eldbdocs`
- Public
- Add Readme file
- Add .gitignore: Python
- Licence: GNU GPL v3.0
- default branch: `main`
## Local: Create Python Environment
Setup a project environment, eg create *venv*
> [!note]- Terminal
> ```py
> # check python version
> py -0
> 
> cd path/to/eldbdocs
> py -m venv .venv
> 
> python -m pip install --upgrade pip
> ```

> [!note]- VS Code
> - Explorer > Open Folder - browse to `~\Github\eldbdocs`
> - Allow file execution - *Yes, I trust the authors*
> - Ctrl-Shift-P to open Command Palette > 'Python: Create environment'
>	> - type = Venv
>	-  interpreter = Python 3.x.0 ('env': venv)
>	- ~> creates a .venv folder containing Python environment
## Python: Install MKdocs Material + Support Packages
- install [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) - `pip install mkdocs-material`
	- also installs [MkDocs](https://www.mkdocs.org), [Python-Markdown](https://python-markdown.github.io/), [Pygments (Python syntax highlighter)](https://pygments.org/) and [PyMdown Extensions (Markdown Extensions)](https://facelessuser.github.io/pymdown-extensions/).
- install [Awesome Nav for MkDocs](https://lukasgeiter.github.io/mkdocs-awesome-nav/) - `pip install mkdocs-awesome-pages-plugin`
- install [Publisher for MkDocs](https://mkdocs-publisher.github.io/setup/installation/) - `pip install mkdocs-publisher`
	- also reinstalls MkDocs, Material for MkDocs and PyMdown Extensions
- **any additional installs need to be added to the github ci.yml - see below**
## Python: Create New MkDocs Project
Create new MkDocs project
```python
## creates mkdocs.yml and docs/index.md
mkdocs new .
```
Edit `mkdocs.yml` - add material theme
```yaml
theme:
  name:material
```
Edit `mkdocs.yml` - add plugins
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
Create `docs/nav.yml` and add navigation
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
Create / Add markdown files into `docs/`

Creates a Github Action that runs whenever a Commit is Pushed - deploys the site
Create `eldbdocs\.github\workflows\ci.yml` containing:
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

