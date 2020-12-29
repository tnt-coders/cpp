cmake_minimum_required(VERSION 3.11.4)

# Define the project
project(cpp LANGUAGES CXX)

# Get CMake modules from Git
include(FetchContent)
FetchContent_Declare(cmake-modules
  GIT_REPOSITORY https://github.com/tnt-coders/cmake-modules.git
  GIT_TAG main
)
FetchContent_MakeAvailable(cmake-modules)

add_subdirectory(cpp-audio)
add_subdirectory(cpp-benchmark)
add_subdirectory(cpp-dsp)
add_subdirectory(cpp-math)
add_subdirectory(cpp-music)