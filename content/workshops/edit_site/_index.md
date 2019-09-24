---
# Course title, summary, and position.
linktitle: Editing the Club's website
summary: A guide on how to add new content and modify the website.
weight: 1

# Page metadata.
title: Overview
date: "2018-09-09T00:00:00Z"
lastmod: "2018-09-09T00:00:00Z"
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.
author: [simon]

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  edit_site:
    name: Overview
    weight: 1
---

This website is powered the [Academic theme](https://sourcethemes.com/academic/) for [Hugo](https://gohugo.io/). The [documentation](https://sourcethemes.com/academic/docs/) they provide is quite extensive, so we summarize some of the important features relevant to the current website and present workflow ideas on how to update the website. 

## Hugo and Markdown

While the website consists of `html` source interpreted by the visitor's browser, its content is generated from Markdown. Hugo acts as an interpreter and compiler: it translates the file structure, the Markdown files and some configuration files (`yaml` or `toml`) into the `html` files visible to the visitor. 

## Repository description

The website is hosted on GitHub Pages. The static contents of the website appears in the `docs` folder of the [UmichStatistics](https://github.com/UMichStatistics/) GitHub organization repository [computingclub](https://github.com/UMichStatistics/computingclub/). The other folders and files of the repository are used to generate the website: only the `docs` folder is necessary for the static website to be operational. 

## Deployment

Any change in the files outside of the `docs` folder will not affect the public website. In order for the changes to become public, it is necessary to deploy the website, i.e. to use Hugo to update the files in `docs`. Hence, anyone updating the website needs to run Hugo for the changes to appear. More details in [Deployment](workflow/)

The maintainers are currently considerings ways to automatically deploy the website upon a push to the repository. More to come...


## External resources

- [Academic Hugo Documentation](https://sourcethemes.com/academic/docs/)
  - [Page Builder and widgets description](https://sourcethemes.com/academic/docs/page-builder/)
- [Font Awesome Icons](https://fontawesome.com/icons?d=gallery&m=free)

