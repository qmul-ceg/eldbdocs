# Deploying EDLB-Docs
## View local version
- run mkdocs - `mkdocs serve`
	- ~> runs webserver showing *index.md* at http://127.0.0.1:8000/
	- view in browser
## Publish to Github Pages
Commit and Push to Github main
### Github Desktop
- Select eldb-docs as Current Repository
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
Wait - can take a while to become available
at: https://qmul-ceg.github.io/eldb-docs/

## Custom Domain
When using the custom domain `https://eldbdocs.qmul-ceg.net` a CNAME file contain just the domain name needs to be created in the `eldb-docs/docs` folder:
```txt
eldbdocs.qmul-ceg.net
```


