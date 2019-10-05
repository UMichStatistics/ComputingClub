---
title: Initialize the website
linktitle: Initialize the website
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  hugo_academic:
    parent: Personal Academic Website Using Hugo
    name: Initialize the website
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

[Academic theme documentation](https://sourcethemes.com/academic/docs/)

[Hugo Getting Started](https://gohugo.io/getting-started)
## Prereq

- Hugo installed on your machine (see this [guide](https://gohugo.io/getting-started/installing/)).
- git installed on your machine (see this [guide](https://www.atlassian.com/git/tutorials/install-git)).

## Initialize and first deploy

[Academic theme documentation: Install with Git](https://sourcethemes.com/academic/docs/install/#install-with-git)

say it is exactly what hugo academic suggests

fork to your github account (put link)

clone your own repo locally
```shell
git clone https://github.com/fontaine618/academic-kickstart.git DemoWebsite
cd DemoWebsite
```

import the academic theme
```shell
git submodule update
```


produce html files
```shell
cd ../..
hugo
```

serve locally to see ythe basic site provided
```shell
hugo server
```

## Description of the repository and first edits

First focus on contents

Authors

Home

Post/Pubs/Talks

Heres where youd put courses

Go Home
prune things by deleting folders
- demo
- hero
- people
- slider
prune things by deactivating them
- tags
Comment here is our first Markdown file. Only a header

Since we deleted files server dit not catch it so restart
```shell
<ctrl+c>
hugo server
```

## Author
Open about
explain
go to admin
change a few things

## Adding content

```shell
hugo new --kind post post/MyFirstPost
```
look at what happened

```shell
hugo new --kind talk talk/MyFirsTalk
hugo new --kind publication publication/MyFirstPublication
```
point out the filtering publications alert and click


## Playing with the menu
Light mode
search site
links point to home page
try making it point to search publication instead

## Configuration
second folder we see : config

- config very important contains high-level description of the site
- languages is not imporatnat unless you want to ttransalte your site in multiple languages
- menus :
- params: mostly display settings, color theme offers a few choices, but you can hvae more control than the one they propose

## Rest of repository

maybe just say that statis is where you would put a new site icon


## Create a course page
create the file, hugo has to real course template
```shell
hugo new --kind docs course/MyFirstCourse/_index.md
hugo new course/_index.md
```


