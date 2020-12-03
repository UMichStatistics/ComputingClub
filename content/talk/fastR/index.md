---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Speeding up R with C/C++/Fortran"
event: "Student Seminar"
event_url:
location: "Remote"
summary: ""
abstract: "R is a great language for statisticians because of its interactivity, simple syntax and access to multiple libraries produced by the community. These features also allow rapid prototyping, testing and debugging of new methods; however, the short implementation time is often outweighed by long execution times. To produce more efficient code and libraries, R possess simple interfaces to other languages such as C++ and Fortran, enabling efficient runtime with limited additional implementation. Indeed, executing the core calculations of a method in a compiled language can produce speed-ups in the order of 10-100x and up to 1000x in some cases. We will consider a few examples to showcase the increase in efficiency of compiled code compared to interpreted R code and build a simple R package from scratch to exhibit the simplicity of the process.

The second part of the presentation will be of the workshop type: if you wish to follow along, you will need to have the R packages “Rcpp” and “devtools” installed. 
"

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: 2020-12-02T10:30:00-02:00
date_end: 2020-12-02T11:30:00-05:00
all_day: false

# Schedule page publish date (NOT talk date).
publishDate: 2020-10-01T15:16:15-04:00

authors: [simon]
tags: []

# Is this a featured talk? (true/false)
featured: true

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter
# Optional filename of your slides within your talk's folder or a URL.
url_slides: fastR.pdf

url_code: "https://github.com/fontaine618/fastR"
url_pdf:
url_video:



# Markdown Slides (optional).
#   Associate this talk with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
