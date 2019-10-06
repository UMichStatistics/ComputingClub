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

Now that you are happy with your local website, it is time to deploy it on the internet. Here is the methodology for GitHub Pages hosting.

## A note on the Academic theme

If you build your website using Hugo and the Acadmic theme, here's how to ensure the static website falls in the correct folder. In the `config/_default/config.toml` file change the following line:
```
publishDir = "docs"
```
To ensure links consistency within your website you need to tell Hugo what will be your base URL. In the case of GitHub hosting, change the following line in `config/_default/config.toml`:
```
baseurl = "https://your-github-account.github.io/academic-kickstart/"
```

Run `hugo` to make your changes effective.

## Local version control

In order to eventually push your website to your GitHub repository, your local files should be staged and committed:
```git
git add -all
git commit -m 'First deploy'
```

## Push your files to your repository

Then, you need to send your files to your GitHub repository.
```git
git push
```
While GitHub only requires the `docs` folder to display your website, it is best to push all the content of your website if you want to make changes from other machines.

## Hosting

At this point, the `docs` folder of your repository contains the necessary files to have a functionning website. However, you need to activate the hosting feature of your repository for GitHub to start hosting the contents of `docs`. In the *Settings* tabs of your repository, scroll down to the *GitHub Pages* section. There, use the drop-down menu under *Source* to `master branch /docs folder`.

Wait a few seconds and check out your awesome website!

## Modifying your website

You will most likely want to add or edit content to your website. To do this, you only need to alter the `docs` folder accordingly. Each update may not be instantaneous, so don't worry if it takes a few seconds before your changes to become effective.

