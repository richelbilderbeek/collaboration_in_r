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
Branch|[![Travis CI logo](pics/TravisCI.png)](https://travis-ci.org)|[![Codecov logo](pics/Codecov.png)](https://www.codecov.io)
---|---|---
`master` |[![Build Status](https://travis-ci.org/ropensci/cirtwo.svg?branch=master)](https://travis-ci.org/ropensci/cirtwo)|[![codecov.io](https://codecov.io/github/ropensci/cirtwo/coverage.svg?branch=master)](https://codecov.io/github/ropensci/cirtwo/branch/master)
`develop`|[![Build Status](https://travis-ci.org/ropensci/cirtwo.svg?branch=develop)](https://travis-ci.org/ropensci/cirtwo)|[![codecov.io](https://codecov.io/github/ropensci/cirtwo/coverage.svg?branch=develop)](https://codecov.io/github/ropensci/cirtwo/branch/develop)
```

## Issues

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
`master` |[![Build Status](https://travis-ci.org/ropensci/cirtwo.svg?branch=master)](https://travis-ci.org/ropensci/cirtwo)|[![codecov.io](https://codecov.io/github/ropensci/cirtwo/coverage.svg?branch=master)](https://codecov.io/github/ropensci/cirtwo/branch/master)
`develop`|[![Build Status](https://travis-ci.org/ropensci/cirtwo.svg?branch=develop)](https://travis-ci.org/ropensci/cirtwo)|[![codecov.io](https://codecov.io/github/ropensci/cirtwo/coverage.svg?branch=develop)](https://codecov.io/github/ropensci/cirtwo/branch/develop)
```

### Add `lintr`

 * Difficulty: 1/10

To the `.travis.yml` script, add:

```
r_github_packages:
  - jimhester/lintr
  - MangoTheCat/goodpractice

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

```
expect_true(calc_squared(1) == 1)
expect_true(calc_squared(2) == 4)
expect_true(calc_squared(3) == 9)
expect_true(calc_squared(4) == 16)
```

### Create `calc_squared` 2: abuse

 * Difficulty: 2/10


```
expect_error(calc_squared("nonsense"), "'x' must be numeric")
expect_error(calc_squared(NA), "'x' must be numeric")
expect_error(calc_squared(NULL), "'x' must be numeric")
expect_equal(calc_squared(c(2, 3)), c(4, 9))
```

### Create `calc_cubed` 1: use

 * Difficulty: 1/10

```
expect_true(calc_cubed(1) == 1)
expect_true(calc_cubed(2) == 8)
expect_true(calc_cubed(3) == 27)
expect_true(calc_cubed(4) == 256)
```

### Create `calc_squared` 2: abuse

 * Difficulty: 2/10

```
expect_error(calc_cubed("nonsense"), "'x' must be numeric")
expect_error(calc_cubed(NA), "'x' must be numeric")
expect_error(calc_cubed(NULL), "'x' must be numeric")
expect_equal(calc_cubed(c(2, 3)), c(8, 27))
```

