# how-to-and-practical-experience
A collection of how to's and practical experience

## Organize your c++ Project

### Project structure

My solution of project structure.

 1. The following directory structure is under version management system
&lt;project-name>                           <── project home directory
 ├──CMakeLists.txt                       <── main cmake file
 ├──Doxyfile.in                          <── cmake config file (Doxyfile input). cmake generates output file named 'Doxyfile'
 ├──readme.md                            <── readme content
 ├──include                              <── include directory, contains:
 │   └──&lt;project-alias-name>             <──  * subdirectory for this project and
 │       ├──&lt;project-cfg-file>.in        <──  * cmake config file (header input). cmake generates output file named '&lt;project-cfg-file>'. This can also be in subdirectory, main there is one.
 │       └──&lt;project-header-files>       <──  * header files and possible subdirectories for this project (only for this project!)
 ├──src                                  <── sorce directory, contains:
 │   └──&lt;project-source-files>           <──  * source files only for this project! (subdirectories are not necessary)
 ├──test                                 <── main test directory
 │   └──...                              <── ... (in progress)
 │
 2. Not under version management system (generated files and directories)
 │
 ├──Makefile                             <── from cmake generated Makefile
 ├──build                                <── binary output directory
 │   ├──obj                              <── objects directory
 │   │   └──&lt;object-files>               <── generated objects
 │   └──out                              <── binary output directory (library or executable)
 │       └──&lt;pr>&lt;project-alias-name>&lt;po> <── project result (pr - prefix, po - postfix)
 ├──doc                                  <── generated documents
 │   └──...                              <── ... (in progress)
 └──...                                  <── other generated files
