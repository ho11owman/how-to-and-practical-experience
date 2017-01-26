# How to & practical experience

A collection of how to's and practical experience with c++development and helpfull tools.

## 1 Organize your c++ Project

### Project structure

After reading several post abaut project structure, i have found my own solution for this "problem".  
My goals are:

**Project Home** directory must be everytime clean
**Modularity**
It should be possible to work ++offline++
Hier is my solution of project structure for **V**ersion **C**ontrol **S**ystem.

```sh
<project-name>                           <── project home directory
 ├──CMakeLists.txt                       <── main cmake file
 ├──build                                <── build directory for cmake
 ├──cmake                                <── cmake config and more
 │   ├──CMakeLists.txt                   <── this file take care of cmake packages
 │   └──<pkg-name>                       <── directory for specific package
 │       └──...                          <── cmake package file's
 ├──doc                                  <── project relevant documentation
 │   └──...
 ├──etc                                  <── project relevant file's (build-/runtime)
 │   └──Doxyfile.in                      <── cmake config file (Doxyfile input). cmake generates output file named 'Doxyfile'
 ├──readme.md                            <── readme content  
 ├──include                              <── include directory, contains:  
 │   └──<project-header-files>           <── header's (with subdirectories) only for this project
 ├──src                                  <── sorce directory, contains:
 │   └──<project-source-files>           <──  * source files only for this project! (subdirectories are not necessary)
 ├──test                                 <── main test directory
 │   └──...                              <── ... (in progress)
 │
```

### GitHub Hallo Word Project
***Step 1***
```sh
some/project/dir> mkdir <project-or-repository-name>
some/project/dir> cd <project-or-repository-name>
```


***Step 2***
>Read the conten of [GitHub Hallo Word Project][1].


***Step 3***
```sh
path/to/your/global/project/dir> git clone git@github.com:<user-name>/<project-name>.git .
```








[1]: https://guides.github.com/activities/hello-world/
