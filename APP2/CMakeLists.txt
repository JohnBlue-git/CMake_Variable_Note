cmake_minimum_required(VERSION 3.10)
project(APP2)

message(STATUS "    [APP2 dir]:")


### Define variables

# non-cache variable
# this line will overite the non-cache variable
set(SELECT_APP "LOCAL APP2")
message(STATUS "    [Var] SELECT_APP: ${SELECT_APP}")

# cache variable
# the cache variable will be overshadowed
set(CACHE_SELECT_APP "LOCAL APP2" CACHE STRING "")
message(STATUS "    [Var] CACHE_SELECT_APP: ${CACHE_SELECT_APP}")
