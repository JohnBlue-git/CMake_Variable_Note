cmake_minimum_required(VERSION 3.10)
project(Variable)

message(STATUS "[Top dir]:")


### Define variables

# non-cache variable
set(SELECT_APP "APP1")
message(STATUS "[Var] SELECT_APP: ${SELECT_APP}")

# cache variable
set(CACHE_SELECT_APP "APP1" CACHE STRING "")
message(STATUS "[Var] CACHE_SELECT_APP: ${CACHE_SELECT_APP}")


### Conditional statement
if(CACHE_SELECT_APP STREQUAL "APP1")
    message(STATUS "[Sub-dir] APP1:")
    add_subdirectory(APP1)
elseif(CACHE_SELECT_APP STREQUAL "APP2")
    message(STATUS "[Sub-dir] APP2:")
    add_subdirectory(APP2)
else()
    message(STATUS "[Sub-dir] Error: ${CACHE_SELECT_APP} does not exist")
endif()
