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




Now that you are happy with your local website, it is time to deploy it on the internet. Here is the methodology for UMich personal space hosting.

See [Web Hosting Tutorial from ITS](http://www.umich.edu/~umweb/how-to/homepage.html) for more details.

## A note on the Academic theme

To ensure links consistency within your website you need to tell Hugo what will be your base URL. In the case of GitHub hosting, change the following line in `config/_default/config.toml`:
```shell
baseurl = "http://www-personal.umich.edu/~uniqname/"
```

Run `hugo` to make your changes effective.

## Prerequisites

First, you will need access to the [MFile](https://mfile.umich.edu/) system. There, ensure you have access to your `Public/html/` folder which is where we will dump our website.

You may need to [use the make-website tool](https://mfile.umich.edu/make-webspace/).

## Local version control

While version control is not necessary for this type of hosting, I highly recommend you do it locally:
```git
git add -all
git commit -m 'First deploy'
```

## Deployment with SCP

The deployment to your personal space can be done in one command line (should work on any platform, Windows users may require [PuTTY](https://putty.org/)):
```shell
scp -r <path-to-local-website>/public/. uniqname@login.itd.umich.edu:Public/html/
```
You should be prompted to enter your password. SCP (Secure Copy Protocol) can only copy files to and from a remote server. It is sufficient to push your website, but you cannot remove files using that protocol. This line basically copies everything from `<path-to-local-website>/public/` (recursively with the `-r` option) to your personal space `uniqname@login.itd.umich.edu:Public/html/` which is where websites are hosted.




### SFTP and SFTP With a GUI

`sftp` (Secure File Transfer Protocol) offer an interactive session and is therefore more flexible than SCP (see thig [guide](https://www.jscape.com/blog/using-sftp-on-command-line)). 

Open a terminal in the `public` folder of your website (or the one where Hugo produces the `html` files). Connection to the remote server is done via
```shell
sftp uniqname@sftp.itd.umich.edu
```
You should be prompted to enter your password. You can navigate your personal space usin `ls` and `cd` as usual. Move to `Public/html` and push all the files of `public`:
```shell
sftp> cd Public/html/
sftp> put -r *
```

The same can be done using a FTP client GUI (e.g. WinSCP or FileZilla). The server is called
```shell
sftp.itd.umich.edu
```
with port 22. You should need to input your username and password at some point.

### Viewing your website

Your new website will be available at
```shell
http://www-personal.umich.edu/~uniqname/
```
which is also available by symply typing
```shell
umich.edu/~uniqname/
```

If you are creating a website for some organization, consider getting some space for your organization instead of using your own space: check [this tutorial (Special services section)](http://www.umich.edu/~umweb/how-to/homepage.html).

