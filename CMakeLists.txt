cmake_minimum_required(VERSION 3.9)
project(guitest_sdl CXX)

# TODO wrap around emscripten variable
set(CMAKE_EXECUTABLE_SUFFIX ".html")

list(APPEND CMAKE_MODULE_PATH ${CMAKE_BINARY_DIR})
list(APPEND CMAKE_PREFIX_PATH ${CMAKE_BINARY_DIR})

find_package(OpenGL REQUIRED)

include(FetchContent)
FetchContent_Declare(
  sdl3_source
  GIT_REPOSITORY https://github.com/libsdl-org/SDL.git
  GIT_TAG        main
)
FetchContent_MakeAvailable(sdl3_source)


file(GLOB guitest_sdl_imgui_src "${CMAKE_SOURCE_DIR}/imgui/*")

add_library(guitest_sdl_imgui ${guitest_sdl_imgui_src})
target_include_directories(guitest_sdl_imgui PUBLIC "${CMAKE_SOURCE_DIR}/imgui" ${OPENGL_INCLUDE_DIR})
target_link_libraries(guitest_sdl_imgui PUBLIC SDL3::SDL3 ${OPENGL_LIBRARIES})



add_executable(guitest_sdl main.cpp)
target_link_libraries(guitest_sdl guitest_sdl_imgui)
