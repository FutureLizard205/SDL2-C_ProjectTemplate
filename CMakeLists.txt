cmake_minimum_required(VERSION 3.26)
project(ProjectName C)

set(CMAKE_C_STANDARD 11)


add_executable(${PROJECT_NAME}
        src/main.c
        src/globalConstants.h)


#INCLUDE(FindPkgConfig)

#if(UNIX)
    #pkg_search_module(SDL2 REQUIRED sdl2)
    #pkg_search_module(SDL2IMAGE REQUIRED SDL2_image>=2.0.0)
    
#else ()
	list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake/sdl2)
	set(SDL2_PATH "C:\\Users/Miguel/Downloads/SDL2-C_ProjectTemplate-main/libraries/SDL2-2.28.5/x86_64-w64-mingw32")
	set(SDL2_IMAGE_PATH "C:\\Users/Miguel/Downloads/SDL2-C_ProjectTemplate-main/libraries/SDL2_image-2.8.2/x86_64-w64-mingw32")
	find_package(SDL2 REQUIRED)
	find_package(SDL2_image REQUIRED)
#endif ()

include_directories(${SDL2_INCLUDE_DIRS} ${SDL2_IMAGE_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} SDL2::Main SDL2::Image)