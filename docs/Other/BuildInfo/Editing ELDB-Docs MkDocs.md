# Editing ELDB-Docs MkDocs
## docs
- All displayed ELDB-Docs content must in the `eldb-docs/docs` folder.
	- `index.md`cannot be renamed or moved - contains Home page
	- `.pages` cannot be renamed or moved - contains sidebar navigation
	- images are stored in the `docs/img` folder under a suitable subfolder
	- `.obsidian` shoud be ignored
## overrides
- CSS customisation is in `eldb-docs/overrides/assets/stylesheets/extra.css`
## mkdoc.yml
- contains site settings 

## Page Structure
An example page is provided below
- YAML section - Each page is headed by a yaml section, defined by two "---" lines.  In Obsidian it is rendered as a *Properties* item.  This is not displayed in the website, but provides settings for deployment:
	- `title:` The title of the page
	- `publish:` Publish page on website - "true" = yes,  "hidden" = yes but not in navigation, "draft" = no.

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
