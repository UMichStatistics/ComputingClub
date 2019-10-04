---
title: Creating content
linktitle: Creating content
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  edit_site:
    parent: Editing the Club's website
    name: Creating content
    weight: 3

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

## Overview of the Academic theme layouts

The content of this website rely on three different `layouts` defined by the Academic theme. Each `.Md` must specify, in its header, what `layouts` it is based on in order for Hugo to produce the correct `html` page.

- **talk** (for meetings) and **post** (for, you guessed it, posts!)
  - Single page output;
  - The page contains a header block describing the post/meeting and that information is taken from the `Markdown` header;
  - Followed by a body for regular `Markdown` for the post or if you want to add more details to a meeting.
- **docs** (for workshops and resources)
  - Each `docs` file is associated with a single `html` page, but multiple `docs` can be associted together within a folder to form different pages of a single workshop;
  - Consists of a simple `Markdown` body;
  - A within-workshop table of content is added to the left;
  - A within-pasge table of content on the right.


## Create your author profile

First things first, you need to create an `authors` profile in order to associate multiple content to the same author. Unfortunately, Hugo does not provide a command to create a new author from command line, so the fastest way to go is to copy the `blank` author folder and give it a name representing your's (say `username` from now on). Then, edit the `_index.md` contained in the new `username` folder and edit its content. It should be documented well enough for you to complete.

If you want to add a picture of yourself, place it in the `username` folder with the name `avatar.jpg/.png`.

## Create a meeting

## Create a workshop

## Add resources

## Create a post



