cmake_minimum_required(VERSION 3.7)
project(GameCppProject)

set(CMAKE_CXX_STANDARD 11)
set(gcc_custom_flags "-c -ansi -pedantic -std=c++0x -Weffc++ -g")

FIND_LIBRARY(libraries NAMES  lEngine lGL lglut lm lGLU PATHS include libLinux)

IF(libraries)
    ADD_LIBRARY(lEngine lGL lglut lm libraries)
ENDIF(libraries)

set(SOURCE_FILES
        src/Asteroid.cpp
        src/Asteroid.h
        src/BLine.cpp
        src/BLine.h
        src/Config.h
        src/Game.cpp
        src/Game.h
        src/main.cpp
        src/MyControlEngine.cpp
        src/MyControlEngine.h
        src/MyGameEngine.cpp
        src/MyGameEngine.h
        src/MyGraphicEngine.cpp
        src/MyGraphicEngine.h
        src/Observer.cpp
        src/Observer.h
        src/Shot.cpp
        src/Shot.h
        src/Spaceship.cpp
        src/Spaceship.h
        src/utils.cpp
        src/utils.h
        src/Wave.cpp
        src/Wave.h)

set(HEADER_FILES  include/ControlEngine.h
        include/Engine.h
        include/GameEngine.h
        include/GraphicEngine.h
        include/GraphicPrimitives.h
        include/libGraphicInclude.h
        include/Stopwatch.h)


include_directories(${CMAKE_SOURCE_DIR}/include)      # -I flags for compiler
link_directories(${CMAKE_SOURCE_DIR}/libLinux)        # -L flags for linker

add_executable(GameCppProject ${SOURCE_FILES} ${HEADER_FILES})  # define executable target prog, specify sources
target_link_libraries(GameCppProject Engine GL glut m GLU)      # -l flags for linking prog target

set_target_properties(GameCppProject PROPERTIES COMPILE_FLAGS ${gcc_custom_flags})
