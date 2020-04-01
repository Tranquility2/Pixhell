cmake_minimum_required(VERSION 3.7)

project(pixhell)

find_package(SDL2 REQUIRED)

include_directories(${SDL2_INCLUDE_DIR})

message("Building pixhell")

message("${SDL2_LIBRARY}")
message("${SDL2_INCLUDE_DIR}")

set(SOURCE_FILES
	"src/main.cpp"
)

add_executable(pixhell ${SOURCE_FILES})
target_link_libraries(pixhell ${SDL2_LIBRARY})

# DLL is needed in case of dynamic libs
IF (WIN32)
	message("${SDL2_BINARY}")
	set(SDL2_DLL ${SDL2_BINARY}/SDL2d.dll)
	install(FILES ${SDL2_DLL} DESTINATION ${CMAKE_INSTALL_PREFIX})
ENDIF()

install(TARGETS pixhell RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX})
 