cmake_minimum_required(VERSION 3.9)
project(guitest_sdl CXX)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_BINARY_DIR})
list(APPEND CMAKE_PREFIX_PATH ${CMAKE_BINARY_DIR})

find_package(OpenGL REQUIRED)

if(EXISTS "${CMAKE_SOURCE_DIR}/conanbuildinfo.cmake")
	include(conanbuildinfo.cmake)
	conan_basic_setup(TARGETS)
else()
	message(FATAL_ERROR "you didn't install conan. Use 'conan install conan/ in the root dir.")
endif()

file(GLOB guitest_sdl_imgui_src "${CMAKE_SOURCE_DIR}/imgui/*")

add_library(guitest_sdl_imgui ${guitest_sdl_imgui_src})
target_include_directories(guitest_sdl_imgui PUBLIC "${CMAKE_SOURCE_DIR}/imgui" ${OPENGL_INCLUDE_DIR})
target_link_libraries(guitest_sdl_imgui PUBLIC CONAN_PKG::sdl ${OPENGL_LIBRARIES})



add_executable(guitest_sdl main.cpp)
target_link_libraries(guitest_sdl guitest_sdl_imgui)
