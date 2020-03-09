---
title: Package Development
linktitle: Packages
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  resources:
    parent: Resources
    name: Packages
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

## Smoke Testing
[Wikipedia](https://en.wikipedia.org/wiki/Smoke_testing_(software))

Smoke testing is a quick and easy way to check if code works. 
If your program can't even run without crashing, there's no point to performing more fine-grained testing procedures.

    sqrt_1 <- function(x) {
        if (x >= 0) {
            ret <- x^(0.5)
        } else {
            ret <- (-x)^(0.5) + "i"
        }
        return(ret)
    }

    sqrt_2 <- function(x) {
        if (x >= 0) {
            ret <- x^(0.5)
        } else {
            ret <- paste0((-x)^(0.5), "i")
        }
        return(ret)
    }
    
Here is the smoke-test we might right. 
Notice that the output is not checked; we just want to check if there are any errors.

    smoke_test <- function(test_input) {
        sqrt_1(test_input) # will raise an error
        sqrt_2(test_input) # will not raise an error, but is problematic
    }
    
    smoke_test(2)
    smoke_test(3.14)
    smoke_test(-2)

## Unit Testing

## Resources

