---
title: "Building & Hosting a Simple Academic Website"
subtitle: "Using Hugo, GitHub Pages and UM personal space"
author: "Simon Fontaine - UM Statistics Computing Club"
date: "October 9th, 2019"
output:
  ioslides_presentation:
    highlight: espresso
    keep_md: true 
    widescreen: true
    logo: ../../../static/img/icon-512.png
  beamer_presentation:
    highlight: espresso
---


## Contents

- How to **create a website** using Hugo and the Academic theme;
- Two ways to **host your website**:
    - GitHub Pages;
    - UMich personal space.

**Disclaimer:**

- You won't learn anything that will make you a better statistician and researcher.



## Why have a personal academic website

**Professional goals**

- Host a public resume; list your publications, research interests, experience, etc.
- Allows people to find you and contact you; easy way to point to you
- Build your "online presence"

**Exposure for your work & research**

- Build workshops, courses and tutorials for everyone to access
- Present your research in alternative ways

**Host content for courses**

- e.g. Canvas may have some limitations that a website might not have
- Make your teaching content public
  


## Why have a personal academic website (cont'ed)

Have a website **before** you need one:

- It is a tidy place to keep track of your publications, talks, accomplishments, etc.
- You don't want to spend time building a website when you're looking for internships/jobs/grants/contributors/etc.

It is also a **humbling experience**:

- The first time you set up your own website, you will most likely have very few things to put on it;
- Additional motivation and incentive to build your image and career.



## Other uses for simple website

- Research group page
- Student organization
- Documenting a software or package you developed
- Online book
- Artist portfolio
- Blogging
- Event/symposium/conference landing page
  


## A quick primer on (static) websites

- Static `html` pages;
- Multiples pages arranged into a tree; leaves are the visible pages;
- No one should write `html` themselves: 
    - use tools and other languages to generate it;
- `index.html` has a special status within a folder
    - `site/subdir/` automatically loads `site/subdir/index.html`



## About Hugo

- Framework for developing websites;
- `Markdown` and `toml` > `Go` engine > `html`;
- Multiples themes for different kind of websites.



## Markdown file front matters

The top part of any `.md` file contains a **front matter** defining:

- a high-level description of the page, 
- the type of page to specify to the Hugo compiler, 
- some details about indexing and referencing across pages.



## Example: blog post

```yaml
---
# Front matter
title: "MyFirstPost"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2019-10-04T18:18:52-04:00
lastmod: 2019-10-04T18:18:52-04:00
featured: false
draft: false
---

The content of the post goes here
...
```


## The Academic theme for Hugo

The [Academic theme](https://themes.gohugo.io/academic/) which is one of the **more complete themes** and is particularly **well-suited for an academic website** (as the name suggests!) Here are some of the things Academic allows:

- Publications and talks 
- Documentation (courses, workshops, documentation)
- Blog posts
- Projects
- Multiple authors
- General pages
- Home page with widgets structure



## More Hugo themes
- [Hugo website](https://themes.gohugo.io/) and [THEMEFISHER](https://themefisher.com/hugo-themes/): other themes;
- [Academia](https://gethugothemes.com/products/academia/): 30$, very similar to Academic, slightly different visuals;
- Resume-type themes: [Resume](https://themes.gohugo.io/hugo-resume/),  [Orbit](https://hugothemesfree.com/my-cv-resume-using-a-free-hugo-theme/);
- Documentation-type themes (many equivalent options)
- Portofolio-type themes (many equivalent options)
- Blog-type themes (many equivalent options)



## Alternatives to Hugo
HTML from scratch

- Highly not recommended

[Jekyll](https://jekyllrb.com/)

- Very similar to Hugo (all content is `Markdown`, similar `shell` commands)
- Slightly more complicated, but has slightly more features
- I have not found a theme that matches the capabilities of Academic for Hugo (see e.g. [Jekyll Academic](https://ncsu-libraries.github.io/jekyll-academic-docs/) and its [demo site](http://ncsu-libraries.github.io/jekyll-academic/))
- GitHub Pages built-in themes (using Jekyll) can be up in a few clicks


## Alternatives to Hugo (cont'ed)

WYSIWYG editor

- [WordPress](https://wordpress.com/)
- [Google Sites](https://sites.google.com/site/sites/)
- [WiX](https://www.wix.com/)
- and many others

More advanced alternatives

- [Grav](https://grav.com/)
- [Drupal](https://www.drupal.org/)



## Alternative hosting

- [Netlify](https://www.netlify.com/) (linked with a GitHub repository, auto-deployment)
- [WordPress](https://wordpress.com/) and [WiX](https://www.wix.com/) offers free hosting options
- Any other web host ($, e.g. [AWS](https://aws.amazon.com/websites/))



## Main takeaways

- Creating your own website is **easy** and you should definitely do it soon.
- People have made it easy for you to display your work; **make use of all the tools available**! 
- **Creating the content** for your website, **not building and deploying it**, should consist most of the work you have to do. 
- Hugo & the Academic theme are simple and powerful, but other ways are also interesting!

[**To the workshop**](https://umichstatistics.github.io/ComputingClub/workshops/hugo_academic/initialize/)
