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

- [MRLookup](https://mathscinet-ams-org.proxy.lib.umich.edu/mrlookup) has a nice search engine to get *verified* citations for many peer-reviewed publications. You can get `BibTeX` formatted exports. Many journals require the MR number, so you can find them using that tool. Also, check out [Abbreviations of Names of Serials](https://mathscinet.ams.org/msnhtml/serials.pdf) if you want the abbreviated version of journal names.

## Editing equations

- Use the `\left` and `\right` commands near brackets and parens to automatically size them (i.e. outer brackets will be made larger than inner brackets).
- The align environment will add a tag to each line as a separate equation. Using `split` within an `equation` or `align` will assign one label to all lines.
- You can use the `\tag` command to edit the number next to an equation 
    -  `\tag{Hi Rob}` will change an equation label from "(1)" to "(Hi Rob)"
    -  This can be a useful, if somewhat hacky, way to add commentary to multiline equations
- The `\label` command assigns an internal keyword which is used in referencing via `\ref` or `\cref`, whereas `\tag` will change the actual label that appears in the output. 
    
## Referencing equations/figures

- The `\Cref` command will automatically determine what is being referenced based on the type of the object that was labelled. For example, `\ref{mylabel}` will display as "Equation (1)" if `\label{mylabel}` is next an equation and "Figure (1)" if `\label{mylabel}` is close to a figure.
- `\autoref` does something similar, but depends on a specific convention within the label. For example, you need to prepend an `eq:` so  `\autoref{eq:mylabel}` will show up as "Equation (1)".

## Some tips and tricks

- Check out [Detexify](http://detexify.kirelabs.org/classify.html) to find the correct math symbol by drawing it.

- Check out the [`todonotes` package](https://www.ctan.org/pkg/todonotes) to add todo notes and comments to LaTeX files and pdf output.

- Use `include` or `input` to insert the content of another `.tex` file where you want it. For example, you can maintain a math macro file that you use often or organize your sections/chapters in different files. Also, read [When should I use \input vs. \include?](https://tex.stackexchange.com/questions/246/when-should-i-use-input-vs-include).
