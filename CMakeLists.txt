#/CMakeLists.txt
# This is the main CMake file that will add all the ones in the directories below this one

# For this example, the main project will be named `Example`, the test project will 
# be called "Example_test" and the library that both of the previous projects use will be 
# linked to will be called "Example_lib"

# A flowchart of the project would look something like this
#           #############
#           #Example_lib#
#           #############
#            |         |
#            V         V
#     ##############  #########
#     #Example_test#  #Example#
#     ##############  #########

# Example will contain the main function, anything written there will not be tested, so
# keep main simple and put other functions in Example_lib and call them from main.
# Example_lib should contain almost all of your code.
# Example_test will contain the tests that you will create with gtest's macros.
# All three of the projects #include the same source files found in /src

# After runing CMake on this file, you should both  be able to execute Example, and run tests.

cmake_minimum_required(VERSION 3.11)

# set the project name
project(Example CXX)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

#Download and cache googletest from Google's GitHub repo using FetchContent
#This fetch section (mostly) comes from this googletest tutorial: https://google.github.io/googletest/quickstart-cmake.html
include(FetchContent)
FetchContent_Declare(
	googletest
	URL https://github.com/google/googletest/archive/refs/tags/release-1.11.0.zip
)
# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
#This compiles the newly downloaded project, then it will be linked when needed
FetchContent_MakeAvailable(googletest)

#setup testing
enable_testing()

# Add all the directories that have source files
add_subdirectory(src)
add_subdirectory(test)
