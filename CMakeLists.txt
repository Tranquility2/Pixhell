cmake_minimum_required(VERSION 3.7)

project(pixhell_build)

include(ExternalProject)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_EXPORT_COMPILE_COMMANDS "ON")

###-------------------------------------------------###

ExternalProject_Add(sdl
  GIT_REPOSITORY "https://github.com/spurious/SDL-mirror"
  GIT_TAG "master"

  SOURCE_DIR "${CMAKE_SOURCE_DIR}/dep/sdl"
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_SOURCE_DIR}/install/sdl/ -DCMAKE_DEBUG_POSTFIX=_d
)

set(SDL_INSTALL_DIR "${CMAKE_SOURCE_DIR}/install/sdl/")
set(SDL_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/install/sdl/include/")
set(SDL_LIBRARY_DIR "${CMAKE_SOURCE_DIR}/install/sdl/lib/")
set(SDL_BINARY_DIR "${CMAKE_SOURCE_DIR}/install/sdl/bin/")

###-------------------------------------------------###

ExternalProject_Add(pixhell
  SOURCE_DIR "${CMAKE_SOURCE_DIR}/pixhell/"
)

###-------------------------------------------------###

add_dependencies(pixhell sdl)
