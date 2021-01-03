cmake_minimum_required(VERSION 3.11.4)

# Define the project
project(cpp LANGUAGES CXX)

# Find dependencies
find_package(Doxygen)

if (${DOXYGEN_FOUND})
    set(DOXYGEN_EXTRACT_ALL YES)
    set(DOXYGEN_GENERATE_TREEVIEW YES)
    set(DOXYGEN_USE_MDFILE_AS_MAINPAGE ${PROJECT_SOURCE_DIR}/README.md)

    # Get the list of subprojects
    file(GLOB SUBPROJECTS cmake-* cpp-*)

    # Add target to generate doxygen documentation
    doxygen_add_docs(__generate_documentation
        ${PROJECT_SOURCE_DIR}/README.md
        ${SUBPROJECTS}
        COMMENT "Generating documentation..."
    )
endif()

add_subdirectory(cmake-modules)
add_subdirectory(cpp-audio)
add_subdirectory(cpp-benchmark)
add_subdirectory(cpp-dsp)
add_subdirectory(cpp-math)
add_subdirectory(cpp-music)