# How to & practical experience

A collection of how to's and practical experience with c++development and helpfull tools.

## 1 Organize your c++ Project

### 1.1 Project structure

My solution of project structure. The following directory structure is under version management system.

```sh
<project-name>                           <── project home directory  
 ├──CMakeLists.txt                       <── main cmake file  
 ├──Doxyfile.in                          <── cmake config file (Doxyfile input). cmake generates output file named 'Doxyfile'  
 ├──readme.md                            <── readme content  
 ├──include                              <── include directory, contains:  
 │   └──<project-alias-name>             <──  * subdirectory for this project and  
 │       ├──<project-cfg-file>.in        <──  * cmake config file (header input). cmake generates output file named '<project-cfg-file>'. This can also be in subdirectory, main there is one.  
 │       └──<project-header-files>       <──  * header files and possible subdirectories for this project (only for this project!)  
 ├──src                                  <── sorce directory, contains:  
 │   └──<project-source-files>           <──  * source files only for this project! (subdirectories are not necessary)  
 ├──test                                 <── main test directory  
 │   └──...                              <── ... (in progress)  
 │  
 ```
 
 ## GitHub Hallo Word Project
 ***Step 1***
  ```sh
 path/to/your/global/project/dir> mkdir <project/repository-name>
 path/to/your/global/project/dir> cd <project/repository-name>
 ```
 ***Step 2***
 read the conten of [GitHub Hallo Word Project][1]
 ***Step 3***
 ```sh
 path/to/your/global/project/dir> git clone git@github.com:<user-name>/<project-name>.git .
 ```
 
 
 [1]: https://guides.github.com/activities/hello-world/
 
 
