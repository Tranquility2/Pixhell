cmake_minimum_required(VERSION 3.7)

project(Pixhell)

add_subdirectory(SDL-mirror)

find_package(SDL2 REQUIRED)

include_directories(
    "src/"
    ${SDL2_INCLUDE_DIRS}
)

set(SOURCE_FILES
	"src/main.cpp"
)

add_executable(Pixhell ${SOURCE_FILES})

target_link_libraries(Pixhell 
    ${SDL2_LIBRARIES}
)

