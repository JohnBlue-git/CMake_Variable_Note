# CMake_Variable_Note

To build the project, follow these steps:

Navigate to the root of your project directory:

cd /path/to/my_project Create a build directory and navigate into it:

mkdir build cd build Run CMake to configure the project:

cmake .. Build the project:


# CMake variable
- Pre-defined variable
- Normal variable
- Cache variable


# Common CMake pre-defined variable

CMAKE_BUILD_TYPE: Specifies the build configuration (e.g., Debug, Release).


*_SOURCE_DIR 和 *_BINARY_DIR

CMakeLists.txt and its corredponging source code

to build code and generate binary

會隨 project() 指令改變的變數, 如果我們的 project 會給其他 CMake 專案使用就會有影響, Day 9 會詳細介紹
PROJECT_SOURCE_DIR
PROJECT_BINARY_DIR

專屬於我們專案的變數, 只有 project(projectName) 會影響, 所以 projectName 最好不要撞名
<PROJECT-NAME>_SOURCE_DIR
<PROJECT-NAME>_BINARY_DIR


CMAKE_CURRENT_SOURCE_DIR: Path to the current source directory.
CMAKE_CURRENT_BINARY_DIR: Path to the current build directory.



每次 build code 前都先清掉舊的 cache variables
這是比較建議的做法, 在開發時透過 CLI 指令將之前 build directories 底下的東西都清掉, 就不會讓之前殘留的產出影響到這次 build code, 缺點是因為把 cache 清空了, 沒辦法加速, 用法如下
--fresh
cmake -S <source-dir> -B <build-dir> --fresh



- CMAKE_CXX_COMPILER: Path to the C++ compiler.

- CMAKE_C_COMPILER: Path to the C compiler.

- CMAKE_SYSTEM_NAME: Name of the operating system (e.g., Linux, Windows).
- CMAKE_SYSTEM_PROCESSOR: Processor architecture (e.g., x86_64).


- list feature
'''
# Define FILES list
# myVar = "file1;file2;file3"
set(FILES
    file1
    file2
    file3)
# Iterate over the FILES list
foreach(file ${FILES})
    message(STATUS "File: ${file}")
endforeach()
'''



# CMake variable property
- normal variable:
-- Type: The type of the variable, typically STRING, BOOL, or PATH. 
-- Scope: They have local scope within the directory and its subdirectories. They do not persist across CMake runs.
-- Non-persistency: These variables are temporary and do not affect future CMake configurations. They are reset each time CMake is runand will be overwritten by sud-directory's set().
'''
set(SELECT_APP "APP1")
'''

- cache variable
-- Type: The type of the variable, typically STRING, BOOL, or PATH. 
-- Scope: They have local scope within the directory and its subdirectories.
-- Persistency: These variables' value will be remember accross the project and affect future CMake configurations (if CMake cache exist). The values set by user defined or under the top-level directory would overshadow the valuse set under the sud-directories. 
'''
# Priority:
# user define > top-level > sub-level

# How to user define variable:
# cmake -D <name>:<type>=<value> <source directory>

set(CACHE_SELECT_APP "APP1" CACHE STRING "")
'''

