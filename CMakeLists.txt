cmake_minimum_required(VERSION 3.11.4)

# Define the project
project(cpp LANGUAGES CXX)

# Get the list of subprojects
file(GLOB subprojects cpp-*)

find_package(Doxygen)
if (${DOXYGEN_FOUND})
    set(DOXYGEN_EXTRACT_ALL YES)
    set(DOXYGEN_GENERATE_TREEVIEW YES)
    set(DOXYGEN_USE_MDFILE_AS_MAINPAGE ${PROJECT_SOURCE_DIR}/README.md)

    # Add target to generate doxygen documentation
    doxygen_add_docs(__generate_documentation
        ${PROJECT_SOURCE_DIR}/README.md
        ${subprojects}
        COMMENT "Generating documentation..."
    )
endif()

add_subdirectory(cmake-modules)

foreach(subproject ${subprojects})
    add_subdirectory(${subproject})
endforeach(subproject)