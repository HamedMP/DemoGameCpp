cmake_minimum_required(VERSION 3.7)
project(GameCppProject)

set(CMAKE_CXX_STANDARD 11)

FIND_LIBRARY(libraries NAMES  lEngine lGL lglut lm lGLU PATHS include libLinux)

IF(libraries)
    ADD_LIBRARY(lEngine lGL lglut lm libraries)
ENDIF(libraries)

############################################
## For searching the *.h and *.cpp files ###
############################################
file(GLOB_RECURSE SOURCE_FILES "src/*.cpp")
file(GLOB_RECURSE HEADER_FILES "src/*.h")

set (Foo_INCLUDE_DIRS ${CMAKE_SOURCE_DIR})
foreach (_headerFile ${HEADER_FILES})
    get_filename_component(_dir ${_headerFile} PATH)
    list (APPEND Foo_INCLUDE_DIRS ${_dir})
endforeach()
list(REMOVE_DUPLICATES Foo_INCLUDE_DIRS)

include_directories(${Foo_INCLUDE_DIRS})


include_directories(${CMAKE_SOURCE_DIR}/include)      # -I flags for compiler
link_directories(${CMAKE_SOURCE_DIR}/libLinux)        # -L flags for linker

add_executable(GameCppProject ${SOURCE_FILES} ${HEADER_FILES})  # define executable target prog, specify sources
target_link_libraries(GameCppProject Engine GL glut m GLU)      # -l flags for linking prog target

## Added the modifier flags in the compiler
set(gcc_custom_flags "-c -ansi -pedantic -std=c++0x -Weffc++ -g")
set_target_properties(GameCppProject PROPERTIES COMPILE_FLAGS ${gcc_custom_flags})
