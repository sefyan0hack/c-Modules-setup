cmake_minimum_required(VERSION 3.30)
project(CXXModlules)
set(CMAKE_CXX_STANDARD 20)

if(NOT CMAKE_GENERATOR STREQUAL "Ninja")
    message(FATAL_ERROR "This project requires the Ninja generator. Please run CMake with -G Ninja.")
endif()

# Disable Modules if Not Used

set(CMAKE_EXPERIMENTAL_CXX_MODULE_CMAKE_API OFF)

# Use Ninja with Module Scanning Enabled
set(CMAKE_CXX_SCAN_FOR_MODULES TRUE)

add_executable(result)
target_sources(result PUBLIC
        ${PROJECT_SOURCE_DIR}/src/main.cpp
    PUBLIC
    FILE_SET CXX_MODULES
    BASE_DIRS ${PROJECT_SOURCE_DIR}/mod
    FILES
        ${PROJECT_SOURCE_DIR}/mod/vec2.cpp

)