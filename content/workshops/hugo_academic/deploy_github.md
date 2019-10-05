---
title: Deployment on GitHub
linktitle: Deployment on GitHub
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  hugo_academic:
    parent: Personal Academic Website Using Hugo
    name: Deployment on GitHub
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---
change public to docs in config
```
publishDir = "docs"
```
change base url
```
baseurl = "https://your-github-account.github.io/academic-kickstart/"
```

git add -all
git commit -m 'First deploy'
git push


go to github
go to academic kickstart 
settings
scroll down to github pages
source to master/docs

should be up in a few seconds!

