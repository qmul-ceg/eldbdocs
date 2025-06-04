# Editing ELDB-Docs MkDocs
## docs
- All displayed ELDB-Docs content must in the `eldb-docs/docs` folder.
	- `eldb-docs/docs/index.md`cannot be renamed or moved - contains Home page
	- `eldb-docs/docs/nav.yml` cannot be renamed or moved - contains sidebar navigation
	- images are stored in the `eldb-docs/docs/img` folder under a suitable subfolder
	- `eldb-docs/.obsidian` should be ignored
## overrides
- CSS customisation is in `eldb-docs/overrides/assets/stylesheets/extra.css`
## MkDocs Settings
- MkDocs settings are in  `eldb-docs/mkdocs.yml`
## Page Structure
An example page is provided below
- YAML section - Each page is headed by a yaml section, defined by two "---" lines.  In Obsidian it is rendered as a *Properties* item.  This is not displayed in the website, but provides settings info.

http://127.0.0.1:8000/ceg-vpn_login/

```markdown
---
title: "This Page"
publish: "true"
---
# Main Page Heading
## Subheading1
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

## Subheading2
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
```
