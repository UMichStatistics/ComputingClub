---
title: Update workflow
linktitle: Update workflow
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  edit_site:
    parent: Editing the Club's website
    name: Update workflow
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

## The lazy way

If you only need to add some post/meeting/workshop to the website, here is a simple way to deploy your new content to the website without much hassle.

1. **Create your content**---The first step is to create your specific content by producing the necessary Markdown files. See [Creating content](../createcontent/) for details on how to do so.
2. **Push your content**---You then need to add your content to the website `content` directory. If you have access to the [UMichStatistics](https://github.com/UMichStatistics/) repository, then you can do it directly using your favorite 'git' workflow. Otherwise, [contact the maintainers](#contact) for them to add your content to the site.
3. **Deploy your content**---As mentionned, an update of the files outside the `docs` folder will not affect the public website. The deployment must be done through Hugo and, for now, this must be done manually. [Contact the maintainers](#contact) for it to happen.

## The good way

Hopefully, you will want to deploy your changes yourself. To do this, here is the summary of the procedure:

1. Have a local copy of the website on your machine.
2. Update your local version.
3. Deploy your local version to your localhost using Hugo in order to update the `docs` contents.
4. Push your changes, including both the source and the updated `docs` to the site's repository.

With the workflow, your changes will instantaneously update the public website. Also, since you first deploy on your local machine, you are able to see the results of your changes before them becoming public. Finally, pushing both the source and the updated `docs` prevents conflicts in future updates.

### Requirements

To use this process, you will need:

- Access to the [organization](https://github.com/UMichStatistics/) repository;
- git installed on your machine (see this [guide](https://www.atlassian.com/git/tutorials/install-git));
- Basic git knowledge (`clone`, `pull`, `add`, `commit` and `push`). Note that most modern IDEs offer git support so you may execute all those steps using your interface;
- Hugo installed on your machine (see this [guide](https://gohugo.io/getting-started/installing/). The installation on Windows is tedious and the only way I could make it work was `R` > install package `blogdown` > `blogdown::install_hugo()` and manually add its path to the system environment variables.)

### Update the local version

First, you will need the latest version of the website stored locally on your machine. 

If you have not cloned the repository yet, do so:
```shell
git clone https://github.com/UMichStatistics/ComputingClub.git <new-folder-name>
```

The website relies on the Academic theme for Hugo, so you will to clone that as well. Fortunately, it is included as a submodule of the repository, so you only need to update all submodules (there is only one):
```shell
git submodule update [--init] [--recursive]
```

If you already have cloned the repository, make sure your local version is up to date with the current online version to avoid merge conflicts when pushing. In a command prompt, move to the site local folder and `pull` the website (or `fetch` and `merge`).

### Create your content

Create your specific content by producing the necessary Markdown files and place them in the correct folders. See [Creating content](create/) for details on how to do so.

### Deploy your local website

Now that your local repository contains updated content, it is time to deploy it to your local `docs` folder. To do so, open a command prompt and run hugo at the root of the site's local repository and type in:
```shell
hugo
```
which will compile the content into the static `html` pages. Unless your code does not compile, you should get an output such as (possibly containing warnings)
```shell
Building sites … WARN 2019/09/24 17:08:23 In the next Hugo version (0.58.0) we will change how $home.Pages behaves. If you want to list all regular pages, replace .Pages or .Data.Pages with .Site.RegularPages in your home page template.

                   | EN
+------------------|----+
  Pages            | 52
  Paginator pages  |  0
  Non-page files   |  6
  Static files     |  8
  Processed images |  9
  Aliases          |  7
  Sitemaps         |  1
  Cleaned          |  0

Total in 265 ms
```
This means that Hugo has successfuly deployed your site to the `docs` folder. If you wish to view the website, you can host it locally using Hugo:
```shell
hugo server
```
which should yield something like
```shell
Watching for changes in /home/simon/git/ComputingClub/{content,data,static,themes}
Watching for config changes in /home/simon/git/ComputingClub/config.toml, /home/simon/git/ComputingClub/config/_default
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ComputingClub/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```
The url `http://localhost:1313/ComputingClub/` is where you find your local website (use the one in your output as it may differ from mine). Also, as long a you do not close the server (by closing the command prompt or by typing `Ctrl+C`), Hugo will listen to any changes, meaning that any file saved in the root repository will trigger deployment. This is useful if you want to create your content and see it deployed instantaneously locally without calling Hugo each time. Note that creating new pages or making large changes may not appear in this "Fast Render Mode", so you may need to exit and re-host. 

### Push your changes

Once your are satisfied with your local version, you need to push your changes to the `master` branch. In the case your Hugo server is still on, close it and run `hugo` one last time to redo the `docs` file for the online version, not the local version.

Stage and commit your changes:
```shell
git add --all
git commit -m 'some description of your changes'
```
and finally push to the online repository
```shell
git push
```

