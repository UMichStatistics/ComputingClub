---
title: LaTeX
linktitle: LaTeX
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  resources:
    parent: Resources
    name: LaTeX
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

## Editors

- [LyX](https://www.lyx.org/), a WYSIWYG LaTeX editor useful for quick math writing.

## Citation management

- [Zotero](https://www.zotero.org/) for local and remote bibliography management.

- [Zotero connector](https://www.zotero.org/download/connectors) for Zotero integration in browsers.

- [bibtex vs biblatex vs biber vs natbib](https://tex.stackexchange.com/questions/25701/bibtex-vs-biber-and-biblatex-vs-natbib) to understand the differences.

## Editing equations

- Use the ```\left``` and ```\right``` commands near brackets and parens to automatically size them (i.e. outer brackets will be made larger than inner brackets).
- The align environment will add a tag to each line as a separate equation. Using ```split``` within an ```equation``` or ```align``` will assign one label to all lines.
- You can use the ```\tag``` command to edit the number next to an equation 
    -  ```\tag{Hi Rob}``` will change an equation label from "(1)" to "(Hi Rob)"
    -  This can be a useful, if somewhat hacky, way to add commentary to multiline equations
- The ```\label``` command assigns an internal keyword which is used in referencing via ```\ref``` or ```\cref```, whereas ```\tag``` will change the actual label that appears in the output. 
    
## Referencing equations/figures

- The ```\Cref``` command will automatically determine what is being referenced based on the type of the object that was labelled. For example, ```\ref{mylabel}``` will display as "Equation (1)" if ```\label{mylabel}``` is next an equation and "Figure (1)" if ```\label{mylabel}``` is close to a figure.
- ```\autoref``` does something similar, but depends on a specific convention within the label. For example, you need to prepend an "eq::" so  ```\autoref{eq:mylabel}``` will show up as "Equation (1)".

## Some tips and tricks

- [Detexify](http://detexify.kirelabs.org/classify.html) to find the correct math symbol by drawing it.

- [`todonotes` package](https://www.ctan.org/pkg/todonotes) to add todo notes and comments to LaTeX files and pdf output.

- Use `\left( ... \right)` for scalable delimiters in math mode;

- Use `\Cref{...}` to get references with formatted names automatically such as "Figure 1" instead of just "1" and writing "Figure" yourself.

- Une `include` or `input` to insert the content of another `.tex` file where you want it: e.g., you can maintain a math macro file that you use often. Also, read [When should I use \input vs. \include?](https://tex.stackexchange.com/questions/246/when-should-i-use-input-vs-include)
