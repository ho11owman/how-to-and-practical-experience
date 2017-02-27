# How to & practical experience

A collection of how to's and practical experience with c++development and helpfull tools.  

[Short How To about Git and GitHub][7]  
[Integrated Development Environment][8]  

## Organize your c++ Project

### Project structure

After reading several post abaut project structure, i have found my own solution for this "problem".  
  
My goals are:

- **Project Home** directory must be everytime clean
- **Modularity**
- It should be possible to work **offline**

>**Note:** Of course, this should also be in the **V**ersion **C**ontrol **S**ystem (**VCS**).
  
```
<project-root>                           <── project root directory
 ├──CMakeLists.txt                       <── main cmake file
 ├──build                                <── build directory for cmake
 ├──cmake                                <── cmake config and more
 │   ├──CMakeLists.txt                   <── this file take care of cmake packages
 │   └──<pkg-name>                       <── directory for specific package
 │       └──...                          <── cmake package file's
 ├──doc                                  <── project relevant documentation
 │   └──...
 ├──etc                                  <── project relevant file's (build-/runtime)
 │   └──Doxyfile.in                      <── cmake config file (input)
 ├──readme.md                            <── readme content  
 ├──include                              <── include directory, contains:  
 │   └──<project-header-files>           <── header's (with subdirectories) only for this project
 ├──src                                  <── sorce directory, contains:
 │   └──<project-source-files>           <── source's (with subdirectories) only for this project
 ├──test                                 <── main test directory
 │   └──...                              <── ... (in progress)
 │
```

#### Explanation

***CMakeLists.txt***

>**Note:** [CMake][1] is not only `Makefile` generator, but also a powerful tool for building, testing and packaging your software. The `CMakeLists.txt` contains instructions for cmake backend programm.

The `CMakeLists.txt`, in the `project-root` directory, is the **main** cmake file for this project. I have several `CMakeLists.txt`s in my project structure and this one triggers all other files.

***build/***

The `build/` directory contains all files generated using [CMake][1]. These are [ignored][2] by the **VCS**.

>**Note:** There are two ways to persuade the CMake to generate the files in that directory:
> - simple run [CMake][1] from this directory like this `cd build && cmake ../`
> - or from `project-root` directory like this `cmake -H. -B./build/`:
>  - -H - path to **main** `CMakeLists.txt`
>  - -B - path to run directory

***cmake/***

```
├──cmake
│   ├──CMakeLists.txt
│   ├──<package-1>
│   │   ├──Find<package-1>.cmake
│   │   ├──<package-1>Config.cmake
│   │   └──...
│   └──<package-n>
│       └──...
```

>**Note:** One of the many strengths of [CMake][1] is the [Packaging System][3]. This can try to [find][4] the package with help of `Find<package-1>.cmake` file or [configure][5] them with `<package-1>Config.cmake` and more othe.  

This work takes `CMakeLists.txt` from this directory. The content of this directory is also under **VCS**.

***doc/***

This directory contains project relevant documentation from project it self and from dependensies.

>**Note:** I'm not sure if the files in this directory should be under **VCS**.

***etc/***

```
├──etc
│   ├──Doxyfile.in
│   └──...
```

This directory contains [CMake][1] [input][6] files and should be under **VCS**.

***include/***

```
├──include
│   └──<project-alias>
│       └──<header-or-subdirs>
```

`include` directory contains `<project-alias>` with possible subdirectories.  
For example we have project named `The best idea` and we aliased it to `tbi`. The client of ouer library/project use it as folow.

```cpp
#include "tbi/the_best.h"
#include "tbi/idea.h"
```

***include/ & src/***

Directories for header and source files. 

***test/***

### Organize your CMakeLists.txt








[1]: https://cmake.org/
[2]: https://git-scm.com/docs/gitignore
[3]: https://cmake.org/cmake/help/v3.0/manual/cmake-packages.7.html
[4]: https://cmake.org/cmake/help/v3.0/manual/cmake-packages.7.html#find-module-packages
[5]: https://cmake.org/cmake/help/v3.0/manual/cmake-packages.7.html#package-configuration-file
[6]: https://cmake.org/cmake/help/v3.2/command/configure_file.html
[7]: https://github.com/ho11owman/how-to-and-practical-experience/blob/master/ShortHowToAboutGitAndGitHub.md
[8]: https://github.com/ho11owman/how-to-and-practical-experience/blob/master/IntegratedDevelopmentEnvironment.md
