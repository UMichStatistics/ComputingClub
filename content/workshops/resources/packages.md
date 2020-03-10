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
```r
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
```
Here is the smoke-test we might right. 
Notice that the output is not checked; we just want to check if there are any errors.
```r
smoke_test <- function(test_input) {
    sqrt_1(test_input) # will raise an error
    sqrt_2(test_input) # will not raise an error, but is problematic
}

smoke_test(2)
smoke_test(3.14)
smoke_test(-2)
```

## The Unit Testing paradigm

[Test-driven development](https://en.wikipedia.org/wiki/Test-driven_development)

### Optimal workflow with an example

We want to implement a square root function with the following behaviour:

- returns the square root for positive input
- returns the complex square root for negative input
- is vectorized and return vectors/matrices with the same dimension
- if one input is negative, all outputs are in complex form
- raises an appropriate error if the input is not numeric (or any element of the input is not numeric)

Before writing the function, we could write the following tests:

- `sqrt(1) = 1`
- `sqrt(-1) = 0+1i` (depends on how complex numbers are implemented)
- `sqrt([0, 1]) = [0, 1]`
- `sqrt([[0], [-1]]) = [[0+0i], [0+1i]]`
- `sqrt("a")` raises an error
- `sqrt([0, "A"])` raises an error

Then, we implement our function checking tests constantly until all criterions are satisfied. 

Some (most) IDEs can automatically run all your tests in the background when any file is saved: this checks the current function your are implementing and also that you did not break any prior developments. This constant checking enable you to quickly diagnose the problem as only your latest edits change the result of tests.

### Another approach

In practice, before writing a specific function, we might not know exactly what it's behaviour will be so it is not clear what tests to write beforehand. (I often get excited about implementing something and writing tests is boring...)

So, instead of writing the tests before the function, we can wait until we are satisfied with the behaviour of a function and *protect* it with tests. Then, interactions with future functions will have some safeguards against bad input or output. Also, any further changes you perform on the function will have to satisfy the tests you previously wrote so any functions depending on the current function should not break.

Furthermore, the creation of tests *after* the function may tell you that you have to refactor some parts of your function. When first writing it, you might not have thought of some edge case and the time spent wirting tests may uncover those cases.

### What to test

- Known output (e.g., simple cases you can compute by hand)
- In/out typing (behaviour under bad input, correct output given input)
- Output dimensions (column vs row vector, do you drop a dimension if it has length 1, etc.)
- Expected errors

### Some notes

- Unit testing is great for interactive languages to detect if you are inadvertantly using global variables (defined outside the scope of a function). The test suite runs outside your scripts so tests will fail if you do so.

## Unit Testing in `R` using the `testthat` package

Let's create a simple `R` package in `RStudio`:

- `New Project`
- `R Package`
- `New Project`
- Put in some name
- Check `Open in new session`

Let's add the above defined functions in the `hello.R` file.

Let's create some tests:

- Run `devtools::test()` and type in `1` to create the `tests` directory, which contains a `testthat.R` file managing imports and helps in running all tests at once, and a sub-directory `testthat` where we will add some test;
- Run test using `Build` > `Test Package` or simply type `Ctrl+Shift+T` or run `devtools::test()`. You should see an output saying there are no tests in the `testthat` directory (as expected).
- Create a `test_sqrt_1.R` file in `tests/testthat` (NB: all test file must start with `test` so it can be discovered by the `testthat` package.)
- At the head of the file, add `context("Test sqrt functions") which will yield a more verbose output.
- Add a first test (note the near-grammarly syntax: the first argument is what we are *testing that `sqrt_1()` works on positive input*):
```r
test_that(
    "sqrt_1() works on positive input", # what we are testing
    { # the test itself, using expect statements
        expect_equal(sqrt_1(1.0), 1.0)
        expect_equal(sqrt_1(0.0), 0.0)
    }
)
```
- Run tests again and observe that our function passes all tests so far.
- Let's add another succeding test, but on an expected non-successfull call:
```r
test_that(
    "sqrt_1 raises an error with negative inputs",
    {
        expect_error(sqrt_1(-1.0), "non-numeric argument")
    }
)
```
- Running all tests should again suceed.
- Now, let's add a test which fails:
```r
test_that(
    "sqrt_1 returns imaginary numbers for negative inputs",
    {
        expect_match(sqrt(-1.0), "1i")
    }
)
```

## Unit Testing in `Python` using the `unittests` package


## Resources

