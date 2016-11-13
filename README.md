# travisci-gcc-arm-test

[![Build Status](https://travis-ci.org/karlding/travisci-gcc-arm-test.svg?branch=master)](https://travis-ci.org/karlding/travisci-gcc-arm-test)

Test Travis CI integration with GCC ARM projects using Throw The Switch's [Unity](http://www.throwtheswitch.org/unity/) unit-testing framework for C unit tests.

This is a test repository that demonstrates a proof-of-concept for the [University of Waterloo](https://uwaterloo.ca/)'s [Midnight Sun Solar Rayce Car team's](http://www.uwmidsun.com/) software team (our GitHub organization can be found at [uw-midsun](https://github.com/uw-midsun)).

## Usage
To use, just enable the Travis CI integration for your project, and then modify the ``.travis.yml`` file as appropriate. Currently, the configuration has Travis:

1. Install dependencies from the ppas
2. Build GNU Make from source

After cloning the project repository, it updates all the submodules using

```bash
git submodule update --init --recursive
```

And then builds a project:

```bash
make build_all PLATFORM=$PLATFORM
```

Our ``Makefile`` is set up such that it returns the exit code in ``$?``. So Travis CI will detect that ``make`` failed, and will report the appropriate error code.

We're also making use of Travis' build matrix, to test a wide variety of environments. Essentially, by declaring certain options, Travis will take those options, and run a build for every possible permutation of the options. In ``.travis.yml``, this is done by:

```yaml
env:
  - PLATFORM=x86
  - PLATFORM=stm32f0xx
```

The following code block will make Travis run twice, once for each version of ``PLATFORM``. Any new platforms should be added here to the build matrix.
