
<details>
<summary>Click to expand code</summary>

```console
def hello_world():
    print("Hello, world!")

function helloWorld() {
    console.log("Hello, world!");
}
```
</details>

# CMake_Variable
To build the project, follow these steps:

Navigate to the root of the project

mkdir build && cd build

cmake ..

or attach with user defined cache variable

cmake -D <_name_>:<_type_>=<_value_> ..

## CMake variable
- Pre-defined variable
- Normal variable
- Cache variable


## Common CMake pre-defined variable
- CMAKE_BUILD_TYPE: \
Specifies the build configuration (e.g., Debug, Release).
- *_SOURCE_DIR 和 *_BINARY_DIR: \
Source directory means the root of the project and it is where CMakeLists.txt located; Binary directory is where we want the project to build code and generate binaries.
    * PROJECT_SOURCE_DIR & PROJECT_BINARY_DIR: \
    It will change as respect to current project()
    * CMAKE_CURRENT_SOURCE_DIR & CMAKE_CURRENT_BINARY_DIR: \
    Path to the current source or build directory.
```console
# We can use -S to set source directory
#        use -B to set binary directory
# (New in cmake version 3.24) To clear binary derectory (or cmake cache) before re-build, we can uuse --fresh
cmake -S <source-dir> -B <binary-dir> --fresh

# ref:
# https://cmake.org/cmake/help/latest/manual/cmake.1.html
```
- CMAKE_CXX_COMPILER: \
Path to the C++ compiler.
- CMAKE_C_COMPILER: \
Path to the C compiler.
- CMAKE_SYSTEM_NAME: \
Name of the operating system (e.g., Linux, Windows).
- CMAKE_SYSTEM_PROCESSOR: \
Processor architecture (e.g., x86_64).

## CMake variable property
- Normal variable:
    * Type: \
    The type of the variable, typically STRING, BOOL, or PATH. 
    * Scope: \
    They have local scope within the directory and its subdirectories. They do not persist across CMake runs.
    * Non-persistency: \
    These variables are temporary and do not affect future CMake configurations. They are reset each time CMake is runand will be overwritten by sud-directory's set().
```cmake
set(SELECT_APP "APP1")
```
- Cache variable:
    * Type: \
    The type of the variable, typically STRING, BOOL, or PATH. 
    * Scope: \
    They have local scope within the directory and its subdirectories.
    * Persistency: \
    These variables' value will be remember accross the project and affect future CMake configurations (if CMake cache exist). The values set by user defined or under the top-level directory would overshadow the valuse set under the sud-directories. 
```cmake
# How to set cache variable via user input
# cmake -D <name>:<type>=<value>

# How to set cache variable within CMakeLists.txt
set(CACHE_SELECT_APP "APP1" CACHE STRING "")

# Priority:
# user input > top-level set() > sub-level set()
```
