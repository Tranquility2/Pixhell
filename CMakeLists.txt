cmake_minimum_required(VERSION 3.7)

project(pixhell_build)

include(ExternalProject)
INCLUDE(FindPackageHandleStandardArgs)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_EXPORT_COMPILE_COMMANDS "ON")

# use FindSDL2.cmake
set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake")

###-------------------------------------------------###

ExternalProject_Add(sdl
  GIT_REPOSITORY "https://github.com/SDL-mirror/SDL"
  GIT_TAG "master"

  SOURCE_DIR "${CMAKE_SOURCE_DIR}/dep/sdl"
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_SOURCE_DIR}/install/sdl/ -DCMAKE_DEBUG_POSTFIX=_d 
)

#ExternalProject_Add(sdl_image
#  DEPENDS sdl
#
#  GIT_REPOSITORY "https://github.com/SDL-mirror/SDL_image"
#  GIT_TAG "master"
#
#  SOURCE_DIR "${CMAKE_SOURCE_DIR}/dep/sdl_image"
#  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_SOURCE_DIR}/install/sdl_image/ -DCMAKE_DEBUG_POSTFIX=_d -DCMAKE_MODULE_PATH=${PROJECT_SOURCE_DIR}/cmake
#)

#ExternalProject_Add(sdl_ttf
#  DEPENDS sdl
#
#  GIT_REPOSITORY "https://github.com/SDL-mirror/SDL_ttf"
#  GIT_TAG "master"
#
#  SOURCE_DIR "${CMAKE_SOURCE_DIR}/dep/sdl_ttf"
#  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_SOURCE_DIR}/install/sdl_ttf/ -DCMAKE_DEBUG_POSTFIX=_d -DCMAKE_MODULE_PATH=${PROJECT_SOURCE_DIR}/cmake
#)

###-------------------------------------------------###

ExternalProject_Add(pixhell 
  DEPENDS sdl

  SOURCE_DIR "${CMAKE_SOURCE_DIR}/pixhell/"
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_SOURCE_DIR}/artifact/ -DCMAKE_DEBUG_POSTFIX=_d -DCMAKE_MODULE_PATH=${PROJECT_SOURCE_DIR}/cmake
)
