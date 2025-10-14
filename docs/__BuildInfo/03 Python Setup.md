## Python: Setup environment
Setup a project environment, eg create *venv*
> [!note]- Terminal
> ```python
> cd path/to/eldbdocs
> 
> ## check python launcher for versions installed (* is default)
> py -0p
> 
> ## create with default py python version
> py -m venv .venv
> ## OR create with specific python version
> python3.14 -m venv .venv
> ```

> [!note]- VS Code
> - Explorer > Open Folder - browse to `~\Github\eldbdocs`
> - Allow file execution - *Yes, I trust the authors*
> - Ctrl-Shift-P to open Command Palette > 'Python: Create environment'
>	> - type = Venv
>	-  interpreter = Python 3.x.0 ('env': venv)
>	- ~> creates a .venv folder containing Python environment
## Python: Install MKdocs Material + Support Packages
```Python
## activate the virtual environment
cd path/to/eldbdocs
.venv/scripts/activate

## update pip installer
python -m pip install --upgrade pip

## install packages
pip install mkdocs-material
pip install mkdocs-awesome-nav
pip install mkdocs-awesome-pages-plugin
pip install mkdocs-publisher
pip install mkdocs-git-revision-date-localized-plugin
```
#### [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
Installs  [MkDocs](https://www.mkdocs.org) + Material Theme with additional functionality:
- [Python-Markdown](https://python-markdown.github.io/)
- [Pygments (Python syntax highlighter)](https://pygments.org/)
- [PyMdown Extensions (Markdown Extensions)](https://facelessuser.github.io/pymdown-extensions/).
#### [Awesome Nav for MkDocs](https://lukasgeiter.github.io/mkdocs-awesome-nav/)
Adds improved sidebar navigation
#### [Publisher for MkDocs](https://mkdocs-publisher.github.io/setup/installation/)
Enables metatags, blogging and Obsidian integration
also reinstalls MkDocs, Material for MkDocs and PyMdown Extensions
#### [mkdocs-git-revision-date-localized-plugin](https://github.com/timvink/mkdocs-git-revision-date-localized-plugin)
Adds last modified date to webpages

**ensure installs are also added to `ci.yml` to be actioned in GitHub
