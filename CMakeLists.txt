cmake_minimum_required(VERSION 3.23)

project(sdl2_tutorial)

add_compile_options(-w -Wall)

find_library(sdl2 SDL2 REQUIRED)
if (${sdl2} STREQUAL sdl2-NOTFOUND)
    message(FATAL ERROR "Shits broke")
else()
    message(STATUS "Found ${sdl2}")
endif()

find_library(sdl2_image SDL2_image REQUIRED)
if (${sdl2} STREQUAL sdl2_image-NOTFOUND)
    message(FATAL ERROR "Shits broke")
else()
    message(STATUS "Found ${sdl2_image}")
endif()

find_library(sdl2_ttf SDL2_ttf REQUIRED)
if (${sdl2} STREQUAL sdl2_ttf-NOTFOUND)
    message(FATAL ERROR "Shits broke")
else()
    message(STATUS "Found ${sdl2_ttf}")
endif()

find_library(sdl2_mixer SDL2_mixer REQUIRED)
if (${sdl2} STREQUAL sdl2_mixer-NOTFOUND)
    message(FATAL ERROR "Shits broke")
else()
    message(STATUS "Found ${sdl2_mixer}")
endif()

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17 -lSDL2")
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

file(GLOB srcs src/*.cpp)

add_executable(hello_sdl2 ${srcs})

target_link_libraries(hello_sdl2 PRIVATE SDL2 SDL2_image SDL2_ttf SDL2_mixer)

target_sources(
    hello_sdl2 PRIVATE
    ${srcs}
)