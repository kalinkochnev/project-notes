# Setting/unsetting variables
```CMake
set(<variable_name> <value>)
unset(<variable_name>)
```
# Export compile_commands.json
https://cmake.org/cmake/help/latest/variable/CMAKE_EXPORT_COMPILE_COMMANDS.html#variable:CMAKE_EXPORT_COMPILE_COMMANDS

If you want [[nvim#LSP|nvim]] to recognize the compilation commands, the file has to be at the root of the current root directory. 

1) Enable the environment variable in CMakeLists.txt
```
set(CMAKE_EXPORT_COMPILE_COMMANDS TRUE)
```
2) The file gets output into the build directory. Create a symlink to the project root directory [[Linux#Create a symlink]]