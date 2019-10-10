---
title: Troubleshooting
linktitle: Troubleshooting
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  hugo_academic:
    parent: Personal Academic Website Using Hugo
    name: Troubleshooting
    weight: 5

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 5
---

## Hugo errors

If you encounter the following error:
```shell
Error: "...\DemoWebsite\config.toml:1:1": unmarshal failed: Near line 0 (last key parsed ''): bare keys cannot contain '.'
```
or any other error the first time you call a `hugo` comment, make sure you have the **Extended** version of Hugo installed. You can check by typing
```shell
hugo version
```
The output should contain the `extended` word somewhere (depends on the OS). 
