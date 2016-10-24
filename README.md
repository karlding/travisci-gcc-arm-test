# travisci-gcc-arm-test

[![Build Status](https://travis-ci.org/karlding/travisci-gcc-arm-test.svg?branch=master)](https://travis-ci.org/karlding/travisci-gcc-arm-test)

Test TravisCI integration with GCC ARM projects using Throw The Switch's [Unity](http://www.throwtheswitch.org/unity/) unit-testing framework for C unit tests.

This is a test repository that demonstrates a proof-of-concept for the [University of Waterloo](https://uwaterloo.ca/)'s [Midnight Sun Solar Rayce Car team's](http://www.uwmidsun.com/) software team (our GitHub organization can be found at [uw-midsun](https://github.com/uw-midsun)).

## Usage
To use, just enable the Travis CI integration for your project, and then modify the ``.travis.yml`` file as appropriate. Currently, the configuration has Travis:

1. Install dependencies from the ppas
2. Add trusty repos and install ``gcc-arm`` from this repo
3. Build GNU Make from source

After cloning the project repository, it updates all the submodules using

```bash
git submodule update --init --recursive
```

And then builds a project:

```bash
make project PROJECT=queue PLATFORM=x86 CFLAGS='-std=c99'
```

When integrating this into Midnight Sun firmware repository, we should update our ``Makefile`` to support building all the projects and running all our unit tests, so we don't have to update the ``.travis.yml`` file each time with each new project.
