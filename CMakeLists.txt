cmake_minimum_required(VERSION 3.11.4)

# Define the project
project(cpp LANGUAGES CXX)

add_subdirectory(cmake-modules)

# Add subprojects
file(GLOB subprojects cpp-*)
foreach(subproject ${subprojects})
    add_subdirectory(${subproject})
endforeach(subproject)