# Project structure

After reading several posts abaut how to organize the c++ project structure, i have found my own solution for this "problem".

## Goals

- **Clean `project-root`:** This means, **no generated** files or subdirectories, **no** specific **IDE configs**. The `project-root` should represent **only project relevant content**.
- **Clarity:** A clear separation of sources, documentation, configuration, tests etc.
- **CMake:** Using CMake as build system.

>**Note:** Of course, the project itself should also be in the Version Control System (VCS).

## Project structure overview

Following is the minimal project structure.

```
<project-root>
 ├─build/
 │  └─<project-generated-data>
 │
 ├─doc/
 │  ├─CMakeLists.txt
 │  └─Doxyfile.in
 │
 ├─include/
 │  └─<project-include-directory>/
 │
 ├─src/
 │  └─<project-sources>
 │
 ├─test/
 │  └─...
 │
 ├─CMakeLists.txt
```

## Description

### `CMakeLists.txt`
### `build\`
### `doc\`
### `include\`
### `src\`
### `test\`
