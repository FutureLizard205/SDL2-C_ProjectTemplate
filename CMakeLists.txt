cmake_minimum_required(VERSION 3.26)
project(ProjectName C)

set(CMAKE_C_STANDARD 11)


add_executable(${PROJECT_NAME}
        src/main.c
        src/globalConstants.h)


INCLUDE(FindPkgConfig)

pkg_search_module(SDL2 REQUIRED sdl2)
pkg_search_module(SDL2IMAGE REQUIRED SDL2_image>=2.0.0)

include_directories(${SDL2_INCLUDE_DIRS} ${SDL2IMAGE_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} ${SDL2_LIBRARIES} ${SDL2IMAGE_LIBRARIES})