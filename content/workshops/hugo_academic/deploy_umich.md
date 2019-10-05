---
title: Deployment on UMich Space 
linktitle: Deployment on UMich Space 
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  hugo_academic:
    parent: Personal Academic Website Using Hugo
    name: Deployment on UMich Space 
    weight: 3

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

need to set up mfile first

should do local version control, but dont need to for the manip

change base url
```
baseurl = "http://www-personal.umich.edu/~uniqname/"
```

copy the content of the `public` to the `Public/html` folder :
```
scp -r <path-to-local-website>/public/. uniqname@login.itd.umich.edu:Public/html/
```

or use a FTP client: 
WinSCP 
```
login.itd.umich.edu
```
port 22
uniqname+password

- Access to the [ITS Login Service](http://www.umich.edu/~gpcc/login/)
- An [IFS home](http://www.itd.umich.edu/itcsdocs/r1070/) directory
[MFile](https://mfile.umich.edu/)
[Web Hosting Tutorial from ITS](http://www.umich.edu/~umweb/how-to/homepage.html)
