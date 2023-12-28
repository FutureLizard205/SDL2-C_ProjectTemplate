cmake_minimum_required(VERSION 3.26)
project(ProjectName C)

set(CMAKE_C_STANDARD 11)


add_executable(${PROJECT_NAME}
        src/main.c
        src/globalConstants.h)


INCLUDE(FindPkgConfig)

if(UNIX)
    pkg_search_module(SDL2 REQUIRED sdl2)
    pkg_search_module(SDL2IMAGE REQUIRED SDL2_image>=2.0.0)

    include_directories(${SDL2_INCLUDE_DIRS} ${SDL2IMAGE_INCLUDE_DIRS})
    target_link_libraries(${PROJECT_NAME} ${SDL2_LIBRARIES} ${SDL2IMAGE_LIBRARIES})
else ()
    include_directories(libraries/SDL2-devel-2.28.5-mingw/include libraries/SDL2_image-devel-2.8.1-mingw/include)
    target_link_libraries(${PROJECT_NAME} libraries/SDL2-devel-2.28.5-mingw/lib libraries/SDL2_image-devel-2.8.1-mingw/lib)

endif ()