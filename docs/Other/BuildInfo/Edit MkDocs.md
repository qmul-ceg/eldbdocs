# Edit MkDocs
## Website Content
- All displayed content must in the `/docs` folder.
	- `/docs/index.md`cannot be renamed or moved - contains the Home page
	- `/docs/nav.yml` cannot be renamed or moved - contains sidebar navigation
	- images are best stored in `/docs/_img`
## MkDocs Settings
- MkDocs settings - `mkdocs.yml`
- CSS customisation - `overrides/assets/stylesheets/extra.css`
- Github Action (deployment script) - `.github/workflows/ci.yml`
- `.gitignore` should exclude Python +
```git
# Obsidian
.obsidian/
/docs/.obsidian

# Environments
.env
.venv
env/
venv/
ENV/
env.bak/
venv.bak/

# PyCharm
.idea/
```
## Page Structure
```markdown
# Main Page Heading
## Subheading1
Lorem ipsum dolor sit amet, **consectetur** adipiscing elit, sed do *eiusmod* tempor incididunt ut labore et dolore ***magna aliqua***. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

### Subheading2
~~strikethrough~~, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat `code` non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

- bullet point
- bullet point
```
Use \ to escape characters
Code block using triple backticks ` ``` ` 
```codetype
code {here}
```
Relative link to pages -  `[link text](../folderpath/file.md#subheading)`

> [!note]- Collapsible Note Heading
> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. 
> - Bullet point

## Python: View local version
MkDocs will display the site (`index.md`) on a local webserver
```python
# activate environment Python
.venv\scripts\activate 

# activate server
mkdocs serve
```
Go to http://127.0.0.1:8000/ to view
Saved changes made to any file (Ctrl+S) updates and reloads the site
# Deploying EDLB-Docs
## View local version
- run mkdocs - `mkdocs serve` ~> view at  http://127.0.0.1:8000/
## Publish to Github Pages
### Github Desktop
- Select eldbdocs as Current Repository
- Add a Summary (+ description) of the changes
- Commit to *main*
- Push *origin*
### Git
```git
git pull
~~~~~~~~~~ 
git status
git add .
git commit -m "{Summary}"
git push
```
Github Action needs to run - can take c.1min for the website to refresh



