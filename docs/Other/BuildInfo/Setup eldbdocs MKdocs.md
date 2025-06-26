# Setup
## Required Software
- Python 3.10+
- a Python IDE (eg PyCharm or Visual Studio Code)
- Git (and/or Github Desktop)

## Git: Clone Github Repo to a Local Repo
### Github Desktop
- File >> Clone repository
	- Select `qmul-ceg/eldbdocs` from the repo list
	- Choose the Local path in which to create the repo folder
		- Git works best outside OneDrive. eg `C:\Users\Kelvin\Github\eldbdocs`
	- Clone ~> creates copy of repo + setups connection to Github repo
### Git
```git
cd {parent folder}
mkdir eldb-docs
cd eldb-docs
git clone git@github.com:qmul-ceg/eldb-docs
```
## Git: Add Obsidian to gitignore
Add
```
# Obsidian
.obsidian/
```

## Obsidian: Setup Vault
- Open folder as vault >> Open
	- Browse to `../eldbdocs/docs` >> Select folder
- Rename vault to "eldbdocs" - vault cannot be open or the vault folders open in File Explorer
-  Settings >> 
- install *VSCode Editor* + Enable
	- Options >> File Extensions: Add ",yml"
	- (makes the nav.yml file visible for editing)
- install *Vault Nickname* + Enable
	- Options >> check Vault nickname: "eldbdocs"
	- (stops Vault showing as simply "docs")
- install *Editor Width Slider* + Enable
	- creates slider in right-hand bottom of app. Set to 3
	- (sets Obsidian editor to roughly the same width as webpage)

## Python: Setup environment
Setup your project environment, eg create *venv*
### Terminal
```py
# check python version
py -0

cd path/to/eldb-docs
py -m venv .venv

python -m pip install --upgrade pip
```
### VS Code
- Explorer > Open Folder - browse to `~\Github\eldbdocs`
- Allow file execution - *Yes, I trust the authors*
- Ctrl-Shift-P to open Command Palette > 'Python: Create environment'
	- type = Venv
	-  interpreter = Python 3.x.0 ('env': venv)
	- ~> creates a .venv folder containing Python environment
### Install MKdocs Material + Support Packages
- install [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) - `pip install mkdocs-material`
	- also installs [MkDocs](https://www.mkdocs.org), [Python-Markdown](https://python-markdown.github.io/), [Pygments (Python syntax highlighter)](https://pygments.org/) and [PyMdown Extensions (Markdown Extensions)](https://facelessuser.github.io/pymdown-extensions/).
- install [Awesome Nav for MkDocs](https://lukasgeiter.github.io/mkdocs-awesome-nav/) - `pip install mkdocs-awesome-nav`
- install [Publisher for MkDocs](https://mkdocs-publisher.github.io/setup/installation/) - `pip install mkdocs-publisher`
	- also reinstalls MkDocs, Material for MkDocs and PyMdown Extensions
- **any additional installs need to be added to the github ci.yml [[Build MkDocs#Local Github Pages Setup]]**
















