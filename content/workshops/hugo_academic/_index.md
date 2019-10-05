---
# Course title, summary, and position.
linktitle: Building & Hosting a Personal Academic Website Using Hugo
summary: A tutorial on how to create a personal academic website using the Academic theme for Hugo and host to on GitHub pages or UMich personal space.
weight: 1

# Page metadata.
title: Building & Hosting a Personal Academic Website Using Hugo
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
  hugo_academic:
    name: Personal Academic Website Using Hugo
    weight: 1
---

In this tutorial, we will go through one way of setting up your personal academic website.

## Why have a personal academic website

Having a personal website serves multipe goals:

- Professional goals 
  - Host a public resume
  - List your publications, research interests, experience, etc.
  - Allows people to find you and contact you
  - Have an easy way to point to you
- Exposure for your work & research
  - Build workshops, courses and tutorials for everyone to access
  - Present your research in different ways than the classical way (articles, talks, posters, etc.)
- Host content for courses
  - e.g. Canvas may have some limitations that a website might not have
  - Make your teaching content public
  
Other uses for simple website

- Research group page
- Student organization
- Documenting a software or package you developped
- Online book
- Artist portfolio
- Blogging
  
## A quick primer on (static) websites

Most websites you encounter consits of `html` (HyperText Markup Language) code and embed other languages to allow more interaction (`javascript`, `Perl`, etc.). A website contains multiples pages, often arranged into different subdirectories, just like regular file management. Each page you access is a generally a `.html` file, but in general no one actually write `html` directly---developpers use programming languages that generate the `html` for themselves. 

The style of a page---colors, font, placement, etc.---are generally contained in `css` (Cascading Style Sheets) files.

## About Hugo

Hugo is a framework for developping websites. In particular, it generates the desired `html` pages given some developper input in `Markdown` files. The engine uses the `Go` language to interpret the `Markdown` and produce the corresponding `html` files. 

In addition to `Markdown` files, the developper also modify configuration files and `Markdown` front matters, in simple `toml` format, to determine meta-information about the website and control visual aspects. Both `Markdown` and `toml` languages have simple and intuitive syntax so the learning curve is very steep. Once the base website is setup, editing and adding content is only a matter of creating folder, creating and editing `Markdown` files and editing `toml` files.

## Markdown file front matters

An important concept to understand about `Markdown` files is the file layout. Each `.md` file must contain a front matter part which describe some meta information about the content of the file and is then follow by the content itself. In the present context, the front matters will contain, among other things, 

- a high-level description of the page, 
- the type of page to specify to the Hugo compiler, 
- some details about index and references across pages.

## The Academic theme for Hugo

Hugo has many themes which can be used as templates for your website. Different themes implement different type of contents and are therefore suited for different purpose. In this tutorial we will consider the Academic theme which is one of the more complete theme and is particularly well-suited for an academic website (as the name suggests!) Here are some of the things Academic allows:

- Blog posts
- Documentation
- Publications
- Talks
- Projects
- Multiple authors
- General pages
- Home page with widgets structure

### [All Hugo themes](https://themes.gohugo.io/)

- Resume-type themes
  - [Resume](https://themes.gohugo.io/hugo-resume/) theme is other best I found
- Documentation-type themes (many equivalent options)
- Portofolio-type themes (many equivalent options)
- Blog-type themes (many equivalent options)

## Alternatives to Hugo
- HTML from scratch
  - Highly not recommended
- Jekyll
  - Very similar to Hugo (all content is `Markdown`, similar `shell` commands)
  - Slighty more complicated, but has slightly more features
  - I have not found a theme that matches the capabilities of Academic for Hugo (see e.g. [Jekyll Academic](https://ncsu-libraries.github.io/jekyll-academic-docs/) and its [demo site](http://ncsu-libraries.github.io/jekyll-academic/))
  - GitHub Pages built-in themes (using Jekyll) can be up in a few clicks
- WYSIWYG editor
  - WordPress
  - Google Sites
  - WiX
  - and many others
- More advanced alternatives
  - Grav
  - Drupal

## Main takeaways

People have made it easy for you to display your work; make use of all the tools available! Creating the content for your website, not building and deploying it, should consist most of the work you have to do. 
