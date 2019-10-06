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

This part of the workshop is about creating your website using the Hugo engine and the Academic theme. Most of the following is a summary or reinterpretation of the [Academic theme documentation](https://sourcethemes.com/academic/docs/).

For more details about Hugo itself, see [Hugo Getting Started](https://gohugo.io/getting-started)

## Prerequsites

In order to perform the following manipulations, you will need:

- Hugo installed on your machine: see this [guide](https://gohugo.io/getting-started/installing/); ( Windows users: I highly recommend [installing Chocolatey](https://chocolatey.org/install) and installing Hugo from command line.)
- git installed on your machine (see this [guide](https://www.atlassian.com/git/tutorials/install-git));
- a [GitHub](http://github.com) account.

## Initialize and first deploy

(Based on [Academic theme documentation: Install with Git](https://sourcethemes.com/academic/docs/install/#install-with-git))

The Academic theme is hosted in a [GitHub repository](https://github.com/gcushen/hugo-academic), but we don't want to build the website from scratch. 

In order to initialize the website with some things already done for us, we'll use the [Academic kickstart website](https://github.com/sourcethemes/academic-kickstart#fork-destination-box). You need to **fork the  repository** into a repository in your own account. Then, the Academic theme is only linked to the kickstart site we are cloning and we need to keep the dependencies alive.

Now that your GitHub account contains the Academic kickstart clone, clone that repository on your local machine:
```shell
git clone https://github.com/<your-github-account>/academic-kickstart.git DemoWebsite
cd DemoWebsite
```

As mentionned, your GitHub repository only contains the link to the Academic theme, so you need to clone recursively:
```shell
git submodule update
```

Now, your `DemoWebsite` folder contains all the neccessary to deploy the Academic kickstart website locally. First, we produce the `html` files from the `Markdown` source: in the `DemoWebsite` folder, run
```shell
hugo
```
At this point, Hugo should have produced the `html` files in a new `public` subdirectory. Then, in order to view yhte new content as a proper website, you will need to serve the website locally. Fortunately, Hugo has a built-in feature to do that: simply run
```shell
hugo server
```
The output should contain a line like
```shell
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
```
which means that your new website is now accessible at the local address http://localhost:1313/.

Something interesting about `hugo server` is that it will rebuild your website anytime you make a change to the `DemoWebsite` directory. That is, it runs a `FastRender` version of the `hugo` command. So, if you make changes to a file, then you can see its effect directly (most web browser have some sort of auto-refresh so you don't have to refresh the page yourselves!) Note that deeper changes (e.g. new pages) won't appear in that `FastRender` mode so you will need to exit the server (`Ctrl+C`) and restart it (alternativley, you can deactivate the `FastRender` mode using `hugo server --disableFastRender`). 

## Content and first edits

Now that we have successfully deployed the Academic kickstart site, it is time to take a look at the specefics of it. Your `DemoWebsite` directory should now contain numerous files and folders. The one of interest to us is the `content` folder which, as the name indicates, contains all the content of the website. 

```shell
content
├── authors
├── home
├── post
├── publication
└── talk
```

### Authors

The `authors` subdirectory is used to store the different authors for your website. For now, it should only contains one author named `admin`. The `index.md` file contained in the `admin` folder controls the information about that author. In particular, it controls:

- The profile on the homepage if that author is chosen to apprea there;
- The profile appearing with talks, posts and publications of that author.

To change the information about the `admin` author, simply go through the `index.md` file and edit it to your needs. It is well documented so it should be clear what everything does. 

The folder name, here `admin`, will be the index used to identify posts, publications and talks to the corresponding auythor. If you need to add additional authors to your website, simply copy the `admin` folder and change its content. The photo associated to the author should lie in the same folder and have name `avatar.jpg/.png`.


### Home

The `home` folder controls what appreas on the home page, that is, the first page a user will land on. The way the home page is structures is through *page sections* as known as *widgets*. On the home page you will see alternating backgroud; each page section is denoted by these alternating background. Thus each file in the `home` folder determines one of those page sections.

To remove some sections, there are two ways:

- Delete the corresponding `.md` file;
- Deactivate the section by setting `active = false` in the front matter.

Let us delete the following sections to clean the current home page:

- `demo`
- `hero`
- `people`
- `slider`
- `tags`

For more details on what each section does, please refer to [Getting Started with the Page Builder](https://sourcethemes.com/academic/docs/page-builder/).

One thing to note is how the section are ordered in the home page. It is done through the `weight` parameter in the front matter where the lowest `weight` value will appear first.

### Post, Publications and Talks

Each of these folder will eventually the corresponding content. These folders are structured as follows (here we consider `post`) :

```shell
post
├── _index.md
└── MyFirstPost
    └── index.md
```

The root `_index.md` defines a landing page are posts are listed. Each subdirectory then defines one post and contains a `index.md` which defines the corresponding post. 

To create new content, use the following command:

```shell
hugo new --kind <post/publication/talk> <folder>/<name-of-content>
```

For example, to create a new publication with identifyer `Publication1`, type
```shell
hugo new --kind publication publication/Publication1
```

Create a few posts, publications and talks and restart the server since you have now added new pages to the site (`Ctrl+c` and `hugo server`).


### Courses, workshops, documentation

If you wish to have space for courses, documentation or workshops, the best way to go is to use the `docs` layout defined by the Academic theme. For example, let us create a `course` folder in the `content` folder and place a `_index.md` file at its root. This file should only contains the following front matter
```shell
title: Courses
layout: docs
```
Just like posts, publications and talks, this file will define a page listing all courses contained in the directory. The `layout: docs` parameter means that this landing page will list pages of type `docs` only.

The Academic theme also implements a `--kind docs` argument to automatically create new `docs` files:

```shell
hugo new --kind docs course/FirstCourse
```




## Configuration

The `config` folder contains various `.toml` files which define site-wide information and parameters.

```shell
config
└── _default
    ├── config.toml
    ├── languages.toml
    ├── menus.toml
    └── params.toml
```

All these files are fairly well-documented, so there is no reason to go over them here. One thing I would like to point out is the `menus.toml` file. The navigation bar presently links only toward page sections of the home page. If you would like them to point toward, say, `post/_index.md` instead of the post section, change the menu entry related to posts :
```toml
[[main]]
  name = "Posts"
  url = "post" # was "#posts" before
  weight = 20
```


## Rest of repository

The rest of the `DemoWebsite` repository mostly contains file used to generate the website. You should most likely not have to touch them except:

- `data`: if you want custom color theme and fonts, you will place them here;
- `static`: you can place site-wide files here, such as a custom site icon.






