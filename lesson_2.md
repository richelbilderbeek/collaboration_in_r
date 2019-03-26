# Lesson 2


## Setup

 * Package name: `cirtwo`
 * Documentation: roxygen2
 * Travis CI: enabled

### `.travis.yml`

```
language: r
cache: packages
```

### README.md

```
# cirtwo

Lessen 2 of [collaboration_in_r](https://github.com/richelbilderbeek/collaboration_in_r).

Branch|[Travis](https://travis-ci.org)|[Codecov](https://www.codecov.io)
---|---|---
`master` |[![Build Status](https://travis-ci.org/richelbilderbeek/cirtwo.svg?branch=master)](https://travis-ci.org/richelbilderbeek/cirtwo)|[![codecov.io](https://codecov.io/github/richelbilderbeek/cirtwo/coverage.svg?branch=master)](https://codecov.io/github/richelbilderbeek/cirtwo/branch/master)
`develop`|[![Build Status](https://travis-ci.org/richelbilderbeek/cirtwo.svg?branch=develop)](https://travis-ci.org/richelbilderbeek/cirtwo)|[![codecov.io](https://codecov.io/github/richelbilderbeek/cirtwo/coverage.svg?branch=develop)](https://codecov.io/github/richelbilderbeek/cirtwo/branch/develop)
```

## Issues

### Become a collaborator

 * Difficulty: 1/10

Share @richelbilderbeek your GitHub username and he'll add you as a Collaborator.

### Add your branch

 * Difficulty: 1/10

Create a branch with your name at the GitHub website

### Show your branch's build status

 * Difficulty: 1/10

Create a branch with your name at the GitHub website.

Do this below the `develop` branch.

```
Branch|[![Travis CI logo](pics/TravisCI.png)](https://travis-ci.org)|[![Codecov logo](pics/Codecov.png)](https://www.codecov.io)
---|---|---
`master` |[![Build Status](https://travis-ci.org/richelbilderbeek/cirtwo.svg?branch=master)](https://travis-ci.org/richelbilderbeek/cirtwo)|[![codecov.io](https://codecov.io/github/richelbilderbeek/cirtwo/coverage.svg?branch=master)](https://codecov.io/github/richelbilderbeek/cirtwo/branch/master)
`develop`|[![Build Status](https://travis-ci.org/richelbilderbeek/cirtwo.svg?branch=develop)](https://travis-ci.org/richelbilderbeek/cirtwo)|[![codecov.io](https://codecov.io/github/richelbilderbeek/cirtwo/coverage.svg?branch=develop)](https://codecov.io/github/richelbilderbeek/cirtwo/branch/develop)
```

### Add `lintr` to Travis CI script

 * Difficulty: 1/10

To the `.travis.yml` script, add:

```
r_github_packages:
  - jimhester/lintr

after_success:
  - Rscript -e "lintr::expect_lint_free()"
```

### Add `covr` to Travis script

 * Difficulty: 1/10

To the `.travis.yml` script, add:

```
r_github_packages:
  - jimhester/covr

after_success:
  - Rscript -e "covr::codecov()"
```

### Add `goodpractice` to Travis script

 * Difficulty: 1/10

To the `.travis.yml` script, add:

```
r_github_packages:
  - MangoTheCat/goodpractice

after_success:
  - Rscript -e "goodpractice::gp()"
```

### Create `calc_squared` 1: use

 * Difficulty: 1/10

`calc_squared` is a function that calculates the square of a number.
It should do what a user expects it to do.

These are its tests:

```r
test_that("use", {

  skip("calc_squared: use")
  expect_true(calc_squared(1) == 1)
  expect_true(calc_squared(2) == 4)
  expect_true(calc_squared(3) == 9)
  expect_true(calc_squared(4) == 16)
  expect_equal(calc_squared(c(2, 3)), c(4, 9))
})
```

### Create `calc_squared` 2: abuse

 * Difficulty: 2/10

`calc_squared` is a function that calculates the square of a number.
It should give a readable error if the user supplies incorrect input.

These are its tests:

```r
test_that("abuse", {

  skip("calc_squared: abuse")
  expect_error(calc_squared("nonsense"), "'x' must be numeric")
  expect_error(calc_squared(NA), "'x' must be numeric")
  expect_error(calc_squared(NULL), "'x' must be numeric")
})
```

### Create `calc_cubed` 1: use

 * Difficulty: 1/10

`calc_cubed` is a function that calculates the cube of a number.
It should do what a user expects it to do.

```r
test_that("use", {

  skip("calc_cubed: use")

  expect_true(calc_cubed(1) == 1)
  expect_true(calc_cubed(2) == 8)
  expect_true(calc_cubed(3) == 27)
  expect_true(calc_cubed(4) == 256)
  expect_equal(calc_cubed(c(2, 3)), c(8, 27))
})
```

### Create `calc_cubed` 2: abuse

 * Difficulty: 2/10

`calc_cubed` is a function that calculates the cube of a number.
It should give a readable error if the user supplies incorrect input.


```r
test_that("abuse", {

  skip("calc_cubed: abuse")

  expect_error(calc_cubed("nonsense"), "'x' must be numeric")
  expect_error(calc_cubed(NA), "'x' must be numeric")
  expect_error(calc_cubed(NULL), "'x' must be numeric")

})
```

### Create `get_crown_age` 1: use

 * Difficulty: 2/10

`get_crown_age` is to get the crown age of a phylogeny.
It should do what a user expects it to do.

```r
test_that("use", {

  skip("get_crown_age: use")
  phylogeny <- ape::read.tree(text = "((A:1, B:1):1, C:2);")
  crown_age <- get_crown_age(phylogeny = phylogeny)
  expect_equal(created, 2)

  phylogeny <- ape::read.tree(text = "((A:2, B:2):1, C:3);")
  crown_age <- get_crown_age(phylogeny = phylogeny)
  expect_equal(created, 3)
})
```

### Create `get_crown_age` 2: abuse

 * Difficulty: 2/10

`get_crown_age` is to get the crown age of a phylogeny.
It should give a readable error if the user supplies incorrect input.


```r
test_that("abuse", {

  skip("get_crown_age: abuse")

  expect_error(get_crown_age("?"), "'phylogeny' must be of class 'phylo'")
  expect_error(get_crown_age(NA), "'phylogeny' must be of class 'phylo'")
  expect_error(get_crown_age(NULL), "'phylogeny' must be of class 'phylo'")

})
```














### Create `get_n_tips` 1: use

 * Difficulty: 2/10

`get_n_tips` is to get the number of tips of a phylogeny.
It should do what a user expects it to do.

Write the function and tests yourself.

### Create `get_n_tips` 2: abuse

 * Difficulty: 2/10

`get_n_tips` is to get the number of tips of a phylogeny.
It should give a readable error if the user supplies incorrect input.

Write the function and tests yourself.
