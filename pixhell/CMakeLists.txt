cmake_minimum_required(VERSION 3.7)

project(Pixhell)

set(BASE_DIR "${CMAKE_SOURCE_DIR}/..")

set(SDL_INSTALL_DIR "${BASE_DIR}/install/sdl/")
set(SDL_INCLUDE_DIR "${SDL_INSTALL_DIR}/include/SDL2")
set(SDL_LIBRARY_DIR "${SDL_INSTALL_DIR}/lib/")
set(SDL_BINARY_DIR "${SDL_INSTALL_DIR}/bin/")

set(SDL2_LIBRARIES "${SDL_LIBRARY_DIR}/SDL2d.lib;${SDL_LIBRARY_DIR}/SDL2maind.lib")
string(STRIP "${SDL2_LIBRARIES}" SDL2_LIBRARIES)

include_directories(${SDL_INCLUDE_DIR})

message("Building Pixhell")

set(SOURCE_FILES
	"src/main.cpp"
)

set(BUILD_OUTPUT_DIRECTORY "${BASE_DIR}/artifact/")

add_executable(Pixhell ${SOURCE_FILES})
target_link_libraries(Pixhell ${SDL2_LIBRARIES})

install(FILES "${SDL_BINARY_DIR}/SDL2d.dll" DESTINATION ${BUILD_OUTPUT_DIRECTORY})
install(TARGETS Pixhell RUNTIME DESTINATION ${BUILD_OUTPUT_DIRECTORY})
 