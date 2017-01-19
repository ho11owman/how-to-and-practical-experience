# How to & practical experience

A collection of how to's and practical experience with c++development and helpfull tools.

## 1 Organize your c++ Project

### 1.1 Project structure

My solution of project structure.

#### 1.1.1 The following directory structure is under version management system

```sh
&lt;project-name&gt;                           <── project home directory  
 ├──CMakeLists.txt                       <── main cmake file  
 ├──Doxyfile.in                          <── cmake config file (Doxyfile input). cmake generates output file named 'Doxyfile'  
 ├──readme.md                            <── readme content  
 ├──include                              <── include directory, contains:  
 │   └──&lt;project-alias-name&gt;             <──  * subdirectory for this project and  
 │       ├──&lt;project-cfg-file&gt;.in        <──  * cmake config file (header input). cmake generates output file named '&lt;project-cfg-file&gt;'. This can also be in subdirectory, main there is one.  
 │       └──&lt;project-header-files&gt;       <──  * header files and possible subdirectories for this project (only for this project!)  
 ├──src                                  <── sorce directory, contains:  
 │   └──&lt;project-source-files&gt;           <──  * source files only for this project! (subdirectories are not necessary)  
 ├──test                                 <── main test directory  
 │   └──...                              <── ... (in progress)  
 │  
 ```
 2. Not under version management system (generated files and directories)
 │
 ├──Makefile                             <── from cmake generated Makefile
 ├──build                                <── binary output directory
 │   ├──obj                              <── objects directory
 │   │   └──&lt;object-files&gt;               <── generated objects
 │   └──out                              <── binary output directory (library or executable)
 │       └──&lt;pr&gt;&lt;project-alias-name&gt;&lt;po&gt; <── project result (pr - prefix, po - postfix)
 ├──doc                                  <── generated documents
 │   └──...                              <── ... (in progress)
 └──...                                  <── other generated files
