[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Build Status](https://travis-ci.org/softwarejimenez/hello_world.svg?branch=master)](https://travis-ci.org/softwarejimenez/hello_world)
[![codecov](https://codecov.io/gh/softwarejimenez/hello_world/branch/master/graph/badge.svg)](https://codecov.io/gh/softwarejimenez/hello_world)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/b796be85572342a5a36af07adcfb4a43)](https://www.codacy.com/app/ajimenez/hello_world?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=softwarejimenez/hello_world&amp;utm_campaign=Badge_Grade)

# hello_world
This repository is a hello_world to use different tools as CMake, Travis and CodeCoverage.

## Clone the repository

```bash
    git clone https://github.com/softwarejimenez/hello_world.git
    cd hello_world
```

## C and CPP language

### Compile applications with CMake

```bash
    mkdir -p build && cd build
    cmake -DCMAKE_BUILD_TYPE=Release|Debug <-DBUILD_C=ON|-DBUILD_CPP=ON> <-DCODE_COVERAGE=ON> ..
    cmake --build . --config Release|Debug
```

### Execute the C and CPP test
```bash
    cd build
    ctest -V
```

### Execute the C and CPP application
```bash
    cd bin
    ./hello_world_c<d>
    ./hello_world_cpp<d>
```

## Java language

### Compile applications with Gradle

```bash
    gradle build
```

### Execute the Java application
```bash
    gradle run
```

## Python language

### Execute the Python application

```bash
    cd src/src_python
    python hello_world_python.py
```
