# Beardog - generate documents with style!

## Overview
Beardog is a system that can be used to generate documents, but we prefer to say it's a
system for *programmming* documents. It adds variables, loops, templates, macros and similar
in order to optimize the amount of present boilerplate code.

## How to compile
It's a CMake based project using conan package manager. Please make sure to install [conan](https://conan.io/). 

### If using CLion
Generate `conanbuildinfo.txt` file with the following:
```bash
conan install . -s build_type=Debug --install-folder=cmake-build-debug
```
You should be able to build the project directly from CLion afterwards.

### If using terminal only
```bash
mkdir build
conan install . -s build_type=Debug --install-folder=build
cd build
cmake ..
make
```
